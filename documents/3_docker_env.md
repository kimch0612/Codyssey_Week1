Subject 3: 도커 환경 점검
----

> 도커 버전 확인
```bash
kinch06120270@c4r6s3 week1 % docker --version
Docker version 28.5.2, build ecc6942

kinch06120270@c4r6s3 week1 % 
```

> 도커 데몬 동작 확인
```bash
kinch06120270@c4r6s3 week1 % docker info
Client:
 Version:    28.5.2
 Context:    orbstack
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.29.1
    Path:     /Users/kinch06120270/.docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.40.3
    Path:     /Users/kinch06120270/.docker/cli-plugins/docker-compose

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 28.5.2
 Storage Driver: overlay2
  Backing Filesystem: btrfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 1c4457e00facac03ce1d75f7b6777a7a851e5c41
 runc version: d842d7719497cc3b774fd71620278ac9e17710e0
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.17.8-orbstack-00308-g8f9c941121b1
 Operating System: OrbStack
 OSType: linux
 Architecture: x86_64
 CPUs: 6
 Total Memory: 15.67GiB
 Name: orbstack
 ID: fd364e82-189b-454a-a74a-56a4f7ec0ac9
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  ::1/128
  127.0.0.0/8
 Live Restore Enabled: false
 Product License: Community Engine
 Default Address Pools:
   Base: 192.168.97.0/24, Size: 24
   Base: 192.168.107.0/24, Size: 24
   Base: 192.168.117.0/24, Size: 24
   Base: 192.168.147.0/24, Size: 24
   Base: 192.168.148.0/24, Size: 24
   Base: 192.168.155.0/24, Size: 24
   Base: 192.168.156.0/24, Size: 24
   Base: 192.168.158.0/24, Size: 24
   Base: 192.168.163.0/24, Size: 24
   Base: 192.168.164.0/24, Size: 24
   Base: 192.168.165.0/24, Size: 24
   Base: 192.168.166.0/24, Size: 24
   Base: 192.168.167.0/24, Size: 24
   Base: 192.168.171.0/24, Size: 24
   Base: 192.168.172.0/24, Size: 24
   Base: 192.168.181.0/24, Size: 24
   Base: 192.168.183.0/24, Size: 24
   Base: 192.168.186.0/24, Size: 24
   Base: 192.168.207.0/24, Size: 24
   Base: 192.168.214.0/24, Size: 24
   Base: 192.168.215.0/24, Size: 24
   Base: 192.168.216.0/24, Size: 24
   Base: 192.168.223.0/24, Size: 24
   Base: 192.168.227.0/24, Size: 24
   Base: 192.168.228.0/24, Size: 24
   Base: 192.168.229.0/24, Size: 24
   Base: 192.168.237.0/24, Size: 24
   Base: 192.168.239.0/24, Size: 24
   Base: 192.168.242.0/24, Size: 24
   Base: 192.168.247.0/24, Size: 24
   Base: fd07:b51a:cc66:d000::/56, Size: 64

WARNING: DOCKER_INSECURE_NO_IPTABLES_RAW is set

kinch06120270@c4r6s3 week1 % 
```

> 도커 이미지 리스트 출력
```bash
kinch06120270@c4r6s3 week1 % docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
ubuntu       24.04     f794f40ddfff   5 weeks ago   78.1MB

kinch06120270@c4r6s3 week1 % 
```

> 만들어진 컨테이너 리스트 출력
```bash
kinch06120270@c4r6s3 week1 % docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

kinch06120270@c4r6s3 week1 % 
```

> 도커 컨테이너 실행
```bash
kinch06120270@c4r6s3 week1 % docker run -itd --name ubuntu-lab f794f40ddfff /bin/bash
63a802d42583360485e9ac763c47d2ac4a476f62017d18e895ae17618e1d4aa1

kinch06120270@c4r6s3 week1 % docker ps -a
CONTAINER ID   IMAGE          COMMAND       CREATED         STATUS        PORTS     NAMES
63a802d42583   f794f40ddfff   "/bin/bash"   2 seconds ago   Up 1 second             ubuntu-lab

kinch06120270@c4r6s3 week1 %
```

> 컨테이너 로그 출력
```bash
kinch06120270@c4r6s3 week1 % docker attach ubuntu-lab

root@63a802d42583:/# echo "Hello World!"
Hello World!

root@63a802d42583:/# exit
exit

kinch06120270@c4r6s3 week1 % docker logs ubuntu-lab
root@63a802d42583:/# echo "Hello World!"
Hello World!
root@63a802d42583:/# exit
exit

kinch06120270@c4r6s3 week1 % 
```

> 컨테이너 자원 사용 현황 출력
```bash
# docker stats

CONTAINER ID   NAME         CPU %     MEM USAGE / LIMIT     MEM %     NET I/O         BLOCK I/O     PIDS 
63a802d42583   ubuntu-lab   0.00%     4.172MiB / 15.67GiB   0.03%     1.13kB / 126B   4.45MB / 0B   1 
```

### 간단한 정리
- 컨테이너를 실행할 때 exec와 attach에는 다음과 같은 차이점이 존재한다
  - attach: 달리는 버스 조수석에 앉기
    - 운전사가 뭘 하는지 다 볼 수 있고, 버스의 현재 내부 상태를 실시간으로 같이 확인할 수 있음
    - 콘솔에서 exit를 입력하면 컨테이너 자체도 같이 꺼짐
  - exec: 버스에 잠시 청소부가 들어옴
    - 운전사가 뭘 하는진 관심 없고, 자기 할 일을 하고 뒷문으로 나감
    - 콘솔에서 exit를 입력해도 컨테이너가 꺼지진 않음