Subject 0: 에러 핸들링
----

> 도커 이름 소문자
```bash
# 도커에선 컨테이너 이름을 소문자만 사용할 수 있음
kinch06120270@c4r6s3 week1 % docker run -d Ubuntu /bin/bash
docker: invalid reference format: repository name (library/Ubuntu) must be lowercase

Run 'docker run --help' for more information

kinch06120270@c4r6s3 week1 % docker run -d --name ubuntu f794f40ddfff /bin/bash
dbccb6e7683fd38f06d1d47faef7695d3b3939946844c45b3beff2f67538e6b1

kinch06120270@c4r6s3 week1 % 
```

> zsh 문법 오류
```bash
# zsh에선 큰따옴표 안에 있는 !를 예약어로 사용함. 그래서 엉뚱하게 </h1>가 호출됨.
kinch06120270@c4r6s3 app % echo "<h1>Hello from Docker Python Server!</h1>" > index.html 
zsh: event not found: </h1>

# 해결 방법은 간단하게 작은따옴표를 사용함
kinch06120270@c4r6s3 app % echo '<h1>Hello from Docker Python Server!</h1>' > index.html

kinch06120270@c4r6s3 app %
```