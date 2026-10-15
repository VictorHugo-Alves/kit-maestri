# CLAUDE.md de {{NOME}}

> Modelo do kit Maestri. A IA preenche os campos {{ASSIM}} com as respostas da entrevista e apaga
> o que não se aplicar. Este arquivo é lido sozinho pelo Claude Code em toda sessão.

## Quem é

- **Nome:** {{NOME}} (prefere ser chamado de {{APELIDO}})
- **O que faz:** {{PROFISSAO_E_CARGO}}
- **Nível técnico:** {{NIVEL}} (explicar sem jargão quando for {{iniciante}})
- **Computadores:** {{UM_OU_MAIS}}

## O negócio

{{DESCRICAO_DO_NEGOCIO: o que vende, para quem, como funciona, números importantes}}

{{SE_TIVER_MAIS_DE_UM_NEGOCIO: lista de negócios e se são separados (cada um com seu cérebro) ou áreas deste}}

## Frentes de trabalho

- {{FRENTE_1}}: {{o que é}} → pasta `{{pasta}}`
- {{FRENTE_2}}: ...

## Como eu (a IA) devo agir

- Português do Brasil, {{TOM: direto ao ponto / mais explicado}}.
- **Nunca inventar** nome, número ou data. Faltou ou não bate: dizer que não sei.
- Antes de apagar, sobrescrever ou publicar algo: pedir confirmação.
- Nunca pedir senha ou token no chat.
- {{REGRAS_DA_PESSOA}}

## Onde fica cada coisa

- `INDICE.md`: mapa de todos os arquivos. **Arquivo novo ganha uma linha aqui na mesma hora.**
- `_contexto/ESTADO-ATUAL.md`: onde o trabalho parou e o que está pendente. **Ler no começo de toda sessão.**
- `_contexto/decisoes/`: uma decisão por arquivo (`AAAA-MM-titulo.md`), com data e o porquê.
- {{PASTAS_DAS_FRENTES}}

## Rotina de git {{apagar se não usar GitHub}}

1. Antes de começar a mexer: `git pull`.
2. Ao terminar cada tarefa: commit (mensagem curta em português dizendo o que mudou) e `git push`.
3. Nunca commitar segredo (`.env`, chaves, tokens). O `.gitignore` já bloqueia o básico.
4. Repositório: {{URL_DO_REPO}} (privado).

## Equipe no Maestri

| Nome | IA | Função |
|---|---|---|
| Maestro | {{IA}} | orquestra: fala com {{NOME}}, divide, revisa, faz commit, push e publica |
| {{NOME_1}} | {{IA}} | {{FUNCAO}} |
| {{NOME_2}} | {{IA}} | {{FUNCAO}} |

Regras da equipe:
- {{NOME}} fala só com o Maestro. O Maestro distribui por **função**, não por quem está livre.
- **Só o Maestro** escreve no `ESTADO-ATUAL.md`, faz commit, push e publica. Os agentes entregam para ele.
- O Maestro **revisa tudo** que volta antes de aceitar.
- Uma tarefa por agente por vez.
- A nota **Quadro** (FAZENDO, FEITO, ESPERANDO {{NOME}}, BACKLOG) é reescrita a cada etapa.
- Texto digitado na caixa de um agente não é de {{NOME}}; só vale o que {{NOME}} fala com o Maestro.
- Mudar a equipe (mais um agente, outro modelo) é **proposta** a {{NOME}}, com o porquê e o custo.
