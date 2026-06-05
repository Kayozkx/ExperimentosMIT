# ExperimentosMIT
Repositório com projetos desenvolvidos no MIT App Inventor para Android. Todos os apps foram criados por mim, do zero, sem uso de IA — com o objetivo de treinar lógica de programação visual com blocos.

# 📱 MIT App Inventor — Experimentos

Repositório com projetos desenvolvidos no **MIT App Inventor** para Android. Todos os apps foram criados por mim, do zero, sem uso de IA — com o objetivo de treinar lógica de programação visual com blocos.

> Projeto pessoal desenvolvido para fins de aprendizado e testes.

---

## 📂 Estrutura do Repositório

```
ExperimentosMIT/
│
├── MateMosquito/
│   ├── Blocks_Moskito.png
│   ├── Mate_o_Mosquito.aia
│   └──  Tela_Moskito.png
│ 
├── MovendoObjetos/
│   ├── Blocks_FogueteBtn.png
│   ├── Movendo_Objetos.aia
│   └── Tela_MovendoObj.png
│
├── MovendoObjetos2/
│   ├── Blocks_FogueteAccel.png
│   ├── Movendo_Objetos2.aia
│   └── Tela_Accel.png
│
├── Paint/
│   ├── Blocks_Paint.png
│   ├── Paint.aia
│   └── Tela_Paint.png
│
├── PlayerTauz/
│   ├── Blocks_MenuTauz.png
│   ├── Blocks_PlayerTauz.png
│   ├── Player_Tauz.aia
│   ├── Tela_MenuTauz.png
│   └── Tela2_PlayerTauz.png
│
├── QuizMatematica/
│   ├── Blocks_QuizMat.png
│   ├── Quiz_Matematica.aia
│   └── Tela_QuizMat.png
│
├── LICENSE
│
└── README.md
```

---

## 🎵 01 — Player Tauz

**Meu primeiro projeto.** Um player de música completo com tema visual inspirado em músicas do estilo House, chamado VibeHouse.

### Telas

#### Tela 1 — Entrada

Tela inicial com fundo temático e botão para entrar no player.

![Tela Menu](PlayerTauz/Tela_MenuTauz.png)

#### Blocos — Tela 1

Bloco simples: o botão **ENTRE** abre a Screen2 (player).

![Blocos Menu](PlayerTauz/Blocks_MenuTauz.png)

---

#### Tela 2 — Player

Tela principal com controles de reprodução, slider de progresso, botões de próxima e anterior, e exibição da capa da música atual.

![Tela Player](PlayerTauz/Tela2_PlayerTauz.png)

#### Blocos — Tela 2

Os blocos controlam toda a lógica do player:

- **Listas globais:** músicas (arquivos `.mp3`), nomes das faixas, imagens das capas e durações armazenados em listas
- **chamar_musica:** função central que carrega a faixa atual — define o arquivo do tocador, atualiza o label com o nome, troca a imagem da capa e reseta o slider
- **PlayPause:** verifica se já há uma música carregada; se sim, alterna entre pausar e continuar; caso contrário, chama `chamar_musica` para iniciar
- **Próximo / Anterior:** incrementa ou decrementa o índice global e chama `chamar_musica`, com verificação de limites da lista
- **Clock (Timer):** a cada tick atualiza a posição do slider (`ThumbPosition`) com o tempo atual da faixa; quando a música termina, para automaticamente
- **Slider:** quando o usuário arrasta, reposiciona a música no ponto selecionado
- **Voltar:** para o tocador e o som ambiente, e retorna para a Screen1

![Blocos Player](PlayerTauz/Blocks_PlayerTauz.png)

---

### 🛠️ Arquivo do Projeto

```
PlayerTauz/Player_Tauz.aia
```

> Projeto criado dia 30 de março de 2026

---

## 🎨 02 — Paint

App de desenho com canvas livre, paleta de cores e controle de espessura do pincel.

### Tela

