+++
title = 'Linux: como saber a diferença entre um crash e um desligamento controlado?'
date = 2016-11-15T11:52:10-03:00
draft = false
tags = ["shutdown", "rebot", "troubleshooting"]
categories = ["linux", "servers"]
#slug = "no-matching-key-exchange-method-found"
+++

Estava diante de um problema em um ambiente e precisava de fato saber o que aconteceu, se alguém havia desligado corretamente os servidores ou se um desligamento abrupto ocorrera.

Quando foi a última vez em que o sistema foi desligado corretamente? Esse comando lista as últimas é possível saber quando ocorreram os últimos. 

Faça uma inspeção com o comando `last -x`.

Com um simples comando `last -n2 -x shutdown reboot`, o arquivo de sistema `wtmp` reporta os últimos dois recentes desligamentos e reinicializações. Um `reboot` indica o sistema inicializando; enquanto que, `shutdown` denota o sistema sendo desligado. Um desligamento controlado exibiria o `reboot` precedido de um `shutdown`, como no exemplo abaixo:

```bash
[root@fox ~]# last -n2 -x shutdown reboot
reboot   system boot  3.10.0-862.11.6. Sat Sep  1 09:51 - 09:45 (124+22:54)
shutdown system down  3.10.0-693.21.1. Sat Sep  1 09:50 - 09:51  (00:00)  
```

Já no exemplo abaixo podemos entender que o servidor foi inicializado sem que houvesse um desligamento controlado antes, pois há dois reboots registrados em seguida.

```bash
lco: [root@virt01 ~]# last -n2 -x shutdown reboot
reboot   system boot  3.10.0-327.18.2. Wed Dec 26 15:20 - 11:45 (8+20:24)   
reboot   system boot  3.10.0-327.18.2. Fri Dec 14 18:46 - 11:45 (20+16:58)  

wtmp begins Mon Apr 11 23:39:49 2016
```

Expandindo para as últimas 4 entradas no mesmo exemplo acima, podemos notar que na penúltima vez em Nov 13 ocorreu o desligamento controlado (shutdown) seguido de um inicialização (reboot).

```bash
lco: [root@virt01 ~]# last -n4 -x shutdown reboot
reboot   system boot  3.10.0-327.18.2. Wed Dec 26 15:20 - 11:46 (8+20:25)   
reboot   system boot  3.10.0-327.18.2. Fri Dec 14 18:46 - 11:46 (20+16:59)  
reboot   system boot  3.10.0-327.18.2. Tue Nov 13 10:18 - 11:46 (52+01:27)  
shutdown system down  3.10.0-327.18.2. Tue Nov 13 10:16 - 10:18  (00:01)    
wtmp begins Mon Apr 11 23:39:49 2016
```

Este artigo originalmente está em inglês [aqui](https://access.redhat.com/articles/2642741) e me foi bastante útil quando precisei. 