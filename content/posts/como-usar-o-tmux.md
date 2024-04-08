+++
title = 'Como Usar O Tmux'
date = 2024-04-08T11:21:27-03:00
draft = false
#type = "post"
tags = ["shell", "tmux"]
categories = ["linux", "tmux"]
slug = "como-usar-o-tmux"
+++


Cria uma sessão com nome aleatório
```
tmux
```

Para criar uma nova sessão nomeada
```
tmux new -s <nome da sessão>
```

Para desatachar de uma sessão use `CTRL+B` ou o comando 
```
tmux detach
```

Para voltar (atachar) em uma sessão
```
tmux ls                         #para listar primeiro, caso tenha várias sessões abertas
tmux attach -t <id or name>     #para atachar na sessão
```

Para dividir a tela na horizontal `CTRL+B` seguido de " (aspas duplas, isso mesmo!)

Para dividir a tela na vertical `CTRL+B` seguido de %

Executar comandos em todos os painéis ao mesmo tempo, para desativar use no no final
```
CTRL+B seguido de : então digitar setw synchronize-panes [no]
```