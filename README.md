# Week 1: AI/SW 개발 워크스테이션 구축

## 1. 프로젝트 개요

터미널, Docker, Git/GitHub를 직접 다루며 로컬 개발 환경을 구성하고, 재현 가능한 실행 환경을 만드는 것이 목표이다.

이 문서에서는 아래 항목을 중심으로 수행 내용을 정리했다.

- 터미널 기본 조작과 파일/디렉토리 관리
- 파일 및 디렉토리 권한 확인과 변경
- Docker 설치 상태 점검과 기본 운영 명령 실습
- `hello-world`, `ubuntu` 컨테이너 실행
- Dockerfile 기반 커스텀 이미지 제작
- 포트 매핑, 바인드 마운트, 볼륨 영속성 검증
- Git 설정과 GitHub 연동
- 트러블슈팅 기록

## 2. 실행 환경

- OS: macOS 15.7.4
- Shell: zsh
- Docker: 28.5.2
- Git: 2.53.0
- Python: 3.12.13

## 3. 수행 항목 체크리스트

- [x] 터미널 기본 조작 기록
- [x] 파일/디렉토리 권한 변경 실습
- [x] Docker 설치 및 데몬 동작 점검
- [x] `hello-world` 실행
- [x] `ubuntu` 컨테이너 실행 및 내부 명령 확인
- [x] Docker 기본 운영 명령 실행 기록
- [x] Dockerfile 기반 커스텀 이미지 빌드
- [x] 포트 매핑 후 접속 확인
- [x] 바인드 마운트 반영 확인
- [x] Docker 볼륨 영속성 확인
- [x] Git 설정 및 GitHub 연동 기록

## 4. 검증 방법과 결과 위치

### 터미널 조작

- 현재 위치 확인: `pwd`
- 숨김 파일 포함 목록 확인: `ls -alh`
- 파일 생성/복사/이동/이름 변경/삭제: `touch`, `cp`, `mv`, `rm`
- 파일 내용 확인: `cat`
- 폴더 이동: `cd`
- 결과 문서: [documents/1_terminal.md](./documents/1_terminal.md)

### 권한 실습

- 권한 확인: `ls -alh`
- 파일 권한 변경: `chmod 600 TEST.txt`
- 디렉토리 권한 변경: `chmod 777 testfolder`
- 결과 문서: [documents/2_permission.md](./documents/2_permission.md)

### Docker 환경 점검 및 기본 운영

- 버전 확인: `docker --version`
- 데몬 확인: `docker info`
- 이미지 목록: `docker images`
- 컨테이너 목록: `docker ps -a`
- 로그 확인: `docker logs`
- 리소스 확인: `docker stats`
- 결과 문서: [documents/3_docker_env.md](./documents/3_docker_env.md)

### 컨테이너 실행 실습

- `hello-world` 실행: `docker run hello-world`
- `ubuntu` 실행 및 내부 명령 확인: `docker run -it --name my-ubuntu ...`
- 결과 문서: [documents/4_docker_deploy.md](./documents/4_docker_deploy.md)

### Dockerfile 기반 이미지와 웹 서버

- 이미지 빌드: `docker build -t my_first_image .`
- 웹 서버 이미지 빌드: `docker build -t my_web_server .`
- 포트 매핑 실행: `docker run -d -p 8080:8000 --name my_web_con my_web_server`
- 접속 확인: `curl http://localhost:8080`
- 브라우저 접속 증거: `images/website.png`
- 결과 문서: [documents/5_dockerfile.md](./documents/5_dockerfile.md), [documents/6_dockerfile_extra.md](./documents/6_dockerfile_extra.md)

### 바인드 마운트와 볼륨 영속성

- 바인드 마운트: `docker run -d -p 8080:8000 -v $(pwd)/app:/app --name bind_con my_web_server`
- 볼륨 생성: `docker volume create my_data_vol`
- 볼륨 연결 및 검증: `docker run -d --name vol_con -v my_data_vol:/data my_web_server`
- 결과 문서: [documents/6_dockerfile_extra.md](./documents/6_dockerfile_extra.md)

### Git / GitHub

- Git 설정 확인: `git config --list`
- 기본 브랜치 설정: `git config --global init.defaultBranch master`
- 기본 브랜치 확인: `git config --list | grep init.defaultbranch`
- VSCode 연동 증거: `images/vscode_github.png`
- GitHub SSH 인증 확인: `ssh -T git@github.com`
- 커밋 및 푸시: `git add .`, `git commit`, `git push`
- 결과 문서: [documents/7_git.md](./documents/7_git.md)

## 5. 문서 목차

- [터미널 실습](./documents/1_terminal.md)
- [퍼미션 실습](./documents/2_permission.md)
- [도커 환경 점검](./documents/3_docker_env.md)
- [도커 컨테이너 실행](./documents/4_docker_deploy.md)
- [Dockerfile 제작](./documents/5_dockerfile.md)
- [Dockerfile 기반 웹 서버 및 볼륨 실습](./documents/6_dockerfile_extra.md)
- [Git 설정 및 GitHub 연동](./documents/7_git.md)
- [트러블슈팅](./documents/0_err.md)