Canvas em branco para desenho livre. Abaixo: slider de espessura e botões de cor (preto, azul, vermelho, amarelo, verde, ciano, magenta, laranja, branco/borracha) e botão de limpar.

![Tela Paint](Paint/Tela_Paint.png)

### Blocos

- **Canvas.Touched:** desenha um ponto nas coordenadas tocadas
- **Canvas.Dragged:** desenha uma linha contínua do ponto anterior ao atual, criando o efeito de pincel
- **Slider.PositionChanged:** chama a função `thumbposition` que atualiza a `LineWidth` do canvas em tempo real
- **Botões de cor:** cada botão chama sua função correspondente (ex: `call verde`, `call azul`) que define o `PaintColor` do canvas
- **Borracha:** define a cor como branco, simulando apagar
- **Limpar:** chama `Canvas.Clear` para resetar o desenho

![Blocos Paint](Paint/Blocks_Paint.png)

---

### 🛠️ Arquivo do Projeto

```
Paint/Paint.aia
```

> Projeto criado dia 04 de abril de 2026

---

## 🚀 03 — Movendo Objetos (Foguete com Botões)

Foguete controlado por botões direcionais na tela. O sprite muda de imagem conforme a direção do movimento.

### Tela

Fundo espacial com um foguete no centro e quatro botões de seta (esquerda, cima, baixo, direita) na parte inferior.

![Tela Movendo Objetos](MovendoObjetos/Tela_MovendoObj.png)

### Blocos

- **alterarsprite (velocidade, direcao):** função reutilizável que define a velocidade e o heading (direção em graus) do sprite Foguete
- **Botão Esquerda:** muda a imagem para `Foguete_Esquerda.png` e chama `alterarsprite` com direção 180°
- **Botão Direita:** muda a imagem para `Foguete_Direita.png` e chama `alterarsprite` com direção 0°
- **Botão Cima:** muda a imagem para `Foguete_Cima.png` e chama `alterarsprite` com direção 90°
- **Botão Baixo:** muda a imagem para `Foguete_Baixo.png` e chama `alterarsprite` com direção 270°
- **Foguete.Dragged:** permite arrastar o sprite diretamente com o dedo

![Blocos Movendo Objetos](MovendoObjetos/Blocks_FogueteBtn.png)

---

### 🛠️ Arquivo do Projeto

```
MovendoObjetos/Movendo_Objetos.aia
```

> Projeto criado dia 7 de maio de 2026 de 2026

---

## ➕ 04 — Quiz Matemática

Quiz de operações matemáticas com geração aleatória de contas e sistema de pontuação.

### Tela

Interface simples com a operação exibida (ex: `1 + 1 =`), campo de resposta, placar no topo e botão Responder.

![Tela Quiz](QuizMatematica/Tela_QuizMat.png)


### Blocos

- **Variáveis globais:** `ValorX`, `ValorY`, `Sinal`, `Resultado`, `Pontuação` e `ListaSinais` (`+`, `-`, `x`)
- **inicializarOperações:** sorteia dois números (1–10), escolhe um sinal aleatório da lista, calcula o resultado correto conforme o sinal e exibe a operação no label. Para subtração, garante que o resultado nunca seja negativo trocando os valores se necessário
- **Responder.Click:** compara o texto digitado com o resultado; se correto, soma 10 pontos, exibe "Você Acertou!" em verde e mostra o botão Próxima; se errado, subtrai 10 pontos e exibe "Você Errou!" em vermelho
- **Próxima.Click:** limpa o campo, esconde o feedback e chama `inicializarOperações` para nova rodada
- **Pular.Click:** subtrai 10 pontos e vai para a próxima operação sem exigir resposta

![Blocos Quiz](QuizMatematica/Blocks_QuizMat.png)

---

### 🛠️ Arquivo do Projeto

```
QuizMatematica/Quiz_Matematica.aia
```

> Projeto criado dia 04 de maio de 2026

---

## 🦟 05 — Mate o Mosquito

Jogo de reflexo onde um mosquito se move aleatoriamente pela tela e o jogador deve tocá-lo antes que o tempo acabe.

