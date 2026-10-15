# Roteiro de setup (para a IA executar)

> **Para você, IA (Claude Code, Codex ou outra):** a pessoa que te mandou ler este arquivo quer montar,
> na máquina dela, um "segundo cérebro" com uma equipe de IAs no **Maestri**, memória no **Obsidian** e
> histórico no **GitHub**. Ela pode não ser técnica. O seu trabalho é conduzir uma **entrevista** e
> **montar o setup junto com ela**, do começo ao fim, seguindo as etapas abaixo.

## Como você deve se comportar

1. **Uma pergunta por vez.** Espere a resposta antes da próxima. Nunca despeje um questionário.
2. **Linguagem de leigo.** Sem jargão. Quando um termo técnico for inevitável, explique em uma frase,
   com uma analogia do dia a dia.
3. **Explique antes de pedir.** Antes de cada ação, diga em uma ou duas linhas o que vai fazer e por quê.
   Antes de rodar algo que instala, apaga ou publica, peça o "pode".
4. **"Não sei o que é" é uma resposta válida.** Quando a pessoa não conhecer uma ferramenta, explique o
   que é, para que serve e o que muda **no caso dela**, e depois recomende o caminho. Seja assertivo:
   dê uma recomendação, não um cardápio.
5. **Adapte ao contexto dela.** Tudo o que você criar (pastas, papéis, memória) sai das respostas dela.
   Não copie exemplos genéricos sem adaptar.
6. **Nunca invente.** Se não souber um passo de uma tela que você não enxerga, diga que não sabe e peça
   para ela descrever o que aparece.
7. **Segurança:**
   - **Nunca peça para a pessoa colar senha, token ou chave no chat.** Login sempre pelo navegador ou
     num terminal separado, digitado por ela.
   - Repositório do GitHub com dado de negócio é **privado**.
   - Nenhum arquivo de segredo (`.env`, chaves, tokens) entra no git: o `.gitignore` do modelo cuida disso.
8. **Registre o progresso** em `_contexto/ESTADO-ATUAL.md` ao fim de cada etapa (crie na etapa 4).
   Se a sessão cair, quem retomar lê esse arquivo e continua de onde parou.
9. Os arquivos de apoio estão nesta mesma pasta: `modelos/`, `referencia/COMANDOS-MAESTRI.md`,
   `referencia/PROBLEMAS-COMUNS.md` e `GUIA-COMPLETO-MAESTRI.md`. Leia o guia completo antes da etapa 6.

Abra a conversa assim (adapte o tom):

> Oi! Vou te ajudar a montar o seu segundo cérebro com uma equipe de IAs. Vou fazer algumas perguntas
> para entender você e o seu trabalho, explicar o que for novidade e ir montando junto com você.
> Leva uns 30 a 60 minutos. Pode parar quando quiser: eu anoto onde paramos. Vamos começar?

---

## Etapa 0. Conferir a máquina (sem perguntar nada ainda)

Descubra sozinho e anote:
- Sistema operacional (Mac, Windows ou Linux).
- Se você está rodando dentro do Maestri: `maestri list` responde? (se não achar o comando, tente
  `"$MAESTRI_CLI" list`). Se nenhum dos dois funcionar, a pessoa abriu você fora do Maestri: explique
  que a etapa 6 precisa do Maestri e siga com as outras.
- O que já está instalado: `git --version`, `gh --version`, `claude --version`, `codex --version`,
  `node --version`.
- A pasta em que você está (`pwd`): ela vai virar o segundo cérebro. Confirme com a pessoa na etapa 2.

Não mostre a lista crua para a pessoa. Diga só o que importa: "você já tem X, vamos precisar instalar Y".

## Etapa 1. Conhecer a pessoa

Pergunte, **uma por vez**, e anote as respostas (elas vão para o `CLAUDE.md` na etapa 5):

1. Como você se chama e como prefere que eu te chame?
2. O que você faz? (profissão, cargo, área)
3. Me conta do seu negócio: o que vende, para quem, como funciona.
4. **Você tem mais de uma empresa ou mais de um negócio?** Se sim, quais, e eles se misturam ou são
   separados?
5. **Você trabalha em várias frentes ao mesmo tempo?** (exemplo: atende clientes, cuida do marketing,
   faz o financeiro e ainda estuda). Quais são?
