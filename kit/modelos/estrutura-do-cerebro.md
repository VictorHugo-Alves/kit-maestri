# Estrutura sugerida do segundo cérebro

> A IA adapta às frentes e negócios da pessoa. Esta é só a base.

```
meu-cerebro/
├── CLAUDE.md               ← quem é a pessoa, regras, equipe (lido em toda sessão)
├── AGENTS.md               ← porta de entrada do Codex e outras IAs
├── INDICE.md               ← mapa de todos os arquivos, com link
├── .gitignore              ← o que nunca vai para o GitHub (segredos)
├── .env                    ← chaves e senhas (NUNCA vai para o git)
├── _contexto/
│   ├── ESTADO-ATUAL.md     ← onde parou, o que está pendente
│   └── decisoes/           ← uma decisão por arquivo: AAAA-MM-titulo.md
├── {{frente-ou-negocio-1}}/
├── {{frente-ou-negocio-2}}/
├── reunioes/               ← (opcional) resumo de cada reunião
├── processos/              ← (opcional) como fazer as coisas que se repetem
└── _referencia/            ← material de consulta (este kit, por exemplo)
```

## Modelo do INDICE.md

```markdown
# Índice

## Contexto
- [CLAUDE.md](CLAUDE.md): quem sou, regras e equipe
- [Estado atual](_contexto/ESTADO-ATUAL.md): onde paramos

## {{Frente 1}}
- [nome do arquivo](pasta/arquivo.md): uma linha do que é
```

## Modelo do _contexto/ESTADO-ATUAL.md

```markdown
# Estado atual
atualizado: {{data}}

## Onde paramos
- {{o que foi feito por último}}

## Pendências abertas
- [ ] {{pendência}} (de quem depende)

## Decisões recentes
- {{data}}: [{{título}}](decisoes/AAAA-MM-titulo.md)
```

## Modelo de decisão (_contexto/decisoes/AAAA-MM-titulo.md)

```markdown
# {{Título da decisão}}
data: {{AAAA-MM-DD}}

- **O que foi decidido:** ...
- **Por quê:** ...
- **Como aplicar:** ...
```
