Subject 6: Dockerfile 기반 웹 서버 및 볼륨 실습
-----

> 웹 서버 소스코드 제작
```bash
kinch06120270@c4r6s3 week1 % mkdir app

kinch06120270@c4r6s3 week1 % cd app

kinch06120270@c4r6s3 app % echo "<h1>Hello from Docker Python Server!</h1>" > index.html 
zsh: event not found: </h1>

kinch06120270@c4r6s3 app % echo '<h1>Hello from Docker Python Server!</h1>' > index.html

kinch06120270@c4r6s3 app % cat index.html
<h1>Hello from Docker Python Server!</h1>

kinch06120270@c4r6s3 app % 
```

> Dockerfile 작성
```bash
kinch06120270@c4r6s3 week1 % vi df/Dockerfile 

kinch06120270@c4r6s3 week1 % cat df/Dockerfile 
FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    apt-get clean

WORKDIR /app
COPY ./app /app

CMD ["python3", "-m", "http.server", "8000"]

kinch06120270@c4r6s3 week1 % 
```

> 이미지 빌드
```bash
kinch06120270@c4r6s3 df % ls -alh
total 8
drwxr-xr-x  4 kinch06120270  kinch06120270   128B Mar 31 10:55 .
drwxr-xr-x  8 kinch06120270  kinch06120270   256B Mar 31 10:55 ..
drwxr-xr-x  3 kinch06120270  kinch06120270    96B Mar 31 10:52 app
-rw-r--r--  1 kinch06120270  kinch06120270   221B Mar 31 10:53 Dockerfile

kinch06120270@c4r6s3 df % docker build -t my_web_server .
[+] Building 1.0s (9/9) FINISHED                                                                                                                                     docker:orbstack
 => [internal] load build definition from Dockerfile                                                                                                                            0.1s
 => => transferring dockerfile: 260B                                                                                                                                            0.0s
 => [internal] load metadata for docker.io/library/ubuntu:24.04                                                                                                                 0.0s
 => [internal] load .dockerignore                                                                                                                                               0.1s
 => => transferring context: 2B                                                                                                                                                 0.0s
 => [1/4] FROM docker.io/library/ubuntu:24.04                                                                                                                                   0.0s
 => [internal] load build context                                                                                                                                               0.1s
 => => transferring context: 110B                                                                                                                                               0.0s
 => CACHED [2/4] RUN apt-get update &&     apt-get install -y python3 python3-pip &&     apt-get clean                                                                          0.0s
 => CACHED [3/4] WORKDIR /app                                                                                                                                                   0.0s
 => [4/4] COPY ./app /app                                                                                                                                                       0.2s
 => exporting to image                                                                                                                                                          0.2s
 => => exporting layers                                                                                                                                                         0.2s
 => => writing image sha256:a01b1a8b1c8cc66e4849990cede10b49577c87341409f66dd3524a3886bff0e3                                                                                    0.0s
 => => naming to docker.io/library/my_web_server                                                                                                                                0.0s

kinch06120270@c4r6s3 week1 % docker images
REPOSITORY       TAG       IMAGE ID       CREATED              SIZE
my_web_server    latest    a01b1a8b1c8c   About a minute ago   559MB
my_first_image   latest    6e3d3831dcf5   20 minutes ago       559MB
hello-world      latest    e2ac70e7319a   7 days ago           10.1kB
ubuntu           24.04     f794f40ddfff   5 weeks ago          78.1MB

kinch06120270@c4r6s3 week1 %
```

> 컨테이너 실행 후 웹 서버 접속
```bash
kinch06120270@c4r6s3 week1 % docker run -d -p 8080:8000 --name my_web_con my_web_server
538cfa625c10345c0fbb680bf70ebfcbd30135681c55d755b974d0aa9c78fdb2

kinch06120270@c4r6s3 week1 % docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED             STATUS                      PORTS                                         NAMES
538cfa625c10   my_web_server    "python3 -m http.ser…"   9 seconds ago       Up 8 seconds                0.0.0.0:8080->8000/tcp, [::]:8080->8000/tcp   my_web_con
a0a0730563bb   my_first_image   "python3 --version"      19 minutes ago      Exited (0) 19 minutes ago                                                 my_first_container
6ccc7c37ec02   f794f40ddfff     "/bin/bash"              57 minutes ago      Exited (0) 56 minutes ago                                                 my-ubuntu
ac9e5a421033   f794f40ddfff     "--name ubuntu /bin/…"   57 minutes ago      Created                                                                   strange_wu
63a802d42583   f794f40ddfff     "/bin/bash"              About an hour ago   Up About an hour                                                          ubuntu-lab

kinch06120270@c4r6s3 week1 % curl http://localhost:8080
<h1>Hello from Docker Python Server!</h1>

kinch06120270@c4r6s3 week1 % 
```

> 호스트 경로를 컨테이너에 바인드
```bash
kinch06120270@c4r6s3 df % ls -alh
total 8
drwxr-xr-x  4 kinch06120270  kinch06120270   128B Mar 31 10:55 .
drwxr-xr-x  8 kinch06120270  kinch06120270   256B Mar 31 10:55 ..
drwxr-xr-x  3 kinch06120270  kinch06120270    96B Mar 31 10:52 app
-rw-r--r--  1 kinch06120270  kinch06120270   221B Mar 31 10:53 Dockerfile

kinch06120270@c4r6s3 df % docker run -d -p 8080:8000 -v $(pwd)/app:/app --name bind_con my_web_server
1f7da1176fefdde002b30c23624e3e89704a9f965996ea973e34d4601040bc8c

kinch06120270@c4r6s3 df % curl localhost:8080
<h1>Hello from Docker Python Server!</h1>

kinch06120270@c4r6s3 df % echo '<h1>Modified by Bind Mount!</h1>' > app/index.html

kinch06120270@c4r6s3 df % curl localhost:8080                                     
<h1>Modified by Bind Mount!</h1>

kinch06120270@c4r6s3 df %
```

> 도커 볼륨 생성
```bash
kinch06120270@c4r6s3 week1 % docker volume create my_data_vol
my_data_vol

kinch06120270@c4r6s3 week1 % docker volume ls
DRIVER    VOLUME NAME
local     my_data_vol

kinch06120270@c4r6s3 week1 % 
```

> 컨테이너에 볼륨 연결하고 파일 생성
```bash
kinch06120270@c4r6s3 week1 % docker run -d --name vol_con -v my_data_vol:/data my_web_server
461b37a096eaed9623ea3bed21e028bd65393fa1e11157292413e79ca0b29640

kinch06120270@c4r6s3 week1 % docker exec vol_con touch /data/test_file.txt

kinch06120270@c4r6s3 week1 % docker exec vol_con ls /data
test_file.txt

kinch06120270@c4r6s3 week1 % 
```

> 연결했던 컨테이너를 삭제하고 다시 생성해서 파일이 존재하는지 확인
```bash
kinch06120270@c4r6s3 week1 % docker rm -f vol_con
vol_con

kinch06120270@c4r6s3 week1 % docker run -it --rm -v my_data_vol:/data ubuntu:24.04 ls /data
test_file.txt

kinch06120270@c4r6s3 week1 % 
```