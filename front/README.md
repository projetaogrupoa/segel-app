# src

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

## Front - ReadMe

## Build Setup

```bash
#It's essential to use the following versions for correct running:

# Node Version 16.13.2

# Vue Version 2.7.10

# Nuxt Version 2.15.8

# Vuetify Version 2.6.10

# install dependencies
$ yarn install

# generate static project
$ yarn generate

# serve with hot reload at localhost:3000
$ yarn dev


```

For detailed explanation on how things work, check out the [documentation](https://nuxtjs.org).

## Special Directories

You can create the following extra directories, some of which have special behaviors. Only `pages` is required; you can delete them if you don't want to use their functionality.

### `assets`

The assets directory contains your uncompiled assets such as Stylus or Sass files, images, or fonts.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/assets).

### `components`

The components directory contains your Vue.js components. Components make up the different parts of your page and can be reused and imported into your pages, layouts and even other components.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/components).

### `layouts`

Layouts are a great help when you want to change the look and feel of your Nuxt app, whether you want to include a sidebar or have distinct layouts for mobile and desktop.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/layouts).


### `pages`

This directory contains your application views and routes. Nuxt will read all the `*.vue` files inside this directory and setup Vue Router automatically.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/get-started/routing).

### `plugins`

The plugins directory contains JavaScript plugins that you want to run before instantiating the root Vue.js Application. This is the place to add Vue plugins and to inject functions or constants. Every time you need to use `Vue.use()`, you should create a file in `plugins/` and add its path to plugins in `nuxt.config.js`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/plugins).

### `static`

This directory contains your static files. Each file inside this directory is mapped to `/`.

Example: `/static/robots.txt` is mapped as `/robots.txt`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/static).

### `store`

This directory contains your Vuex store files. Creating a file in this directory automatically activates Vuex.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/store).
