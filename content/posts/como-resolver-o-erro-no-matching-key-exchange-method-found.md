+++
title = 'Como resolver o erro No matching key exchange method found'
date = 2024-08-20T17:45:25-03:00
draft = true
tags = ["rocky9", "ssh", "openssl"]
categories = ["linux", "ssh"]
slug = "no-matching-key-exchange-method-found"
+++

Ao utilizar um cliente SSH mais atual (Rocky Linux 9), alguns equipamentos e sistemas passaram a apresentar uma mensagem de erro indicando problemas no reconhecimento da chave dos servidores SSH.

```bash
ssh -l user 10.10.0.1
Unable to negotiate with 10.10.0.1 port 22: no matching key exchange method found. Their offer: diffie-hellman-group1-sha1
``` 

A mesma mensagem pode aparecer em outros casos tais como `ssh-rsa`, `ecdsa-sha2-nistp256`, etc.

Uma forma de contornar isso é adicionar as diretivas `KexAlgoritms` e `HostKeyAlgorithms` explicitamente no arquivo `~/.ssh/config` para forçar o cliente a utilizar o tipo método correspondente.

```bash
$ cat ~/.ssh/config
Host *
  KexAlgorithms +diffie-hellman-group1-sha1
  HostKeyAlgorithms +ssh-rsa,ecdsa-sha2-nistp256
  PubkeyAcceptedKeyTypes +ssh-rsa
  Ciphers +aes128-cbc,3des-cbc,aes192-cbc,aes256-cbc
```

Este workaround NÃO corrige o problema, ou seja, o sistema remoto pode continuar precisando de atualizações, mas habilita o acesso para que seja possível aplicar as devidas correções.
