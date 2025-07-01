# 1. O que é Git?

## 1.1 Versionamento de Código

O versionamento é a prática de registrar mudanças em arquivos ao longo do tempo. Ele permite que você:

- Acesse versões anteriores de um projeto;
- Recupere arquivos antigos;
- Desenvolva em colaboração com outras pessoas;
- Entenda o histórico de alterações do código.

## 1.2 O que é o Git?

O **Git** é um sistema de controle de versão distribuído que armazena os registros de um projeto como **snapshots** — ou seja, “fotos” do estado dos arquivos em determinados momentos, e não apenas como diferenças entre eles.

Cada vez que você realiza um **commit**, o Git salva um snapshot completo do seu projeto e registra uma referência para ele, tornando possível navegar por esse histórico com facilidade.

### Principais vantagens:

- A maioria das operações opera localmente, garantindo agilidade nas operações sendo quase instantâneas devido a facilidade de acessar arquivos em seu próprio computador. (como `add`, `commit`, `log`);
- Possui ferramentas para colaboração remota (via GitHub, GitLab, etc.);
- Permite múltiplas versões paralelas do projeto por meio de **branchs**;
- Possui comandos para fusão de alterações, resolução de conflitos e muito mais.
  Perfeito! Aqui está a segunda seção formatada para o curso com **títulos**, **blocos de código**, **texto corrido** e um estilo educacional coeso:

---

# 2. Instalação do Git

## 2.1 Download

Você pode baixar o Git diretamente do site oficial:

