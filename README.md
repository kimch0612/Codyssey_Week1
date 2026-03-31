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
- [x] 트러블슈팅 2건 기록
- [x] VSCode GitHub 로그인 및 저장소 연동 증거 보강
- [x] 기본 브랜치 설정 증거 보강
- [ ] 브라우저 주소창 포함 접속 스크린샷 보강
- [ ] 학습 목표 설명형 정리 보강

## 4. 검증 방법과 결과 위치

### 터미널 조작

- 현재 위치 확인: `pwd`
- 숨김 파일 포함 목록 확인: `ls -alh`
- 파일 생성/복사/이동/이름 변경/삭제: `touch`, `cp`, `mv`, `rm`
- 파일 내용 확인: `cat`
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
