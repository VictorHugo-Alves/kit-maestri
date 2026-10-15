# Kit Maestri: leia primeiro

Este kit monta, na sua máquina, uma equipe de IAs trabalhando juntas no **Maestri**, com memória no
**Obsidian** e histórico no **GitHub**. Você não precisa saber programar: a própria IA te entrevista e faz
o setup com você.

## O que tem aqui

| Arquivo | Para quem | Para que serve |
|---|---|---|
| `LEIA-PRIMEIRO.md` | você | este guia rápido |
| `SETUP-COM-IA.md` | **a sua IA** | o roteiro que a IA segue para te entrevistar e montar tudo |
| `GUIA-COMPLETO-MAESTRI.md` | você e a IA | tudo sobre o Maestri, para consulta |
| `modelos/` | a IA | arquivos-base que a IA preenche com o seu contexto |
| `referencia/COMANDOS-MAESTRI.md` | você e a IA | cola dos comandos do Maestri |
| `referencia/PROBLEMAS-COMUNS.md` | você e a IA | erros que já aconteceram e como resolver |

A aula visual (o que é cada ferramenta e por que importa) está na página onde você baixou este kit.

## Os 4 passos

1. **Assista à aula** na página do kit, para entender as três peças: Maestri, Obsidian e GitHub.
2. **Instale o Maestri** (site oficial: <https://themaestri.app>) e pelo menos uma IA de terminal:
   - **Claude Code** (precisa de assinatura do Claude): no Mac ou Linux, abra o Terminal e rode
     `curl -fsSL https://claude.ai/install.sh | bash`. No Windows, no PowerShell:
     `irm https://claude.ai/install.ps1 | iex`. Depois rode `claude` e faça login.
   - **Codex** (precisa de assinatura do ChatGPT): `npm install -g @openai/codex` (no Mac também dá
     `brew install --cask codex`). Depois rode `codex` e faça login.
3. **Crie uma pasta vazia** para ser o seu "segundo cérebro" (exemplo: `Documentos/meu-cerebro`) e
   **copie esta pasta do kit para dentro dela**.
4. **Abra o Maestri**, crie um workspace apontando para essa pasta, abra um terminal com o Claude Code
   (ou o Codex) e mande esta mensagem:

   > Leia o arquivo `kit-maestri/SETUP-COM-IA.md` e siga o roteiro comigo, do começo ao fim.

A IA vai te fazer perguntas sobre você e o seu negócio, explicar o que você não conhecer, e montar o
setup com você.

## Três regras de segurança

- **Nunca cole senha ou token no chat da IA.** O roteiro ensina a fazer login sem precisar disso.
- **Repositório do GitHub sempre privado** quando tiver dado do seu negócio.
- A IA executa comandos na sua máquina. Leia o que ela pede para aprovar antes de aprovar.