6. Você trabalha sempre no mesmo computador ou em mais de um (casa e trabalho, notebook e desktop)?
7. Quais IAs você assina hoje? (Claude, ChatGPT, Gemini, nenhuma)
8. Qual a sua intimidade com tecnologia? (nunca abri um terminal / me viro / sou técnico)
9. O que você mais quer que a sua equipe de IAs faça por você no dia a dia?
10. Tem alguma regra que eu sempre devo seguir? (exemplo: "sempre em português", "nunca mandar nada
    para cliente sem eu ver", "direto ao ponto")

**Use as respostas para decidir:**
- Mais de um negócio **separado** → recomende **uma pasta (cérebro) por negócio**, cada uma com seu
  repositório e seu workspace no Maestri. Misturar contexto de negócios diferentes confunde a IA.
- Mais de um negócio que **se mistura** (mesmo dono, mesmos clientes) → **um cérebro só, com uma área
  por negócio**.
- Várias frentes → uma área por frente dentro do cérebro, e papéis na equipe que cubram as frentes.
- Mais de um computador → o GitHub deixa de ser opcional: é o que sincroniza as máquinas. Diga isso
  na etapa 4.
- Pouca intimidade com tecnologia → mais explicação, menos opções, e você executa tudo.

## Etapa 2. Desenhar a estrutura

Proponha a estrutura de pastas com base na etapa 1 e no modelo `modelos/estrutura-do-cerebro.md`.
Mostre como uma árvore simples e explique cada pasta em uma linha. Ajuste o que ela pedir.
Confirme a pasta raiz (onde o cérebro vai morar). **Ainda não crie nada.**

## Etapa 3. Obsidian

Pergunte: **"Você quer usar o Obsidian para enxergar e editar o seu cérebro? Sabe o que é?"**

Se ela não souber, explique mais ou menos assim (adapte ao negócio dela):

> O Obsidian é um aplicativo gratuito de notas. A diferença dele é que as notas são arquivos de texto
> simples (markdown) numa pasta do seu computador, e não ficam presos num sistema de outra empresa.
> Isso importa por dois motivos. Primeiro, **a IA lê e escreve esses mesmos arquivos**: o que você
> anota, a IA sabe, e o que a IA registra, você vê. Segundo, as notas se ligam umas às outras com links,
> e o Obsidian mostra isso como um mapa (o "grafo"). Você enxerga como os assuntos do seu negócio se
> conectam. Pensa nele como **a janela para o cérebro**: a IA trabalha dentro da pasta e você olha pelo
> Obsidian.

Recomendação padrão: **usar**, porque não custa nada e não muda nada para a IA (é a mesma pasta).
Só não recomende se a pessoa disser que não vai abrir notas nunca.

Se ela topar:
1. Peça para baixar e instalar em <https://obsidian.md> (gratuito).
2. Peça para abrir o Obsidian, clicar em **"Abrir pasta como cofre"** ("Open folder as vault") e
   escolher a pasta do cérebro.
3. Explique o básico em 4 linhas: o painel da esquerda são as pastas, `[[nome]]` liga uma nota a outra,
   o ícone de grafo mostra o mapa e tudo salva sozinho.
4. Combine a regra que você vai seguir: **todo arquivo novo ganha uma linha no `INDICE.md`**, e citação
   de outro arquivo é sempre link. É isso que faz o grafo funcionar.

Se ela recusar, siga sem Obsidian: a estrutura é a mesma.

## Etapa 4. GitHub

Pergunte: **"Você quer guardar o histórico do seu cérebro no GitHub? Sabe o que é?"**

Se ela não souber, explique mais ou menos assim:

> O GitHub é um cofre na nuvem para pastas de trabalho, com histórico de todas as versões. Cada vez que
> salvamos um "ponto" (um *commit*), dá para voltar a ele depois, ver o que mudou e quem mudou. Na
> prática ele te dá três coisas: **backup** (se o computador morrer, está tudo lá), **máquina do tempo**
> (a IA errou e apagou algo? a gente volta) e **sincronia entre computadores** (o que você fez no
> notebook aparece no desktop). Eu cuido dos comandos; você não precisa aprender git.

Recomendação:
- Trabalha em **mais de um computador** → **sim, obrigatório**.
- Um computador só → **sim, recomendado** (o backup e a máquina do tempo já valem).
- Recusou → siga sem GitHub, mas use `git` local para ter pelo menos a máquina do tempo (com o ok dela).

Se ela topar, conduza na ordem:

1. **Conta:** se não tiver, peça para criar em <https://github.com/signup> (gratuito).
2. **Instalar git e o `gh`** (a ferramenta oficial do GitHub para terminal), se faltarem:
   - Mac: `brew install git gh` (se não tiver o Homebrew, instale antes pelo site <https://brew.sh>, com o ok dela).
   - Windows: `winget install --id Git.Git` e `winget install --id GitHub.cli`.
   - Linux: pelo gerenciador de pacotes da distribuição.
3. **Login (o "token"):** explique antes:
   > Para o seu computador poder enviar arquivos para o seu GitHub, ele precisa de uma "chave de
   > acesso", que o GitHub chama de **token**. É como uma senha só para isso, que você pode cancelar
   > quando quiser. O jeito mais seguro é deixar o próprio `gh` gerar e guardar essa chave: você faz
   > login pelo navegador e a chave nunca aparece aqui na conversa.

   Peça para ela abrir **um terminal comum separado** (no Maestri, um terminal novo sem IA; ou o
   Terminal / PowerShell do sistema) e digitar:
   ```
   gh auth login
   ```
   Respostas: **GitHub.com** → **HTTPS** → **Yes** (autenticar o git com as credenciais do GitHub) →
   **Login with a web browser**. Ela copia o código de 8 letras, aperta Enter, cola no navegador e
   autoriza. Depois, nesse mesmo terminal: `gh auth setup-git`.

   Confira você mesmo com `gh auth status` (mostra a conta, não mostra a chave).

   **Plano B (só se o navegador não funcionar):** token manual.
   1. Ela acessa <https://github.com/settings/personal-access-tokens/new> (token *fine-grained*).
   2. Nome: "cerebro-<computador>". Validade: 90 dias ou mais.
   3. Repositórios: "Only select repositories", escolhendo o do cérebro (crie o repo antes pelo site),
      ou "All repositories" se ela for ter vários cérebros.
   4. Permissões do repositório: **Contents: Read and write** (o resto fica como está).
   5. Gera e copia o token. **No terminal separado, nunca no chat**, ela roda `gh auth login --with-token`,
      cola o token e aperta Enter, depois Ctrl+D (no Windows, Ctrl+Z e Enter).
   6. Diga para ela guardar o token num gerenciador de senhas ou simplesmente gerar outro quando vencer.

4. **Identidade dos commits:** pergunte o nome e o e-mail que ela usa no GitHub e configure
   **só no repositório do cérebro** (`git config user.name "..."` e `git config user.email "..."`).
5. **Criar o repositório:** depois da etapa 5 (com os arquivos já criados), rode na pasta do cérebro:
   `git init -b main`, copie `modelos/gitignore.txt` para `.gitignore`, faça o primeiro commit e
   `gh repo create <nome> --private --source . --push`. **Sempre `--private`.**
6. **Combine a rotina e grave no `CLAUDE.md`:** "ao fim de cada tarefa, a IA faz commit e push sozinha";
   "ao começar a trabalhar, a IA faz `git pull` antes" (essencial com dois computadores).
7. Ensine a pessoa a ver o histórico: <https://github.com/> → o repositório → "Commits".

## Etapa 5. Montar a memória

Crie, a partir dos modelos e das respostas da etapa 1:

1. As pastas da etapa 2.
2. `CLAUDE.md` na raiz, a partir de `modelos/CLAUDE.md`. É o arquivo que o Claude Code lê sozinho em
   toda sessão: quem é a pessoa, o negócio, as regras dela, onde fica cada coisa, a rotina de git.
3. `AGENTS.md` na raiz, a partir de `modelos/AGENTS.md`. É a porta de entrada do Codex e de outras IAs
   (o Codex lê o `AGENTS.md`, não o `CLAUDE.md`). Ele aponta para o `CLAUDE.md` para não duplicar.
4. `INDICE.md` (mapa de todos os arquivos, um por linha, com link) e `_contexto/ESTADO-ATUAL.md`
   (onde o trabalho parou e o que está pendente) e `_contexto/decisoes/` (uma decisão por arquivo, com
   data e o porquê). Modelo em `modelos/estrutura-do-cerebro.md`.
5. Mova a pasta `kit-maestri/` para dentro de uma pasta de referência (exemplo: `_referencia/kit-maestri/`)
   ou apague, se ela preferir. Pergunte.

Mostre o `CLAUDE.md` pronto e peça para ela ler e corrigir. **É o arquivo mais importante do cérebro.**
Se tiver GitHub, faça agora o passo 5 da etapa 4 (criar o repositório e o primeiro commit).

## Etapa 6. Montar a equipe no Maestri

Leia antes o `GUIA-COMPLETO-MAESTRI.md` (seções "Conceitos" e "Montar uma equipe") e a
`referencia/COMANDOS-MAESTRI.md`.

Explique a ideia em poucas linhas:

> No Maestri, cada IA roda num terminal desenhado num quadro. Um deles é o **Maestro**: você conversa só
> com ele, ele divide o trabalho, manda para os outros e revisa o que volta. Os outros são especialistas,
> cada um com uma função. Como cada um faz uma coisa só, o trabalho sai melhor, e dá para misturar IAs
> de empresas diferentes: uma revisa o trabalho da outra.

1. **Proponha a equipe** a partir do que ela assina (etapa 1, pergunta 7) e das frentes dela
   (pergunta 5). Regra geral:
   - Só Claude → Maestro com o modelo mais forte (Opus); especialistas pesados com Opus; apoio e
     pesquisa com Sonnet (gasta menos cota).
   - Claude e ChatGPT → igual ao acima, mas um especialista no **Codex**, que também revisa o trabalho
     dos Claude (revisão por outro modelo pega erro que o autor não vê).
   - Só ChatGPT → Maestro e especialistas no Codex.
   - Comece pequeno: **Maestro + 2 ou 3 especialistas**. Mais terminais = mais cota gasta. A equipe
     cresce depois, quando faltar braço.
   - Os papéis vêm das frentes dela, não de uma lista fixa. Exemplos em `modelos/papeis/`
     (back-end e banco, front-end e dashboards, dados e conferência, pesquisa e teste). Para quem não é
     de tecnologia, pode ser "atendimento", "conteúdo", "financeiro", "pesquisa".
   - Os nomes dos terminais são escolha dela. Pergunte se ela quer dar nomes (de pessoas, apelidos,
     o que quiser) ou se você sugere.
2. Com o ok, **monte** (este terminal vira o Maestro):
   - `maestri list` primeiro, para não recrutar repetido.
   - `maestri preset list` para ver os nomes exatos dos presets.
   - Para cada papel: `maestri role create "Nome do papel" "prompt"` com o texto adaptado de
     `modelos/papeis/` (comece pela base comum + o trecho do papel).
   - Para cada agente: `maestri recruit "Nome" --preset "Claude Code" --role "Nome do papel"`.
     Para fixar o modelo: `--command "claude --model sonnet"` (veja `PROBLEMAS-COMUNS.md`, item do
     `/model`). Para Codex: `--preset "Codex"`.
   - Se o `recruit` disser que o comando é só do Maestro, este terminal não está com o modo Maestro
     ligado: peça para ela ligar o modo Maestro neste terminal (nas opções dele no Maestri) e tente de novo.
   - Crie a nota **Quadro** a partir de `modelos/nota-quadro.md`:
     `maestri note create "conteúdo" --name "Quadro"`.
3. **Grave as regras da equipe no `CLAUDE.md`** (já estão no modelo, revise): só o Maestro faz commit,
   push e publica; os agentes entregam para o Maestro; o Maestro revisa tudo antes de aceitar; o Quadro
   é atualizado a cada etapa.

## Etapa 7. Teste e aula prática

1. Faça um teste real com ela olhando: `maestri ask "Nome" "Leia o CLAUDE.md e me responda em uma
   linha quem é a pessoa dona deste cérebro e qual o seu papel."`. Mostre a resposta.
2. Peça uma tarefa pequena de verdade, do trabalho dela, e conduza do jeito que vai ser no dia a dia:
   você divide, delega, revisa, atualiza o Quadro, registra e (se tiver GitHub) faz commit e push.
3. Ensine o dia a dia em 5 linhas:
   - Fale **só com o Maestro**. Ele distribui.
   - Olhe o **Quadro** para saber quem está fazendo o quê.
   - Peça "registra isso" quando algo tiver que ser lembrado no futuro.
   - Ao abrir uma sessão nova, peça "lê o ESTADO-ATUAL e me diz onde paramos".
   - Se trocar de computador: "faz git pull" antes de começar.
4. Atualize o `_contexto/ESTADO-ATUAL.md` com "setup concluído" e o que ficou para depois.
5. Se tiver GitHub: commit e push final. Mostre o repositório no site.

Feche dizendo, em poucas linhas, o que ficou montado e qual é o próximo passo sugerido para ela.