[https://git-scm.com/downloads](https://git-scm.com/downloads)

![Pasted image 20250624125540](https://github.com/user-attachments/assets/c9787c6c-85b4-4091-889b-adb952f8de45)

A instalação segue o padrão do seu sistema operacional (Windows, macOS ou Linux). Após instalado, o Git pode ser usado via terminal (prompt de comando, bash, zsh, etc.).

## 2.2 Testando a Instalação

Para verificar se o Git foi instalado corretamente, execute no terminal:

```bash
git --version
```

Se tudo estiver certo, o terminal exibirá a versão instalada.

## 2.3 Configuração Inicial

Após instalar, configure o nome do usuário, o e-mail e defina o nome da branch padrão como `main`:

```bash
git config --global user.name "Seu Nome"
git config --global user.email seuemail@dominio.com
git config --global init.defaultBranch main
```

> Essa configuração será usada em todos os repositórios locais criados por você.

### Por que usar `main` como branch principal?

Historicamente, o Git usava o nome `master` como branch padrão. Porém, a comunidade passou a evitar esse termo por sua associação com uma linguagem historicamente ligada à escravidão (master/slave). Desde 2020, plataformas como GitHub passaram a adotar `main` como padrão, promovendo uma linguagem mais inclusiva.

## 2.4 Verificando as Configurações

Para checar as configurações que você definiu, use:

```bash
git config --list
```

Aqui está a seção **"Repositórios do Git – Dois caminhos"** revisada com estrutura didática, uso de títulos, texto corrido, blocos de código e destaques:

# 3. Repositórios do Git

## 3.1 Dois Caminhos para Começar

### Caminho 1: Clonar um Repositório Remoto

![Pasted image 20250624130333](https://github.com/user-attachments/assets/c263110a-395a-4ce7-84eb-7596547b25bd)

Quando você já tem um repositório hospedado em uma plataforma como o GitHub, GitLab ou Bitbucket, pode trazê-lo para sua máquina com o comando:

```bash
git clone <>
```

![Pasted image 20250624130519](https://github.com/user-attachments/assets/0e31b191-cb94-4c82-9e9b-a7c32d3e438f)
Isso cria uma nova pasta com todos os arquivos do projeto, além de uma subpasta oculta chamada `.git`.

#### O que é a pasta `.git`?


![Pasted image 20250624130659](https://github.com/user-attachments/assets/5610a297-c37b-4382-ab93-19204cae45cf)
Após executar `git clone`, o Git cria automaticamente a pasta oculta `.git`, que guarda **todo o histórico de commits**, **referências a branches**, **configurações remotas**, entre outras informações.  
Essa pasta é o coração do repositório local e **não deve ser alterada manualmente**. Ela é oculta justamente para proteger esses dados.

### Caminho 2: Iniciar um Repositório Local

Você também pode iniciar um repositório Git localmente em uma pasta já existente no seu computador. Para isso, navegue até o diretório desejado no terminal e execute:

```bash
git init
```

Saída esperada:

```bash
Initialized empty Git repository in C:/Users/diogomasc/Documents/Workspace/git-course/.git/
```

Esse comando transforma a pasta em um repositório Git local, pronto para começar a registrar as mudanças que você fizer nos arquivos localmente.

## 3.2 Resumo

- `git clone`: usado para copiar um repositório remoto já existente para o seu computador.
- `git init`: usado para transformar qualquer pasta local em um novo repositório Git.
- `.git`: pasta oculta criada automaticamente pelo Git que armazena toda a estrutura de versionamento.
  
  # 4. Gravando Mudanças no Repositório
  

## 4.1 Os Estados dos Arquivos no Git

O Git organiza os arquivos do seu projeto em diferentes **estados**, que representam o que está acontecendo com eles no ciclo de versionamento. Entender esses estados é importante para saber **quando o arquivo está pronto para ser salvo no histórico**, quando ele ainda está sendo alterado, ou quando ele nem começou a ser acompanhado pelo Git ainda.

### Visão geral dos estados

![Pasted image 20250624132056](https://github.com/user-attachments/assets/5c93bc3f-c49f-4f8e-bb5d-1353f869abdb)

### Unmodified — Arquivo monitorado e sem alterações

Esse é o estado quando o arquivo **já foi adicionado e salvo com um commit**, e **nenhuma mudança foi feita desde então**, ele está no estado chamado de **Unmodified**.

Ou seja: o Git **está monitorando** esse arquivo, mas como nada mudou nele desde o último commit, ele está "quietinho", sem pendências.

### Modified — Arquivo modificado

Assim que você faz **qualquer alteração** em um arquivo que o Git já está monitorando, ele muda de estado: **sai do Unmodified e vira Modified**.

Nesse momento, o Git sabe que **algo foi alterado**, mas ainda **não foi sinalizado se essa mudança será salva ou não**.

Pra checar isso em detalhes, usamos o comando:

```bash
git status
```

Esse comando mostra quais arquivos estão modificados, quais já foram preparados para commit, quais não estão sendo acompanhados, etc.```

### Staged — Área de preparação para o commit

Depois de modificar o arquivo, chega o momento de dizer ao Git:  
“Essa mudança aqui tá pronta para ser salva no histórico”.

Pra isso, usamos o comando:

```bash
git add app.js 
```

Agora o arquivo vai para uma **área intermediária chamada de Staged**, que é como uma fila de espera: os arquivos estão prontos para o commit, mas ainda **não foram oficialmente salvos** no repositório.

Você pode adicionar arquivos de várias formas:

```bash
git add app,js              # adiciona um arquivo específico
git add pasta/*             # adiciona todos os arquivos dentro da pasta
git add pasta/*.js          # adiciona apenas os arquivos .js de uma pasta
```

### Untracked — Arquivos novos, ainda não monitorados

Quando você **cria um novo arquivo** no projeto, o Git **não começa a monitorá-lo automaticamente**. Ele fica em um estado chamado **Untracked**.

O Git nem considera esse arquivo como modificado ou não modificado, porque ele simplesmente **ainda não sabe da existência dele** no sistema de controle de versão.

Se você quiser que esse arquivo comece a fazer parte do controle de versão, precisa adicioná-lo e salva-lo no controle de versão com `git add <>` e em seguida "commitar" as alteracoes. Assim ele entrará na área de staged pela primeira vez e depois salvar.

## 4.2 Comandos Essenciais para Gerenciar Mudanças

### git diff — Comparando mudanças feitas

Se você quiser ver **o que exatamente mudou** em um arquivo desde o último commit, pode usar:

```bash
git diff
```

Esse comando mostra linha por linha o que foi alterado em relação ao último commit.

Você também pode ver as mudanças em um arquivo específico ou em uma pasta:

```bash
git diff app.js
git diff src/
```

> ⚠️ Atenção: esse comando mostra apenas **arquivos modificados que ainda não foram adicionados a área de staged. 
> Se você já usou `git add`, o `git diff` normal **não mostrará mais nada**. Nesse caso, use:

```bash
git diff --staged
```

Assim você verá o que será salvo no próximo commi

### git rm --cached e git restore --staged — Remover da área de staged

Às vezes você manda um arquivo para a área de staged usando `git add`, mas depois percebe que **não deveria ter feito isso ainda** — por exemplo, porque era um arquivo temporário, um arquivo de configuração pessoal, ou até uma senha que foi parar lá sem querer.

Nesse caso, você pode remover o arquivo da área de staged **sem apagar o arquivo da pasta do projeto e sem apagar as mudanças feitas**, com:

```bash
git rm --cached app.js
```

Ou, de forma mais moderna, com:

```bash
git restore --staged app.js
```

O primeiro comando (rm --cached) é mais tradicional e explícito.  
O segundo (`restore --staged`) é mais intuitivo e recente, e pode até ser mais prático.

Ambos tiram o arquivo da preparação para commit e o devolvem ao estado de Modified (ou até Untracked, se ele nunca tiver sido salvo antes).

### git commit — Salvando as mudanças no histórico

Agora que você fez as alterações e mandou os arquivos certos para o staged, é hora de realmente **salvar tudo no histórico do Git**. Para isso, usamos o comando:

```bash
git commit -m "mensagem explicativa"
```

Essa mensagem deve ser curta e direta, explicando o que foi feito naquele conjunto de mudanças.

### Dica: Usando mensagens de commit padronizadas (Conventional Commits)

Quando fazemos um `git commit`, é muito importante deixar claro **o que foi feito** e **por que foi feito**. Uma prática muito usada é seguir o padrão chamado **Conventional Commits**, que deixa as mensagens mais organizadas e fáceis de entender — tanto para humanos quanto para ferramentas automatizadas.

#### Estrutura básica:

```bash
<type>(<scope>): <mensagem no imperativo>
```

- **type** → tipo da mudança (obrigatório)
- **scope** → onde foi feita a mudança (opcional)
- **mensagem** → explicação curta e direta no imperativo (ex: "adiciona botão" e não "adicionado botão")

#### Exemplos comuns de `type`:

- `feat:` nova funcionalidade
- `fix:` correção de bug
- `refactor:` melhorias no código (sem mudar a lógica)
- `style:` ajustes visuais ou de formatação (sem impactar o funcionamento)
- `test:` criação ou ajuste de testes
- `docs:` mudanças na documentação
- `chore:` tarefas de manutenção (como configs ou dependências)
- `build:` mudanças no processo de build
- `ci:` ajustes no pipeline (CI)
- `revert:` reversão de commit anterior
  
  #### Exemplo:
  

```bash
git commit -m "feat(login): adiciona validação de senha no formulário"
```

> Pense assim: “Se esse commit for aplicado, ele irá...”, por isso a mensagem deve estar sempre no imperativo (“adiciona validação”, “corrige erro”, “remove console.log” etc.)

Esse padrão ajuda a manter um histórico limpo e permite gerar changelogs automáticos, entender o que está sendo feito no projeto e até melhorar o onboarding de quem entra depois no time.

---

## 4.3 Exemplo completo de fluxo

```bash
# 1. Verificando o que foi alterado no projeto
git status

# 2. Visualizando as diferenças entre o código atual e o último commit
git diff

# 3. Adicionando arquivos modificados à área de staged
git add index.js

# 4. Verificando novamente o status (para confirmar se está no staged)
git status

# 5. Tirando da área de staged se foi adicionado por engano
git rm --cached index.js
# ou
git restore --staged index.js

# 6. Adicionando os arquivos certos
git add src/*.js

# 7. Verificando o que será incluído no próximo commit
git diff --staged

# 8. Salvando as mudanças no histórico com uma mensagem clara e padronizada
git commit -m "feat(login): adiciona validação de senha no formulário"
```

---

### Atenção com `git restore`

Se você usar o comando:

```bash
git restore app.js
```

em um arquivo **que está modificado (Modified)**, o Git vai **desfazer todas as alterações que você fez desde o último commit**, sem perguntar se você tem certeza.  
Ou seja, ele vai voltar o arquivo para o **exato estado salvo no último commit**. Então use com cuidado!

### 4.4 Consultando e Revertendo o Histórico

#### Histórico de Commits com `git log`

O comando `git log` exibe o **histórico completo de commits** realizados no repositório, incluindo:

- Nome da branch, Autor do commit, Data e hora e Hash do commit (identificador único)

Você pode utilizar variações para exibir esse histórico de forma mais compacta ou visual:

```bash
git log                         # Visualização completa
git log --oneline               
# Exibe commits em uma linha com hashes abreviados (com os primeiros 7 caracteres do hash, normalmente já é suficiente para identificar o commit e fazer as operações)
git log --oneline --graph       # Mostra a estrutura de árvore
git log --oneline --graph --all --decorate
# Mostra todas as branches, estrutura e nomes dos commits
```

#### Comandos Complementares

- `git show <hash ou HEAD>`: exibe detalhes completos de um commit específico.
- `git reflog`: mostra **todas as referências recentes**, como alterações de branch, resets, rebase etc. feitas localmente mesmo que não estejam mais no `git log`.
- `gitk`: ferramenta gráfica do Git para navegação visual do histórico.
  
  ### 4.5 Voltando a Versões Anteriores
  

Em situações em que precisamos **voltar o projeto a um estado anterior**, temos duas abordagens principais:

#### `git checkout <hash>` ou `git switch --detach <hash>`

Isso permite **navegar até um commit antigo** sem apagar o histórico — ideal para análise, testes ou criação de uma nova branch a partir de um ponto do passado.

```bash
git checkout <hash>
# ou
git switch --detach <hash>
```

> Isso coloca o repositório em modo **“detached HEAD”**, ou seja, você está em um commit específico e não em uma branch ativa.

- Nenhum dado é apagado.
- Pode-se criar uma nova branch a partir do commit:

```bash
git switch -c nova-branch
ou
git checkout -b nova-branch
```

#### `git reset` — Reescrevendo a História

O `git reset` serve para **mover o ponteiro da branch atual para um commit anterior**, podendo ou não manter as alterações feitas desde então. Há três modos principais:

```bash
git reset --soft <hash>
git reset --mixed <hash>   # padrão
git reset --hard <hash>
```

##### `--soft`: Mantém as alterações no staged

- Reposiciona o ponteiro da branch, mas **mantém as mudanças na área de staging**.
  
- Permite reescrever commits recentes mantendo o conteúdo.
  
- Útil para reorganizar commits sem perder alterações.
  
  ##### `--mixed`: Remove do staged, mantém alterações nos arquivos
  
- Reposiciona a branch e **retira as alterações da área de staging**, mas elas continuam nos arquivos.
  
- Ideal para revisar as mudanças antes de adicioná-las novamente com `git add`.
  
  ##### `--hard`: Apaga tudo após o commit
  
- Retorna ao commit indicado e **descarta completamente** todas as mudanças feitas depois dele, inclusive arquivos modificados que não foram commitados.
  
- Use com extrema cautela — alterações não salvas serão perdidas.
  

> ⚠️ Essa ação é **irreversível** a menos que você consiga recuperar via `git reflog`.

# 5. Interagindo com Repositório Remoto GitHub

No nosso projeto, se você seguiu o curso até aqui e **não começou a partir de um repositório remoto**, deve ter notado que **ainda não fizemos nada relacionado ao GitHub**. E isso é totalmente normal.

O Git pode ser usado **completamente de forma local**, sem nenhum problema. Podemos versionar, voltar no tempo, criar branches e trabalhar normalmente. Porém, à medida que avançamos no curso — e principalmente quando começarmos a trabalhar com branches —, é interessante que você **já esteja familiarizado com a integração entre repositórios locais e remotos**, como os que usamos no GitHub.

## 5.1 Configurando a Origem Remota

O que precisamos fazer agora:

1. Acesse o GitHub ([https://github.com/](https://github.com/)) no seu navegador.
2. Crie um **novo repositório vazio** (sem README, `.gitignore` ou licença).
3. Esse repositório será a **origem remota** do nosso projeto.

## Verificando se há repositório remoto

No terminal (inclusive no VSCode), você pode verificar se o repositório está conectado a alguma origem com:

```bash
git remote -v
```

Se não retornar nada, é porque **ainda não há origem configurada**.

## Adicionando a origem remota

Com o repositório do GitHub já criado, copie o link e execute:

```bash
git remote add origin <URL>
```

> Aqui, `origin` é um nome padrão para a origem remota principal do seu projeto.

Se quiser confirmar que deu certo:

```bash
git remote -v
```

## Ajustando o nome da branch (se necessário)

Algumas versões antigas do Git ainda criam a branch principal com o nome `master` por padrão. Para garantir que estamos usando `main` como branch padrão, execute:

```bash
git branch -M main
```

## Enviando o código local para o GitHub

Agora que tudo está conectado, envie os commits locais para o repositório remoto com:

```bash
git push -u origin main
```

O `-u` define um vínculo entre a branch local `main` e a remota `main`, facilitando futuros `git push` e `git pull` (sem precisar especificar `origin` e o nome da branch).

## 5.2 Sincronizando com o Repositório Remoto

Uma coisa recorrente a ser feita é **atualizar os arquivos locais em relação aos arquivos remotos**. Isso acontece quando outras pessoas fazem alterações no projeto, ou quando você mesmo trabalha em máquinas diferentes, ou até quando faz alterações diretamente pelo GitHub.

## git fetch — Buscando mudanças sem aplicar

O comando `git fetch` serve para **trazer as mudanças do repositório remoto sem dar merge automaticamente**. É como se você estivesse "checando o que tem de novo" sem alterar nada no seu código local ainda:

```bash
git fetch
```

Após um `git fetch`, você pode usar o `git diff` para verificar o que será alterado. Mas agora o `git diff` não irá comparar o que foi alterado localmente, mas sim comparar sua branch local com a origem remota. Para isso, passamos o parâmetro dessa origin:

```bash
git diff origin/main
```

Isso mostra exatamente **quais linhas serão alteradas** se você fizer o merge das mudanças remotas.

## git pull — Buscando e aplicando mudanças automaticamente

O `git pull` é mais direto: ele **busca as mudanças do repositório remoto e dá merge automaticamente** nos arquivos locais:

```bash
git pull
```

Na prática, o `git pull` é como se você executasse `git fetch` seguido de `git merge origin/main` de uma vez só. É mais prático para o dia a dia, mas às vezes é interessante usar o `git fetch` primeiro para revisar o que vai ser alterado antes de aplicar as mudanças.

# 6. Trabalhando com Branches

No Git, **branches** são como ramificações do código que podem ser criadas e desenvolvidas em paralelo ao desenvolvimento principal. Isso é extremamente útil para testar uma nova funcionalidade, corrigir bugs ou editar partes do sistema sem comprometer o funcionamento da branch principal. Essas ramificações podem ser unidas depois, o que chamamos de **merge**.

![Pasted image 20250624151800](https://github.com/user-attachments/assets/e6ba3dd2-413c-4fad-aa42-0cd8e2b34e68)

## 6.1 Criando e Navegando entre Branches

## Criando uma nova branch

Para criar uma nova branch, usamos o comando:

```bash
git branch nomedanovabranch
```

Depois disso, podemos visualizar se ela foi criada com:

```bash
git branch
```

## Trocando de branch

Após a criação, podemos trocar para ela com o comando:

```bash
git checkout nomedanovabranch
# Ou usando o comando mais moderno:
git switch nomedanovabranch
```

## Criando e trocando ao mesmo tempo

Uma alternativa mais prática é **já criar e trocar ao mesmo tempo**:

```bash
git checkout -b nomedanovabranch
# Ou usando o comando mais moderno:
git switch -c nomedanovabranch
```

A partir disso, você está naquela branch nova e **tudo o que fizer, como criação de arquivos, alterações e commits, ficará isolado nela**. Isso significa que você pode experimentar à vontade sem medo de quebrar o código da branch principal.

## 6.2 Desenvolvendo em Branches Paralelas - Salvando e Enviando Mudanças

Nesse ponto, podemos fazer o versionamento normalmente, inclusive com múltiplos commits locais. Cada branch mantém seu próprio histórico de commits, permitindo que diferentes funcionalidades sejam desenvolvidas simultaneamente sem interferência.

A qualquer momento, podemos **enviar essa branch para o repositório remoto**. Para isso, usamos os comandos normais de versionamento:

```
git add . 
git commit -m "feat: implementa nova funcionalidade"
```

Depois de fazer os commits localmente, usamos o comando `git push` para enviá-los ao GitHub. No entanto, se a branch ainda **não existir no repositório remoto**, será necessário **publicá-la** explicitamente com:

```bash
git push -u origin nomedabranch
```

Esse comando não apenas cria a branch no repositório remoto, mas também envia todos os commits feitos até então. Isso é um ponto de atenção importante: ao trabalhar com Git e branches, é essencial evitar acumular muitos commits locais sem fazer `push`, pois isso pode resultar em Pull Requests (PRs) muito grandes, difíceis de revisar e de rastrear.

Por isso, além de fazer **commits pequenos e frequentes durante o desenvolvimento**, também é recomendado enviar essas alterações regularmente para o repositório remoto com `git push`. Esse hábito contribui para um histórico mais limpo, facilita a colaboração com o time e ajuda a prevenir conflitos mais difíceis de resolver no futuro.

## Colaboração em equipe com branches

Essas branches podem então ser **acessadas por outros membros da equipe no GitHub**. Eles podem usar `git fetch` para atualizar o repositório local com base na origem, e até navegar entre branches remotas com:

```bash
git checkout nomedabranch
# Ou
git switch nomedabranch
```

## 6.3 Unindo Branches com Merge

Agora que temos branches separadas, é natural que elas precisem **se juntar em algum momento à branch de desenvolvimento ou branch que estavamos trabalhando e separamos para resolver algum bug, editar algo ou afim. Isso é feito usando o comando `git merge`.

## Processo de merge

Primeiro, precisamos estar na branch onde queremos juntar tudo:

```bash
git checkout nomedabranch
```

E depois usar:

```bash
git merge nomedabranch
```

Se não houver conflitos, o merge será feito automaticamente e um novo commit de merge será criado, unindo o histórico de commits das duas branches.

## Conflitos de merge

Mas às vezes acontece das duas branches terem alterado **o mesmo trecho de código**, e aí temos o que chamamos de **conflito de merge**. Quando isso acontece, o Git pausa o merge e marca no código os trechos conflitantes.

Veja o exemplo abaixo de um código com conflito:

```js
var idade = 20;

function validarEntradaNoEvento() {
<<<<<<< HEAD
  if (idade <= 18) {
    console.log("Nao pode entrar no evento");
  } else {
    console.log("Pode entrar no evento");
  }
=======
  idade >= 18 ? console.log("Pode entrar no evento") : console.log("Nao pode entrar no evento");
>>>>>>> test
}
```

O Git mostra as duas versões do mesmo trecho:

- A versão atual (entre `<<<<<<< HEAD` e `=======`)
- A versão da branch que está sendo mesclada (entre `=======` e `>>>>>>> test`)

Cabe a você **escolher qual trecho manter ou mesclar os dois manualmente**. Depois que resolver, basta dar:

```bash
git add nomedoarquivo 
git commit
```

Para finalizar o merge. O Git automaticamente criará uma mensagem de commit indicando que foi resolvido um conflito de merge.

## 6.4 Fluxo Completo de Trabalho com Branches

![Pasted image 20250624161430](https://github.com/user-attachments/assets/b3704eff-b8f3-49b7-b38b-58b03f9abc90)

Um fluxo típico de trabalho com branches seria:

```bash
# 1. Atualizar a branch principal
git checkout main
git pull

# 2. Criar uma nova branch para a funcionalidade
git switch -c feature/nova-funcionalidade

# 3. Desenvolver e fazer commits
git add .
git commit -m "feat: adiciona nova funcionalidade"

# 4. Enviar a branch para o remoto
git push -u origin feature/nova-funcionalidade

# 5. [IMPORTANTE] Abertura de Pull Request no GitHub
# Aqui você vai até o GitHub, abre um PR de 'feature/nova-funcionalidade' → 'main'
# e aguarda aprovação, revisão ou execução de testes automáticos

# 6. Após o merge via Pull Request, atualizar sua branch local
git checkout main
git pull

# 7. Opcional: deletar a branch local após o merge
git branch -d feature/nova-funcionalidade
```

Fluxo 2:

```bash
# 1. Começamos na branch de funcionalidade principal
git checkout feature/login

# 2. Durante o desenvolvimento, detectamos um bug e decidimos corrigir ele isoladamente
git switch -c fix/bug-login

# 3. Corrigimos o bug, salvamos as mudanças e fazemos commit
git add .
git commit -m "fix(login): corrige bug na verificação de senha nula"

# 4. Testamos localmente, validamos a correção

# 5. Voltamos para a branch principal de funcionalidade
git checkout feature/login

# 6. Fazemos o merge da correção na nossa branch principal de funcionalidade
git merge fix/bug-login

# 7. Continuamos com o desenvolvimento ou enviamos a branch com o bug resolvido para revisão
git push  # ou git push -u origin feature/login se for o primeiro push

# 8. (Opcional) Após o merge, deletamos a branch de correção se ela não for mais necessária
git branch -d fix/bug-login
```
