# Kit Maestri

Aula visual e kit de setup para montar uma equipe de IAs no **Maestri**, com memória no **Obsidian** e
histórico no **GitHub**. Feito para os alunos da aula de outubro de 2026.

**Página da aula:** <https://victorhugo-alves.github.io/kit-maestri/>

## O que tem aqui

| Caminho | O que é |
|---|---|
| `index.html` | a aula visual, publicada no GitHub Pages |
| `kit-maestri.zip` | o kit para baixar (gerado a partir de `kit/`) |
| `kit/LEIA-PRIMEIRO.md` | guia rápido para o aluno |
| `kit/SETUP-COM-IA.md` | roteiro que a IA do aluno (Claude Code ou Codex) segue: entrevista e monta o setup |
| `kit/GUIA-COMPLETO-MAESTRI.md` | tudo sobre o Maestri, para consulta |
| `kit/modelos/` | modelos de `CLAUDE.md`, `AGENTS.md`, nota Quadro, estrutura do cérebro, `.gitignore` e papéis |
| `kit/referencia/` | cola de comandos do Maestri e problemas comuns |

## Decisões

- **Sem preço nem requisito de sistema nos textos:** as fontes divergiam; o texto manda conferir no site oficial.
- **Equipe de exemplo** é a real: Maestro, JP (back-end e banco), Junior (Codex, front-end e dashboards),
  VH (dados e conferência), Arthur (pesquisa e teste).
- **Login do GitHub pelo navegador** (`gh auth login`); token nunca vai para o chat da IA.
- Repositório público porque é material de aula, sem dado de empresa.
- **Celular:** todo ajuste de tela pequena fica num bloco `@media (max-width:640px)` no fim do CSS, para o
  desktop não mudar. Ali a linha do tempo do git vira vertical, os passos empilham, os botões ocupam a
  largura toda e o desenho "Uma pasta, três papéis" rola para o lado (com a dica "Arraste").

## Como atualizar

1. Edite os arquivos em `kit/` ou o `index.html`.
2. Regere o zip: `rm -f kit-maestri.zip && cp -R kit /tmp/kit-maestri && (cd /tmp && zip -rq - kit-maestri) > kit-maestri.zip && rm -rf /tmp/kit-maestri`
3. Commit e push na `main`. O Pages publica sozinho em cerca de um minuto.
