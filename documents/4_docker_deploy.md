Subject 4: 도커 컨테이너 실행
----

> hello-world container 실행
```bash
kinch06120270@c4r6s3 week1 % docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
Digest: sha256:452a468a4bf985040037cb6d5392410206e47db9bf5b7278d281f94d1c2d0931
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/


kinch06120270@c4r6s3 week1 % 
```

> Ubuntu 컨테이너를 실행
```bash
kinch06120270@c4r6s3 week1 % docker run -it --name my-ubuntu f794f40ddfff /bin/bash

root@6ccc7c37ec02:/# docker ps -a
bash: docker: command not found

root@6ccc7c37ec02:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

root@6ccc7c37ec02:/# echo "HIHIHIHIHI"
HIHIHIHIHI

root@6ccc7c37ec02:/#
```