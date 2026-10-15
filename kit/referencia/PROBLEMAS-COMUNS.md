# Problemas comuns (e como resolver)

> Tudo aqui aconteceu de verdade com a minha equipe (Victor Hugo). Formato: o que acontece, por quê, o que fazer.

### 1. O Codex fica parado esperando aprovação
- **Por quê:** o Codex pede aprovação para muitas ações e espera alguém responder.
- **O que fazer:** o Maestro aprova com `maestri ask "Nome" --raw "y"` (se a caixa continuar,
  `--raw $'\r'`); para cancelar, `--raw "\e"`. Tarefa que vai rodar sem ninguém olhando vai para um
  agente do Claude.

### 2. Todos os Claude passaram a abrir com o modelo mais fraco
- **Por quê:** digitar `/model sonnet` dentro do Claude Code grava o Sonnet como **padrão global**
  (no `~/.claude/settings.json`). Toda sessão nova, inclusive a do Maestro, passa a abrir em Sonnet.
- **O que fazer:** fixe o modelo de cada agente na hora de recrutar (`--command "claude --model sonnet"`)
  em vez de usar `/model`. Se já aconteceu, apague a linha `"model"` desse arquivo.

### 3. O agente do Codex abriu num terminal vazio
- **Por quê:** o Codex não estava instalado nessa máquina.
- **O que fazer:** confira com `codex --version` antes de recrutar. Instale (`npm install -g @openai/codex`;
  no Mac, se o npm falhar por permissão, `brew install --cask codex`) e faça login com `codex`.

### 4. Um agente gastou a cota da semana com tarefa simples
- **Por quê:** algumas IAs têm cota pequena no plano (aconteceu com o Gemini numa pesquisa simples).
- **O que fazer:** tarefa de volume vai para o modelo mais leve da assinatura maior. Troque a IA do
  terminal com `maestri recruit --replace`, sem perder as ligações.

### 5. Vários agentes mexeram no git ao mesmo tempo
- **Por quê:** todo mundo podia fazer commit.
- **O que fazer:** só o Maestro faz commit e push. Escreva isso no papel de cada agente e repita no pedido.

### 6. Um agente escreveu na memória que era só do Maestro
- **Por quê:** o modelo mais leve às vezes desobedece regra escrita só uma vez.
- **O que fazer:** repetir no próprio pedido ("não escreva no ESTADO-ATUAL") e o Maestro revisa.

### 7. Como saber se um agente terminou
- **O que fazer:** `maestri check "Nome"`. Enquanto aparecer "esc to interrupt" na tela, ele ainda está
  trabalhando.

### 8. Duas tarefas no mesmo agente e uma atropelou a outra
- **O que fazer:** uma frente por terminal. A segunda espera na fila do Quadro ou vai para outro agente.

### 9. `maestri recruit` responde que é só para o Maestro
- **Por quê:** o terminal onde você está não tem o modo Maestro ligado.
- **O que fazer:** ligue o modo Maestro nas opções desse terminal no Maestri, ou rode o comando no
  terminal que já é o Maestro.

### 10. O `git push` pede usuário e senha
- **Por quê:** o git não está usando o login do `gh`.
- **O que fazer:** num terminal separado, `gh auth login` (login pelo navegador) e depois `gh auth setup-git`.
  Nunca cole token no chat da IA.
