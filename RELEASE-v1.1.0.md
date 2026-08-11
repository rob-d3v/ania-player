# Ania Player v1.1.0

**Windows · Linux (x86_64 e ARM64)**

Esta é a release que a v1.0.0 prometeu.

Sendo direto sobre isso: as notas da v1.0.0 anunciaram TTS, STT, palavra de ativação e um
"pipeline de IA" que **não existiam no player**. Existiam no aplicativo Java de criação, ou
como algo que você montava por fora com n8n. Também falavam em 194 idiomas, e o player não
tinha tradução nenhuma.

Agora tudo isso existe como software funcionando. É por isso que este texto é longo — a
release anterior deixou muita coisa sem explicar, e várias delas ninguém descobre sozinho.

---

## As cinco coisas que você provavelmente não sabe que ele faz

### 1. Seu avatar virou uma webcam

Instale uma vez e **"Ania Virtual Camera"** aparece na lista de câmeras do OBS, Zoom, Meet,
Discord e qualquer coisa que aceite webcam. Por trás dela há um compositor de cenas em
camadas — captura de tela, imagens e o avatar juntos, com editor de arrastar e
redimensionar e seletor de região estilo ferramenta de captura.

No Windows a instalação é **um clique**: os drivers DirectShow (UnityCapture, MIT) já vêm
embutidos e o player os registra sozinho. No Linux exige `v4l2loopback`, e o app te mostra
o comando exato. **macOS não tem câmera virtual** — não é limitação temporária, falta a
base de sistema.

### 2. Ele sincroniza com a voz do ChatGPT sem você configurar áudio nenhum

O **modo companion** coloca o avatar num canto da tela — pequeno, transparente, sem moldura,
sempre no topo, clicável através — e a **resolução automática de loopback** encontra sozinha
o dispositivo que captura o que os alto-falantes estão tocando.

Sem Stereo Mix, sem VB-Cable, sem lista de dispositivos, **sem diálogo nenhum**. WASAPI no
Windows, o `.monitor` do sink padrão no Linux.

Duas coisas que ele faz por honestidade e que valem dizer: ele **verifica por 2 segundos**
antes de afirmar que funcionou, e **nunca diz que está capturando o sistema quando caiu no
microfone**. Silêncio não é tratado como falha — o ChatGPT ainda não ter falado é
indistinguível do dispositivo errado em 2 segundos.

> Ele não detecta nem se acopla ao ChatGPT. É uma postura de janela + áudio: sincroniza com
> o áudio do sistema, seja ChatGPT, YouTube ou qualquer outra coisa.

**Escape obrigatório:** `Ctrl+Shift+A` devolve o controle da janela. E se o atalho não
conseguir se registrar, o clique-através **não é aplicado** — janela agarrável é melhor que
janela irremovível.

### 3. O assistente de IA é real agora, e o n8n virou opcional

Palavra de ativação → transcrição → LLM → fala, tudo dentro do app, com **12 motores
trocáveis**:

- **TTS (5):** Piper local (voz pt-BR de 63 MB), Edge neural da Microsoft (grátis, sem
  chave), ElevenLabs, Google Cloud, OpenAI — este com Base-URL configurável, então funciona
  com Azure ou OpenRouter.
- **STT (5):** faster-whisper local (padrão), Google, Windows offline, ElevenLabs, Whisper
  da OpenAI.
- **Wake word (2):** openWakeWord e **Sentinela**.

Sai da caixa apontando pro **Ollama local** — offline de verdade, sem chave de API, sem
nuvem. Janela de chat flutuante com **transcrição parcial ao vivo** e galeria de imagens.

O lip sync do assistente é dirigido pela **forma de onda do próprio TTS**, não pelo barulho
do ambiente.

### 4. A Ania tem motor de palavra de ativação próprio

**Sentinela** é da casa: treinado com vozes sintéticas, ajustado para pt-BR, um único ONNX
pequeno sem torch, inferência 100% offline, limiar auto-calibrado. Os modelos baixam
sozinhos com **verificação sha256 — e recusa se não bater**.

