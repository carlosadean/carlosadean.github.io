+++
title = 'Como Usar O Tmux'
date = 2024-04-08T11:21:27-03:00
draft = false
#type = "post"
tags = ["shell", "tmux"]
categories = ["linux", "tmux"]
slug = "como-usar-o-tmux"
+++


Criar uma sessão com nome aleatório
```shell
tmux
```

Criar uma nova sessão nomeada
```shell
tmux new -s <nome da sessão>
```

Desconectar de uma sessão use `CTRL+B` ou o comando 
```shell
tmux detach
```

Para listar sessões
```shell
tmux ls
```

Reconectar a uma sessão existente
```shell
tmux attach -t <id or name>     
```

Dividir a tela na horizontal `CTRL+B` seguido de " (aspas duplas, isso mesmo!)

Dividir a tela na vertical `CTRL+B` seguido de %

Executar comandos em todos os painéis ao mesmo tempo, para desativar use no no final
```
CTRL+B seguido de : então digitar setw synchronize-panes [no]
```