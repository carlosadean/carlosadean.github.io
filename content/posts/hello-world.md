+++
title = 'Hello World'
date = 2024-03-30T17:09:00-03:00
draft = true
type = "post"
+++

# My first post

Sequencia para fazer um post com hugo

1. abrir o power shell e entrar no diretório carlosadean.github.io
2. abrir a pasta carlosadean.github.io com o vscode 
3. criar um novo post com `hugo new content posts/meu-novo-post.md`
4. depois de editar o post, faça os ajustes no cabeçalho:
   1. alterar a opção draft = false, do contrário o post não será exibido
5. gere o site estático com o comando abaixo:
   1. `hugo --minify --destination docs`
6. verifique se o site está funcionando com o servidor local
   1. `hugo serve -D`
   2. É **serve** mesmo não é **server**!
7. por fim faça `git add .` e `git push origin main`
   1. tanto faz fazer pelo power shell ou direto pelo vscode
8. existe um pipeline no github action que reconstrói o site automaticamente após um push no `branch main`.