É também o **único** wake word que se provisiona sozinho (veja as limitações).

### 5. O player é scriptável e controlável remotamente

- **CLI com 34 verbos:** `aniaplayer tts "olá"`, `action`, `status --json`. Socket Unix
  0600 no Linux, TCP loopback com token no Windows.
- **Links `ania://`** que uma página web pode disparar.
- **Ania Link:** controle remoto opt-in por código de 6 caracteres, para um plugin do
  ChatGPT dirigir seu avatar.

---

## Tudo que é novo, por área

### Sistema de plugins — não existia

Gerenciador completo com busca, filtros e cartões agrupados por Apps / TTS / STT / Wake
Word. Antes de instalar, cada componente mostra **tamanho, repositório e licença**. Cada um
carrega uma pílula **☁ Nuvem / 🏠 Local** dizendo se seus dados saem da máquina.

**17 plugins** no registro.

### Modo companion e `ania://`

Três verbos, e só três:

| Link | O que faz |
|---|---|
| `ania://companion?avatar=&lt;id&gt;` | abre em modo companion |
| `ania://open?listing=&lt;uuid&gt;` | instala do marketplace e abre |
| `ania://link?code=&lt;ABC234&gt;` | entra numa sala do Ania Link |

Registrado em `HKCU` no Windows — **sem pedir administrador**. No Linux via
`x-scheme-handler/ania`.

Validação dura: limite de 2048 bytes, rejeita caracteres de controle, sem userinfo, porta
ou caminho, e URL malformada é **rejeitada sem efeito colateral nenhum**. Um segundo clique
reaproveita a janela aberta.

### Marketplace dentro do player

Vitrine em PyQt5: busca com debounce, chips de categoria, filtro grátis/pago, ordenação,
carregamento infinito, miniaturas WebP animadas, instalação com progresso. Miniaturas
ficam em cache com ETag e **continuam aparecendo offline**.

**Sem login, sem conta, sem token.**

### Biblioteca local à prova de queda

Índice com fsync e substituição atômica, e **o arquivo é gravado antes da entrada no
índice** — matar o player no meio de um download deixa no máximo um arquivo órfão, nunca
uma entrada quebrada. Varredura de `.part` e órfãos no boot. Índice corrompido é
preservado, não fatal. Verificação SHA-256 contra o manifesto.

Limite de 10 avatares / 500 MB com remoção LRU **confirmada por você**, nunca silenciosa.

### Ania Link — desligado por padrão

Com ele desligado, o módulo cliente **nem é importado**. Nada resolve DNS, nada conecta.

Cliente WebSocket RFC 6455 escrito à mão, **sem dependência nova**. **16 verbos
permitidos**, lista de negados explícita, limite de 10 mensagens/s, TTS recusado com a
janela escondida. `set_avatar` recebe **id de listagem**, resolvido contra a biblioteca
local — **nenhum caminho de arquivo trafega pela rede**. Código de pareamento sem
caracteres confundíveis, expira em 10 minutos, primeira reivindicação vence.

**Áudio nunca é enviado.** Frames binários são recusados.

### Integrações

- **MQTT** bidirecional: o LLM publica, e assinaturas alimentam `{variáveis}`.
- **MySQL** — **somente leitura por padrão**, validado por prefixo (SELECT/SHOW/DESCRIBE/
  EXPLAIN) com remoção de comentários para bloquear desvio por `/*…*/`.
- **Variáveis globais** com `{templating}` ao vivo em fala e prompts.

### Raspberry Pi e máquinas fracas

A v1.0.0 já dizia suportar Pi. **Estes são os componentes que fazem isso valer:** redutor
de frames, redutor de qualidade (metade/quarto de resolução com cache WebP em disco, 75-94%
menos RAM) e adaptador de tela para LCDs pequenos.

### Por baixo do capô

Uma autoridade única para caminhos de configuração, dados e cache — o código antigo estava
copiado em mais de 12 arquivos e deixava **~2,7 GB de modelos dentro da pasta de
configuração**. Também corrige `%APPDATA%` vazio gravando config no diretório atual.
`aniaplayer tidy` migra instalações antigas, com `--dry-run`.

