[DESCOMPLICANDO O DOCKER](https://www.youtube.com/watch?v=0xxHiOSJVe8&list=PLf-O3X2-mxDkiUH0r_BadgtELJ_qyrFJ_)(LinuxTips)
---





* docker run PARAMETROS IMAGEM COMANDO

imagem:
  
Uma imagem local, caso não tenha a imagem local. Será feito o download  

parametros: 

   * **-t**: terminal
     Conecta em um terminal no container 
   * **-i**: interativo
     Modo interativo

Exemplo:

```bash

docker run -it ubuntu /bin/bash

```

Para sair de um container **ctrl +d** . O container será encerrado 

Para sair de um container sem encerrá-lo **ctrl +p +q**

* Vizualizar containeres parados


```bash
docker ps -a

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                         PORTS               NAMES
36eae871c067        ubuntu              "/bin/bash"         26 seconds ago      Exited (0) 12 seconds ago                          unruffled_dijkstra
6fe711691772        ubuntu              "/bin/bash"         39 seconds ago      Up 37 seconds                                      silly_bardeen
f96324d24209        ubuntu              "/bin/bash"         4 minutes ago       Exited (0) 4 minutes ago                           keen_beaver
21842bd1fb0e        ubuntu              "/bin/bash"         31 minutes ago      Created                                            quizzical_pike
f34ff4a581d1        centos:7            "/bin/bash"         39 minutes ago      Exited (0) 31 minutes ago                          agitated_pasteur
f8a176c9d761        ubuntu              "/bin/bash"         42 minutes ago      Exited (130) 41 minutes ago                        serene_banach
619fcf1fbf6c        hello-world         "/hello"            About an hour ago   Exited (0) About an hour ago                       sad_mcclintock



```

* Visualizar containeres em execução


```bash
docker ps

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
6fe711691772        ubuntu              "/bin/bash"         12 minutes ago      Up 12 minutes                           silly_bardeen

```

* Voltar para o shell de um containeres no modo interativo

   * docker attach CONTAINER ID
     
     CONTAINER ID: 

      *Para descobrir o código do container rode **docker ps** 


```bash
docker attach f34ff4a581d1

[root@f34ff4a581d1 /]#
```

* Para parar um container

docker stop CONTAINER ID

```bash
docker stop f34ff4a581d1

docker ps -a

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS 
f34ff4a581d1        centos:7            "/bin/bash"         About an hour ago   Exited (137) 13 seconds ago                                                    

PORTS               NAMES
                    agitated_pasteur
```

* Para inicalizar um container

docker start CONTAINER ID

```bash
docker start f34ff4a581d1

docker ps

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
f34ff4a581d1        centos:7            "/bin/bash"         About an hour ago   Up 6 seconds                            agitated_pasteur

```

* Para pausar um container

docker pause CONTAINER ID

```bash
docker pause f34ff4a581d1

docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                           PORTS               NAMES

docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                           PORTS               NAMES
f34ff4a581d1        centos:7            "/bin/bash"         About an hour ago   Up 2 minutes (Paused)                                agitated_pasteur
```

* Para parar um container

docker upause CONTAINER ID

```bash
docker upause f34ff4a581d1

docker ps

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
f34ff4a581d1        centos:7            "/bin/bash"         About an hour ago   Up 6 minutes                            agitated_pasteur

```

* Para destruir um container

docker rm CONTAINER ID

   * **-f**: Força de destruição de um container em execução

```bash
docker rm f34ff4a581d1

docker ps 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES


docker ps -a

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                           PORTS               NAMES
36eae871c067        ubuntu              "/bin/bash"         About an hour ago   Exited (0) About an hour ago                         unruffled_dijkstra
f96324d24209        ubuntu              "/bin/bash"         About an hour ago   Exited (0) About an hour ago                         keen_beaver
21842bd1fb0e        ubuntu              "/bin/bash"         About an hour ago   Created                                              quizzical_pike
f8a176c9d761        ubuntu              "/bin/bash"         About an hour ago   Exited (130) About an hour ago                       serene_banach
619fcf1fbf6c        hello-world         "/hello"            2 hours ago         Exited (0) 2 hours ago                               sad_mcclintock
```
   * o container some da lista


* Visualizar recursos consumidos pelo container

docker stats CONTAINER ID

```bash
docker stats 36eae871c067

CONTAINER           CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
36eae871c067        0.00%               568KiB / 15.58GiB   0.00%               5.13kB / 90B        0B / 0B             1
```

* Visualizar processos do container

docker top CONTAINER ID

```bash
docker top fec534563d74

UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                18145               18127               0                   23:03               pts/0               00:00:00            /bin/bash
root                18285               18145               0                   23:04               pts/0               00:00:00            sleep 900
```

* Inspecionar comando realizados no container

```bash
docker logs fec534563d74
root@fec534563d74:/# sleep 900
```