### Tela

Canvas com fundo de sala de estar, contador de tempo (10s) e vidas (3) no topo, e botão Iniciar.

![Tela Mate Mosquito](MateMosquito/Tela_Moskito.png)

### Blocos

- **Variáveis globais:** `vida` (começa com 3), `tempo` (começa com 10), `jogando` (booleano)
- **MoverMosquito:** torna o sprite visível e posiciona em coordenadas X e Y aleatórias (0–270)
- **Iniciar.Click:** ativa os dois clocks, reseta o tempo para 10, chama `MoverMosquito` e verifica se o placar é "Fim de Jogo!" para resetar as vidas
- **Clock1.Timer (countdown):** a cada tick, se `jogando = true` e tempo > 0, decrementa o tempo e atualiza o label. Quando chega a zero: para os clocks, subtrai uma vida. Se ainda há vidas, reinicia o tempo para 10 e continua; se não há vidas, chama `FimdeJogo`
- **Clock2.Timer:** chama `MoverMosquito` em loop para movimentar o mosquito pela tela
- **Mosquito.Touched:** quando o jogador toca o mosquito, chama `FimdeJogo` (contabiliza como acerto/vitória da rodada)
- **FimdeJogo:** para tudo, esconde o mosquito, exibe dialog "Fim de Jogo! — Jogar Novamente"
- **Notifier.AfterChoosing:** se o jogador escolhe "Jogar Novamente", reseta vidas e estado para uma nova partida

![Blocos Mate Mosquito](MateMosquito/Blocks_Moskito.png)

---

### 🛠️ Arquivo do Projeto

```
MateMosquito/Mate_o_Mosquito.aia
```

> Projeto criado dia 11 de maio de 2026

---

## 🚀 06 — Foguete com Acelerômetro

Foguete controlado pela inclinação física do celular usando o sensor acelerômetro. Projeto em desenvolvimento.

### Tela

Canvas com foguete sprite e labels mostrando os valores X, Y e Z do acelerômetro em tempo real. Botões Iniciar e Parar.

![Tela Acelerômetro](MovendoObjetos2/Tela_Accel.png)

### Blocos

- **alterarsprite (velocidade, direcao):** define velocidade e heading do sprite, igual ao projeto de botões
- **AccelerometerSensor1.AccelerationChanged:** evento disparado a cada mudança de inclinação. Se `JogoIniciado = true`, atualiza os labels X, Y, Z e move o foguete:
  - Se `xAccel ≥ 0` → move para direita (`X + 5`)
  - Se `xAccel < 0` → move para esquerda (`X - 5`)
  - Se `yAccel ≥ 0` → move para baixo (`Y + 5`)
  - Se `yAccel < 0` → move para cima (`Y - 5`)
- **Iniciar.Click:** define `JogoIniciado = true`, ativando o movimento
- **Parar.Click:** define `JogoIniciado = false`, reseta os labels para 0 e retorna o foguete à posição central

![Blocos Acelerômetro](MovendoObjetos2/Blocks_FogueteAccel.png)

---

### 🛠️ Arquivo do Projeto

```
MateMosquito/Mate_o_Mosquito.aia
```

> Projeto criado dia 25 de maio de 2026

---

## 🛠️ Tecnologias Utilizadas

- [MIT App Inventor](https://appinventor.mit.edu)
- Android
- Programação visual com blocos

---

## 🔁 Como Replicar

1. Acesse [MIT App Inventor](https://appinventor.mit.edu)
2. Vá em **Projects → Import project (.aia) from my computer**
3. Selecione o arquivo `.aia` da pasta do projeto desejado
4. Explore as telas e blocos diretamente no editor

---

## ✏️ Autor

Desenvolvido por **Kayozkx**
Todos os projetos foram feitos do zero, sem uso de IA — apenas lógica própria e programação em blocos.

---

> Este repositório documenta a estrutura e lógica de cada app para fins de aprendizado e portfólio pessoal.