### Idiomas

**192 locales**, agora de verdade, no player. Verificado que são traduções reais, não cópias
do inglês.

---

## Limitações — leia antes de instalar

Prefiro que você saiba disso agora do que descubra depois.

### Por plataforma

| | Windows | Linux | macOS |
|---|---|---|---|
| Câmera virtual | ✅ um clique | ⚠️ exige `sudo modprobe v4l2loopback` | ❌ não existe |
| Captura de tela | ✅ | ⚠️ **Wayland é recusado** | ❌ |
| STT offline do sistema | ✅ | — | — |
| Serviço systemd (8 verbos) | — | ✅ | — |

### Coisas que não estão prontas

- **A palavra de ativação padrão não baixa sozinha numa instalação nova.** O instalador
  escreve um README e reporta sucesso mesmo assim. **Use o Sentinela** — é o único que se
  provisiona sozinho.
- **`ania://open` provavelmente precisa de dois cliques na primeira vez.** A instalação roda
  em segundo plano e o "abrir" seguinte reporta "não está na biblioteca".
- **`ania://link?code=…` ativa o controle remoto sem confirmação dentro do app.** O desenho
  assume que o aviso do navegador é o consentimento. A lista de verbos permitidos limita o
  estrago, mas se você clicar num link `ania://link` de origem desconhecida, alguém pode
  comandar seu avatar até o código expirar.
- **O marketplace não abre no Windows** se o PyQt5 não estiver presente — a dependência
  ainda está marcada como exclusiva de Linux.
- **Dá para instalar um avatar que não abre:** `.aniapack` baixa, mas só `.ania` toca.
- **Chaves de API ficam em JSON puro**, sem criptografia.
- **190 dos 192 idiomas estão uma release atrás.** A interface do Ania Link só existe em
  inglês e português; o modo companion **não tem tradução nenhuma**, é inglês fixo em todos.
- **19 idiomas RTL não têm layout da direita para a esquerda.**
- O botão "🔄 Atualizar" da aba de áudio não faz nada.

### Não anunciado de propósito

O renderizador de pixel art existe no código mas **nunca é instanciado** — é código morto,
sem painel de configuração. Camadas de tipo `animated`, `video`, `webcam` e `text` no estúdio
virtual são **espaços reservados** e desenham um retângulo magenta de "não suportado".

### Cobertura de testes

Os testes automatizados cobrem áudio, voz, wake word e inicialização. **Não há testes** para
Ania Link, marketplace, biblioteca, esquema `ania://` ou modo companion. São recursos novos
exercitados à mão.

---

## Instalação

**Windows:** baixe `AniaPlayerSetup.exe` e execute. O `ania://` é registrado em `HKCU` — sem
prompt de administrador. O único UAC que aparece é o da câmera virtual, e só se você clicar
para instalá-la.

**Linux x86_64:** `AniaPlayerSetup.deb` · **Linux ARM64:** `aniaplayer_1.1_arm64.deb`

```bash
sudo dpkg -i AniaPlayerSetup.deb || sudo apt -f install
```

Para a câmera virtual no Linux:

```bash
sudo apt install -y v4l2loopback-dkms && \
sudo modprobe v4l2loopback devices=1 video_nr=10 \
  card_label="Ania Virtual Camera" exclusive_caps=1
```

`exclusive_caps=1` não é opcional — sem ele o Chrome e o Discord recusam o dispositivo.

---

## Privacidade

- **O áudio do seu computador nunca é gravado nem transmitido.** A análise de lip sync roda
  inteiramente na sua máquina.
- Sem conta, sem login, sem coleta de dados pessoais.
- O controle remoto é **opt-in** e, desligado, não abre conexão nenhuma.
- Motores locais (Piper, faster-whisper, Sentinela, Ollama) rodam offline. Os de nuvem estão
  marcados com ☁ na interface, antes de você instalar.

---

*Compilado com Nuitka — código Python compilado para nativo.*
