## Como inicializar o git-flow
O git-flow é uma ferramenta que ajuda a executar os fluxos de git com menos comandos e mais facilidade, bom pra iniciantes. 

O primeiro passo para utliza-lo é inicializar na pasta raiz do repositório.
```bash
cd ./pasta-raiz-do-projeto
git flow init
# basta dar enter em tudo que perguntar após esse comando
```

## Como criar branch feature, commitar e subir pra branch develop
Depois de editar o projeto, queremos subir nossas alterações codigo pro repositório.

Siga os passos abaixo para criar uma feature e commitar suas alterações.

```bash
git flow feature start seunome/nome-da-feature 
# ex: lucas/menu-update
git status 
# verifica arquivos modificados disponiveis para commitar
git add ./arquivo # adiciona arquivo no commit (p/ add todos, 'git add *')
git status 
# confere arquivos adicionados no commit, se tiver faltando pode dar git add quantas vezes quiser
git commit -m "mensagem do commit" 
# cria commit com arquivos adicionados ex: git commit -m "modifying menu files"
git flow feature finish seunome/nome-da-feature 
# finaliza feature mergeando commits com a branch develop no seu repositorio local
git push origin develop 
# atualiza a branch develop do repositorio remoto, a partir da develop local

# Basta repetir esse processo cada vez que quiser subir alterações para o repositório
```

obs: caso queira subir a branch da feature que você está fazendo antes de finalizar e mergear com a branch develop, (pode ser util pra mostrar um erro a algum colega), basta dar um:

```bash
git push origin feature/seunome/nomedafeature
```
e a branch vai estar disponivel no repositorio