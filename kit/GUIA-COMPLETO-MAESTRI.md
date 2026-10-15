# Guia completo do Maestri

> Para consulta, de pessoas e de IAs. Planos e preços mudam: confira sempre no site oficial,
> <https://themaestri.app>.

## 1. O que é

**O Maestri é um aplicativo com uma tela infinita (canvas) onde você coloca vários agentes de IA lado a
lado, dá uma função para cada um e eles conversam entre si.**

Pensa numa **orquestra**. Cada IA é um músico que toca muito bem um instrumento. Sozinhos, cada um toca
a sua parte. O **Maestro** é quem lê a partitura, diz quem entra quando e garante que o resultado soe
como uma música só. No Maestri, o Maestro é uma IA também: você conversa com ele, e ele rege os outros.

Outra forma de ver: em vez de cinco janelas de IA soltas, com você correndo de uma para outra e
guardando na cabeça quem estava fazendo o quê, o Maestri é uma **sala de reuniões visual**. Cada agente
é uma mesa no quadro; você liga duas mesas com uma linha e elas passam a se falar. O estado do trabalho
fica visível, não só na sua cabeça.

O Maestri **não é uma IA**. É o palco. As IAs (Claude Code, Codex, Gemini, OpenCode) você instala e
assina à parte, e escolhe quais quer usar.

## 2. Por que usar

1. **Cada agente faz uma coisa só, e faz melhor.** Um lidera, um constrói, um confere, um pesquisa.
2. **Trabalho em paralelo.** Enquanto um agente monta o banco de dados, outro faz a tela e outro
   pesquisa. O que levaria uma tarde em fila sai em uma hora.
3. **Revisão cruzada.** Uma IA de outra empresa revisa o trabalho da primeira. Modelos diferentes erram
   em lugares diferentes, então um pega o erro que o outro não vê.
4. **Não depende de um fornecedor.** Dá para misturar Claude, ChatGPT (Codex) e outros no mesmo quadro.
5. **Rende mais a sua cota.** Tarefa pesada vai para o modelo forte; tarefa simples (pesquisa, teste,
   conferência) vai para um modelo mais leve. E cada assinatura tem a sua própria cota.
6. **Local e privado.** O app guarda tudo em arquivos na sua máquina (markdown e JSON). Atenção: as IAs
   continuam conversando com os servidores das empresas delas; isso é da IA, não do Maestri.

## 3. Conceitos

| Conceito | O que é |
|---|---|
| **Workspace** | Um projeto. Fica apontado para uma pasta do seu computador (o seu cérebro, por exemplo). |
| **Terminal** | Uma "mesa" no quadro, onde roda uma IA (ou um terminal comum). |
| **Preset** | O tipo de agente que abre no terminal: "Claude Code", "Codex", "OpenCode" etc. |
| **Maestro** | O terminal principal, com poder de recrutar, demitir e ligar os outros. Você fala com ele. |
| **Papel (role)** | O texto que diz ao agente quem ele é, o que faz e o que não faz. O agente abre já com isso. |
| **Linha (conexão)** | Liga dois terminais (ou um terminal e uma nota). Só quem está ligado conversa. |
| **Nota** | Um post-it em markdown no quadro. Ligada a vários agentes, vira memória compartilhada. |
| **Fichário** | Uma pilha de notas, para organizar. |
| **Portal** | Um navegador (ou simulador de celular) no quadro, que o agente consegue ver e operar. |
| **Floor (andar)** | Uma cópia do workspace em outra branch do git, para testar algo arriscado sem mexer no principal. |
| **Rotina** | Um comando ou lembrete agendado (a cada 30 min, todo dia às 9h etc.). |
| **Partitura** | Uma configuração de equipe salva (papéis, notas, portais, conexões) para reaplicar em outro projeto. |
| **Ombro** | Assistente local que acompanha os agentes e resume o que aconteceu enquanto você estava fora (no Mac, usa o Apple Intelligence). |

## 4. Instalar

