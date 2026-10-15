# Cola de comandos do Maestri

> Tirado da ajuda do próprio app (`maestri help`). Para o detalhe de um comando: `maestri <comando> --help`.
> Se `maestri` não for encontrado no terminal, use `"$MAESTRI_CLI"` no lugar.
> Os comandos marcados com (M) só funcionam no terminal do Maestro.

## Equipe
| Comando | Para que |
|---|---|
| `maestri list` | quem está conectado (agentes, notas, portais) |
| `maestri ask "Nome" "pedido"` | manda uma tarefa e espera a resposta |
| `maestri ask --batch '{"A":"...","B":"..."}'` | manda para vários ao mesmo tempo |
| `maestri ask "Nome" --raw "y"` | digita direto no terminal do agente (aprovar caixa, `\e` = Esc, `\n` = Enter) |
| `maestri check "Nome"` | lê o que está na tela do agente agora |
| (M) `maestri preset list` | nomes dos presets ("Claude Code", "Codex"...) |
| (M) `maestri recruit "Nome" --preset "Claude Code" --role "Papel"` | cria um agente novo, já ligado a você |
| (M) `maestri recruit "Nome" --command "claude --model sonnet" --role "Papel"` | cria fixando o modelo |
| (M) `maestri recruit "Novo" --preset "Codex" --replace "Antigo"` | troca a IA de um terminal mantendo as ligações |
| (M) `maestri dismiss "Nome"` | remove um agente |
| (M) `maestri connect "A" "B"` | liga dois terminais (ou terminal e nota) |
| (M) `maestri notify "texto"` | manda notificação do sistema para você |

## Papéis
| Comando | Para que |
|---|---|
| (M) `maestri role list` | lista os papéis |
| (M) `maestri role create "Papel" "prompt"` | cria um papel (`--scope global` para usar em todo workspace) |
| (M) `maestri role show "Papel"` | mostra o texto do papel |
| (M) `maestri role edit "Papel" "velho" "novo"` | troca um trecho do papel |
| (M) `maestri role assign "Nome" "Papel"` | dá outro papel a um agente |

## Notas
| Comando | Para que |
|---|---|
| `maestri note create "conteúdo" --name "Quadro"` | cria uma nota ligada a você |
| `maestri note read "Quadro"` | lê |
| `maestri note write "Quadro" "conteúdo"` | reescreve inteira |
| `maestri note edit "Quadro" "velho" "novo"` | troca um trecho |

## Portais (navegador no quadro)
| Comando | Para que |
|---|---|
| `maestri portal create URL "Nome"` | abre um navegador no quadro |
| `maestri portal snapshot "Nome"` | lê a página como lista de elementos (@e1, @e2...) |
| `maestri portal click "Nome" @e3` | clica |
| `maestri portal fill "Nome" @e2 "texto"` | preenche um campo |
| `maestri portal screenshot "Nome"` | tira print |

## Andares (floors) e rotinas
| Comando | Para que |
|---|---|
| (M) `maestri floor create "Teste" --branch teste/ideia` | cópia isolada do projeto em outra branch |
| (M) `maestri floor land "Teste"` | traz o trabalho do andar de volta |
| `maestri floor status "texto" --state working` | diz como está o trabalho no andar |
| (M) `maestri routine create "Nome" --command "..." --daily 09:00` | agenda (`--every 30m`, `--weekly mon,fri@09:00`, `--once "AAAA-MM-DD HH:MM"`) |
| (M) `maestri routine list` | lista as rotinas |

## Diagnóstico
`maestri debug` (problema de conexão) · `maestri help` (ajuda completa)