## 6. 트러블슈팅

- Docker 이미지 이름 대문자 사용 오류: [documents/0_err.md](./documents/0_err.md)
- zsh에서 `!` 문자 처리 오류: [documents/0_err.md](./documents/0_err.md)

## 7. 디렉토리 구조

```text
week1
|-- df
|   |-- Dockerfile
|   `-- app
|       `-- index.html
|-- documents
|   |-- 0_err.md
|   |-- 1_terminal.md
|   |-- 2_permission.md
|   |-- 3_docker_env.md
|   |-- 4_docker_deploy.md
|   |-- 5_dockerfile.md
|   |-- 6_dockerfile_extra.md
|   `-- 7_git.md
|-- images
`-- README.md
```

## 8. 디렉토리 구조 설계 기준

이번 저장소는 실습 대상과 제출 증거를 역할별로 분리하는 기준으로 구성했다.

- `df/`: Dockerfile과 웹 서버 소스코드를 함께 두어 빌드 컨텍스트를 단순하게 유지했다. `docker build -t my_web_server .`를 `df/` 안에서 바로 실행할 수 있도록 한 구조이다.
- `df/app/`: 컨테이너 안으로 복사되는 정적 웹 파일 위치이다. 같은 폴더를 바인드 마운트 대상으로도 사용해, 이미지 빌드와 실시간 반영 실습을 같은 소스로 비교할 수 있게 했다.
- `documents/`: 터미널, 권한, Docker, Git 실습 로그를 주제별로 분리해 README가 너무 길어지지 않도록 했다.
- `images/`: 브라우저 접속 화면, VSCode GitHub 연동 화면처럼 스크린샷 증거를 모아 문서와 분리했다.

즉, 실행에 필요한 파일과 제출 증거 파일을 섞지 않고, `실습 대상(df)`과 `설명 문서(documents, images)`를 나누는 기준으로 구조를 설계했다.

## 9. 포트/볼륨 재현 기준

포트와 볼륨은 매번 같은 방식으로 다시 실행할 수 있도록 이름과 명령 패턴을 고정해서 기록했다.

- 웹 서버 컨테이너는 컨테이너 내부 포트를 항상 `8000`으로 유지했다.
- 호스트 포트는 `8080`을 기준으로 사용하고, 문서에서도 동일한 명령 `docker run -d -p 8080:8000 --name my_web_con my_web_server`를 반복 사용했다.
- 바인드 마운트는 `$(pwd)/app:/app` 형태로 기록해 현재 `df/` 디렉토리 기준에서 바로 재현할 수 있게 했다.
- 볼륨은 이름을 `my_data_vol`로 고정해 컨테이너를 삭제한 뒤에도 같은 이름으로 다시 연결해 영속성을 검증했다.

이렇게 고정된 포트, 컨테이너 이름, 볼륨 이름, 작업 디렉토리 기준을 문서에 명시해 두면 다른 사람이 README를 보고 같은 방식으로 다시 실행할 수 있다.

## 10. 학습 내용 정리

### 절대 경로와 상대 경로

절대 경로는 루트부터 시작하는 전체 경로이고, 상대 경로는 현재 위치를 기준으로 계산하는 경로이다.

- 절대 경로 예시: `/Users/kinch06120270/Desktop/week1/df/app/index.html`
- 상대 경로 예시: `df/app/index.html`

즉, 절대 경로는 어디서 실행해도 같은 대상을 가리키고, 상대 경로는 현재 작업 디렉토리에 따라 해석 결과가 달라진다.

### 파일 권한과 숫자 표기

파일 권한의 `r`, `w`, `x`는 각각 읽기, 쓰기, 실행 권한을 의미한다.

- `r = 4`
- `w = 2`
- `x = 1`

이 값을 사용자, 그룹, 기타 사용자 순서로 더해서 숫자로 표현한다.

- `755`는 `rwxr-xr-x` 이므로 소유자는 읽기/쓰기/실행이 가능하고, 나머지는 읽기/실행만 가능하다.
- `644`는 `rw-r--r--` 이므로 소유자는 읽기/쓰기가 가능하고, 나머지는 읽기만 가능하다.

### 이미지와 컨테이너의 차이

이미지는 실행에 필요한 파일과 설정이 담긴 읽기 전용 템플릿이고, 컨테이너는 그 이미지를 실행한 인스턴스이다.

- 빌드 관점: Dockerfile을 수정하면 새로운 이미지를 다시 빌드해야 한다.
- 실행 관점: `docker run`은 이미지를 바탕으로 실제 실행 중인 컨테이너를 만든다.
- 변경 관점: 실행 중인 컨테이너 안에서 일어난 변경은 원본 이미지를 바꾸지 않는다. 이미지를 바꾸려면 Dockerfile을 수정하고 다시 빌드해야 한다.

이번 실습에서는 `my_web_server` 이미지를 한 번 빌드한 뒤 여러 컨테이너를 실행했다. 또한 바인드 마운트를 사용했을 때는 호스트 파일 수정이 컨테이너에 바로 반영되었지만, 이것 역시 이미지 자체가 바뀐 것이 아니라 실행 환경에 외부 디렉토리를 연결한 결과이다.