1. Baixe o Maestri no site oficial (<https://themaestri.app>) para o seu sistema e instale.
2. Instale pelo menos uma IA de terminal e faça login nela:
   - **Claude Code** (assinatura do Claude): Mac e Linux `curl -fsSL https://claude.ai/install.sh | bash`;
     Windows (PowerShell) `irm https://claude.ai/install.ps1 | iex`. Depois `claude` para logar.
   - **Codex** (assinatura do ChatGPT): `npm install -g @openai/codex` ou, no Mac,
     `brew install --cask codex`. Depois `codex` para logar.
3. Abra o Maestri, crie um workspace apontando para a pasta do seu projeto e adicione um terminal com o
   preset da sua IA.
4. Confira que está tudo certo: no terminal, `maestri list` deve responder.

## 5. Montar uma equipe

O jeito fácil é pedir ao Maestro (o roteiro `SETUP-COM-IA.md` faz isso). Por baixo, são estes passos:

```bash
maestri list                                   # quem já existe (não recrute repetido)
maestri preset list                            # nomes exatos dos presets
maestri role create "Dados e conferência" "Seu papel: ..."
maestri recruit "VH" --preset "Claude Code" --role "Dados e conferência" --command "claude --model sonnet"
maestri recruit "Junior" --preset "Codex" --role "Front-end e dashboards"
maestri note create "# Quadro ..." --name "Quadro"
maestri ask "VH" "Confira os números da planilha X e me diga o que não bate."
```

### Exemplo real: a minha equipe de 5 terminais (Victor Hugo)

| Nome | IA | Função | Recebe quando |
|---|---|---|---|
| **Maestro** | Claude Code (Opus) | orquestra | é com quem eu falo: decide, divide, revisa, faz commit, push e publica |
| **JP** | Claude Code (Opus) | back-end e banco | banco de dados, regras de acesso, rotas de API, integrações |
| **Junior** | Codex (GPT) | front-end e dashboards | telas e painéis; revisa o código do JP com o olhar de outro modelo |
| **VH** | Claude Code (Sonnet) | dados e conferência | planilha grande, conferir número antes de ir para a liderança |
| **Arthur** | Claude Code (Sonnet) | pesquisa e teste | mapear documentação, pesquisar na web, testar depois de cada entrega |

Por que funciona: **cada terminal tem uma função fechada**. Quando havia dois "executores" iguais, o
Maestro não tinha critério de quem pegava o quê e acabava fazendo tudo sozinho.

## 6. Boas práticas de orquestração

1. **Fale só com o Maestro.** Texto que aparece digitado na caixa de um agente não é seu: é do Maestro.
2. **Só o Maestro faz commit, push e publica.** Os agentes entregam para ele. Cinco terminais
   disputando o mesmo repositório é receita para conflito e trabalho pela metade publicado.
3. **O Maestro revisa tudo** que volta antes de aceitar. Roda o teste de novo; não confia no "passou".
4. **Delegar por função, não por quem está livre.** Banco vai para quem é de banco, mesmo que outro
   esteja parado.
5. **Uma frente por terminal.** Não empilhe duas tarefas no mesmo agente; a segunda espera ou vai para
   outro.
6. **Quadro sempre atualizado.** Uma nota com FAZENDO, FEITO, ESPERANDO VOCÊ e BACKLOG, reescrita a
   cada etapa. Você bate o olho e sabe como está tudo.
7. **Memória mora no cérebro, não na conversa.** O que tem que ser lembrado vira arquivo (decisão,
   estado atual), escrito pelo Maestro.
8. **Modelo certo para cada tarefa.** Pesado com o forte, volume com o leve. Equilíbrio, não economia
   extrema.
9. **Comece pequeno.** Maestro + 2 ou 3. Cresça quando faltar braço, e saiba dizer por que precisa de
   mais um.

## 7. Cuidados

- **Cota:** cada agente consome a cota da assinatura dele. Cinco agentes do Claude ao mesmo tempo gastam
  rápido.
- **Memória do computador:** muitos terminais abertos pesam. Feche quem não está trabalhando.
- **Aprovações:** o Codex costuma parar pedindo aprovação. Tarefa que vai rodar sem você olhando vai para
  quem roda sozinho.
- **Regras claras:** escreva no papel de cada agente o que ele **não** pode fazer (publicar, apagar,
  mandar mensagem para alguém, mexer em senha).
- **Segredos:** chave e senha ficam num arquivo `.env` ignorado pelo git, nunca no chat e nunca em nota.

## 8. Perguntas frequentes

- **Preciso pagar o Maestri?** Existe plano gratuito. Planos e preços: confira no site oficial.
- **Preciso pagar as IAs?** Sim, à parte. O Maestri não substitui a assinatura do Claude ou do ChatGPT.
- **Funciona no Windows?** Sim. Alguns recursos (como o Ombro com Apple Intelligence) são do Mac.
- **Os agentes veem os arquivos uns dos outros?** Todos trabalham na mesma pasta do projeto, e
  compartilham o que estiver nas notas ligadas a eles. O resto é por mensagem.
- **É só para programador?** Foi feito para agentes de código, mas serve para dados, pesquisa,
  documentação, conteúdo e organização. Quem manda é o papel que você escreve.
- **E se eu fechar o app?** O quadro, as notas e os papéis ficam salvos. As conversas das IAs, não
  necessariamente: por isso a memória importante vai para arquivo.

## 9. Fontes

- Site oficial: <https://themaestri.app>
- Product Hunt: <https://www.producthunt.com/products/maestri>
- Ajuda do próprio app: `maestri help` e `maestri <comando> --help`
- A minha experiência (Victor Hugo) no dia a dia (outubro de 2026).
