# Documentação do Sistema - Atlas (The Wizard)

O **Atlas**, codinome **The Wizard**, é um assistente pessoal inteligente projetado para atuar como um companheiro proativo em seu ambiente de trabalho. Utilizando visão computacional e processamento de áudio em tempo real, o Atlas observa suas atividades e fornece insights, dicas técnicas e suporte à produtividade sem a necessidade de comandos constantes.

---

## 1. História, Inspiração e Créditos

### 🌟 A Origem e a Quinta Onda

O desenvolvimento do **Atlas** (originalmente The Wizard) é fruto da colaboração direta com a **Comunidade Quinta Onda**, que apoia o projeto desde o seu lançamento inicial em 2022. Desenvolvido em **Electron**, o projeto evoluiu de um simples assistente para uma companhia de IA completa.

[🎥 Vídeo da V1 (YouTube)](https://www.youtube.com/watch?v=-BsOOXYJIIA)

### 📖 Storytelling & Inspiração

A criação do Atlas foi inspirada por uma narrativa moderna de "Cyberpunk Real":

> _"Um aluno de uma universidade da Ivy League acaba de lançar um aplicativo de IA que pode fornecer respostas em tempo real aos usuários... decidi testá-lo para ver se a IA conseguiria responder a perguntas de entrevistas de emprego tão bem quanto eu."_

A faísca veio da história de **Chungin "Roy" Lee**, o estudante da Columbia que viralizou com o **Cluely** — uma ferramenta polêmica para "hackear" entrevistas, analisando a tela e o áudio em tempo real para sugerir respostas. Roy foi suspenso, mas sua startup levantou milhões e atraiu milhares de usuários, provando o poder da IA em tempo real.

Também nos inspiramos em **Lucas Montano**, criador do **Persua**, que também explorou conceitos inovadores de assistência em tempo real e serviu de inspiração para o próprio projeto do Roy.

O Atlas nasce dessa mesma premissa de **inteligência aumentada em tempo real**, mas com um propósito diferente: não apenas dar respostas, mas ser um companheiro de jornada, um "segundo cérebro" que vive no seu monitor.

### 🤝 Créditos

- **Desenvolvimento:** Atos
- **Apoio e Comunidade:** Quinta Onda (Desde 2022)

---

## 2. Modos de Operação (Canais de Percepção)

O Atlas "percebe" o mundo através de três canais principais:

- **🧠 Cérebro (Chat e Microfone):** Interação direta. Você pode perguntar coisas via teclado (Alt+Space) ou falar diretamente com o Atlas (Alt+M). Neste modo, ele mantém a memória da conversa.
- **👁️ Olho (Contexto Visual):** Adiciona mensagens com contexto visual quando habilitado. O Atlas pode "ver" o que você está trabalhando para dar respostas mais úteis.
- **🎧 Ouvido (Áudio do Sistema):** O Atlas pode ouvir o áudio que sai do seu computador (vídeos, reuniões, podcasts) para complementar o contexto da tela ou atuar como um glossário em tempo real (Também requer permissão).

---

## 3. Interface do Usuário

A interface foi projetada para ser minimalista e não obstrutiva:

- **The Orb (Avatar Visual):** Uma representação visual dinâmica do Atlas que brilha e se move conforme ele processa informações ou está ouvindo.
- **Floating Island / Top Bar:** Uma barra superior elegante que dá acesso rápido ao monitoramento, configurações, modo fantasma e notas.
- **Insight Bubbles:** Pequenos cartões que surgem no canto da tela com informações automáticas. Eles possuem um "fade-out" automático, mas congelam ao passar o mouse.
- **Ghost Mode (Modo Invisível):** Ativa a transparência máxima para que o Atlas quase desapareça, mantendo apenas o essencial visível.

---

## 4. Ferramentas Integradas

### 📝 Notas Rápidas

Um painel lateral (Alt+N) para capturar pensamentos.

- **Editor Rico:** Suporta formatação, listas, negrito e imagens.
- **Auto-save:** Suas notas são salvas automaticamente em um banco de dados local (SQLite).

### 🕒 Histórico e Logs

- **Histórico de Chat:** Acesso rápido às conversas anteriores (Alt+H).
- **Log de Insights:** O Atlas permite abrir a pasta com todos os arquivos de insights capturados para consulta posterior.

### 🛠️ Tool Calling

O Atlas possui a capacidade de usar "ferramentas" internas, como pesquisar notícias, capturar a tela sob demanda, verificar processos do sistema ou até buscar dados em APIs externas (como Pokémon para demos).

---

## 5. Atalhos de Teclado (Hotkeys)

| Atalho           | Ação                                                |
| :--------------- | :-------------------------------------------------- |
| `Alt + Space`    | Abre/Fecha o campo de chat.                         |
| `Alt + H`        | Abre/Fecha o histórico de mensagens.                |
| `Alt + M`        | Ativa/Desativa o microfone (se configurado).        |
| `Alt + B`        | Repete a última notificação do Atlas por voz/texto. |
| `MediaPlayPause` | Alternar Modo de Voz (Realtime API)                 |

---

## 6. Configurações Avançadas

O App permite um alto grau de customização técnica:

- **Modelos de IA:** Você pode escolher modelos diferentes para Visão, Chat, Áudio e Sumarização (ex: GPT-4o, GPT-4o-mini).
- **Ollama Integration:** Suporte nativo para rodar modelos localmente (Llama 3, Mistral, etc.) via URL do Ollama.
- **Realtime API:** Modo de voz ultra-rápido com latência mínima para conversas naturais.
- **Webhook Server:** O app possui um servidor Express interno (`/webhook`) para receber notificações de serviços externos.

---

## 7. Instalação e Requisitos

**📥 Download:** [Release 1.0.15 (GitHub)](https://github.com/omagodev/the_wizard/releases/tag/1.0.15)

1.  **Chave de API:** Requer uma chave da OpenAI (ou Ollama local).
2.  **Áudio:** Para capturar o áudio do sistema (Modo Ouvido), recomenda-se o uso de um cabo virtual (como VB-Cable) se o sistema operacional não suportar loopback nativo.
3.  **Permissões:** Deve ter permissão de captura de tela e microfone.

---

## 8. Guia de Sobrevivência e Interação (Novos Recursos)

### 🔌 Webhooks (Integração)

Você pode enviar notificações ou comandos externos para a Atlas via HTTP POST.

- **Porta:** `3333`
- **Endpoint:** `/webhook`
- **Payload JSON:**
  ```json
  {
    "text": "Mensagem para exibir",
    "type": "notification", // ou "input" para tratar como fala do usuário
    "notify": true
  }
  ```

### 🥩 Alimentação e Energia

A Atlas possui um sistema vital simulado:

- **Fome (Comida):** Decai com o tempo. Se chegar a 0, ela fica fraca.
- **Como alimentar:** Clique no ícone de **Comida (🥩)**.
- **Custo:** Você precisa ter "Comida Disponível" no inventário.
- **Ganhando Comida:** Complete 5 ciclos de desenvolvimento (barra de progresso circular) para ganhar +1 item de comida.
- **Limite:** Máximo de 10 itens no estoque.

### 🧠 Sistema de Memória

- **Curto Prazo:** Lembra o contexto da conversa atual.
- **Fatos (Longo Prazo):** Coisas importantes que você diz (nomes, gostos) são salvas no banco de dados.
- **Resumo Automático:** Periodicamente, a Atlas resume conversas longas para manter o contexto sem estourar o limite de tokens.

### 💀 Morte e Renascimento

- **Morte:** Se a Atlas for negligenciada ao extremo (Saúde 0), ela "morre".
- **Tela de Kill Switch:** Uma tela especial aparece bloqueando o uso.
- **Renascimento:** Você pode revivê-la (via botão/comando), o que reseta seus atributos para o padrão de fábrica, permitindo um novo começo.

---

### 🐛 Bugs e Suporte

Este projeto está em desenvolvimento ativo e **pode conter bugs**.
Se você encontrar problemas, por favor reporte para nós:

- **Instagram:** [@omago.dev](https://www.instagram.com/omago.dev/)
- **GitHub:** Abra uma _Issue_ neste repositório.

Agradecemos o seu feedback para tornar o Atlas cada vez melhor!

---

_Documentação gerada para a versão 1.0.16._
