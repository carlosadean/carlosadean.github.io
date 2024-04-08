+++
title = 'Remover a primeira linha de arquivos com tail'
date = 2019-04-01T18:36:14-03:00
draft = false
#type = "post"
tags = ["shell","cli"]
categories = ["linux", "bash"]
+++

Uma maneira rápida de remover a primeira linha de arquivos texto é usando o comando `tail` e o redirecionador da saída padrão para criar um novo arquivo. Tem que usar o +2.

```console
cat file.csv
id,ra,dec
228856653,23.00001,-48.250037
228250285,23.000014,-50.699538
228236797,23.000019,-50.455765
228038470,23.000034,-50.068905
228232771,23.000049,-50.389778
```

```console
tail -n +2 file.csv
228856653,23.00001,-48.250037
228250285,23.000014,-50.699538
228236797,23.000019,-50.455765
228038470,23.000034,-50.068905
228232771,23.000049,-50.389778
```