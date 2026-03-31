Subject 5: Dockerfile 제작
----

> Dockerfile 파일 작성
```
FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    apt-get clean

CMD ["python3", "--version"]
```

> Dockerfile 빌드
```bash
kinch06120270@c4r6s3 df % docker build -t my_first_image .
[+] Building 57.1s (6/6) FINISHED                                                                                                                                    docker:orbstack
 => [internal] load build definition from Dockerfile                                                                                                                            0.2s
 => => transferring dockerfile: 214B                                                                                                                                            0.0s
 => [internal] load metadata for docker.io/library/ubuntu:24.04                                                                                                                 0.0s
 => [internal] load .dockerignore                                                                                                                                               0.2s
 => => transferring context: 2B                                                                                                                                                 0.0s
 => [1/2] FROM docker.io/library/ubuntu:24.04                                                                                                                                   0.1s
 => [2/2] RUN apt-get update &&     apt-get install -y python3 python3-pip &&     apt-get clean                                                                                54.0s
 => exporting to image                                                                                                                                                          2.3s 
 => => exporting layers                                                                                                                                                         2.2s 
 => => writing image sha256:6e3d3831dcf5b64c93a73e831f73ba09f1fd394ada6140c0d3349d73d699884a                                                                                    0.0s 
 => => naming to docker.io/library/my_first_image                                                                                                                               0.0s 

kinch06120270@c4r6s3 df % docker images
REPOSITORY       TAG       IMAGE ID       CREATED              SIZE
my_first_image   latest    6e3d3831dcf5   About a minute ago   559MB
hello-world      latest    e2ac70e7319a   7 days ago           10.1kB
ubuntu           24.04     f794f40ddfff   5 weeks ago          78.1MB

kinch06120270@c4r6s3 df % 
```

> 컨테이너 실행
```bash
kinch06120270@c4r6s3 df % docker run --name my_first_container my_first_image
Python 3.12.3

kinch06120270@c4r6s3 df % 
```