### 기존 Dockerfile 기반 커스텀 이미지

이번 과제에서는 `ubuntu:24.04` 이미지를 베이스로 사용해 Python 실행 환경과 정적 웹 서버 실행 기능을 추가했다.

- `apt-get install -y python3 python3-pip`: Python 실행 환경 추가
- `WORKDIR /app`: 작업 디렉토리 고정
- `COPY ./app /app`: 웹 서버에서 제공할 파일 복사
- `CMD ["python3", "-m", "http.server", "8000"]`: 컨테이너 시작 시 웹 서버 실행

즉, 기존 베이스 이미지를 그대로 쓰는 것이 아니라 목적에 맞게 기능을 추가해 커스텀 이미지로 확장했다.

### 포트 매핑이 필요한 이유

컨테이너 안에서 실행되는 서버는 기본적으로 컨테이너 내부 네트워크에만 열려 있으므로, 호스트 브라우저에서 접근하려면 포트를 연결해야 한다.

예를 들어 `-p 8080:8000`은 호스트의 `8080` 요청을 컨테이너의 `8000`으로 전달한다. 그래서 브라우저에서 `http://localhost:8080`으로 접속해도 컨테이너 내부 웹 서버에 접근할 수 있다.

### Docker 볼륨과 영속 데이터

볼륨은 컨테이너를 삭제해도 데이터를 유지하기 위한 Docker 전용 저장소이다.

이번 실습에서는 `my_data_vol`에 파일을 만든 뒤 컨테이너를 삭제하고 다시 연결했는데도 파일이 남아 있었다. 이 과정을 통해 컨테이너와 데이터 저장 위치가 분리되어 있다는 점을 확인할 수 있었다.

### Git과 GitHub의 차이

Git은 내 컴퓨터에서 커밋 이력과 파일 변경을 관리하는 로컬 버전 관리 도구이고, GitHub는 그 Git 저장소를 원격으로 공유하고 협업하는 플랫폼이다.

- Git: `git add`, `git commit`, `git log`처럼 로컬 변경 관리
- GitHub: `git push`, 저장소 공유, 원격 백업, 협업

즉, Git이 버전 관리의 엔진이라면 GitHub는 그 결과물을 함께 관리하고 공유하는 협업 공간에 가깝다.

## 11. 기타 이것저것 정리

### 호스트 포트가 이미 사용 중일 때 진단 순서

포트 매핑이 실패하면 먼저 Docker 명령의 에러 메시지를 확인하고, 그 다음 실제로 누가 그 포트를 점유하고 있는지 확인해야 한다.

1. `docker run -p 8080:8000 ...` 실행 시 출력된 에러 메시지를 읽는다.
2. `docker ps` 또는 `docker ps -a`로 이미 같은 포트를 사용 중인 컨테이너가 있는지 확인한다.
3. `lsof -i :8080` 또는 `netstat` 계열 명령으로 Docker 외 다른 프로세스가 포트를 점유 중인지 확인한다.
4. 원인에 따라 기존 컨테이너를 중지/삭제하거나, 호스트 포트를 `8081`처럼 다른 값으로 바꿔 다시 실행한다.
5. 마지막으로 `docker ps`와 `curl http://localhost:포트번호`로 정상 연결 여부를 검증한다.

### 컨테이너 삭제 후 데이터가 사라지는 것을 막는 방법

컨테이너 내부 파일시스템은 기본적으로 일회성이기 때문에, 중요한 데이터는 컨테이너 안에만 저장하면 안 된다.

- 영속 데이터는 named volume을 사용해 컨테이너 수명과 분리한다.
- 개발 중 소스코드나 설정 파일은 bind mount로 연결해 호스트 파일을 직접 사용한다.
- 데이터베이스나 업로드 파일처럼 중요한 정보는 볼륨과 별도 백업 정책을 함께 가져가는 것이 안전하다.

즉, "컨테이너를 삭제해도 남아야 하는 데이터"는 볼륨으로 분리하고, "호스트에서 즉시 수정해야 하는 파일"은 바인드 마운트로 연결하는 방식으로 구분하는 것이 핵심이다.

### 이 미션에서 가장 어려웠던 지점과 해결 과정

가장 어려웠던 지점은 Dockerfile 자체보다도, 웹 서버 실습 초반에 zsh가 `!` 문자를 특별하게 해석해서 HTML 파일 생성 명령이 실패했던 부분이었다.

- 가설: `</h1>`에 포함된 `!` 때문에 zsh 히스토리 확장이 발생했을 수 있다.
- 확인: 같은 내용을 작은따옴표로 감싸 다시 실행했더니 정상 동작했다.
- 조치: HTML 문자열을 작은따옴표로 감싸 `index.html`을 생성했다.

이 경험을 통해 문제를 만났을 때는 "도구가 잘못됐다"라고 바로 단정하지 않고, 셸, 명령 형식, 인자, 실행 환경을 순서대로 의심해야 한다는 점을 배웠다.
