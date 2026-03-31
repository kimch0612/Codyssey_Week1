Subject 0: 에러 핸들링
----

> 도커 이름 소문자
```bash
kinch06120270@c4r6s3 week1 % docker run -d Ubuntu /bin/bash
docker: invalid reference format: repository name (library/Ubuntu) must be lowercase # 도커에선 컨테이너 이름을 소문자만 사용할 수 있다?

Run 'docker run --help' for more information

kinch06120270@c4r6s3 week1 % docker run -d --name ubuntu f794f40ddfff /bin/bash # 이름을 소문자로만
dbccb6e7683fd38f06d1d47faef7695d3b3939946844c45b3beff2f67538e6b1

kinch06120270@c4r6s3 week1 % # 해결
```

> zsh 문법 오류
```bash
kinch06120270@c4r6s3 app % echo "<h1>Hello from Docker Python Server!</h1>" > index.html 
zsh: event not found: </h1> # 앞쪽 <h1>엔 문제가 없었으니 </h1>에 붙은 !가 문제다?

# 작은따옴표를 사용하면 !를 무시하므로 해결 방법은 간단하게 작은따옴표를 사용함
kinch06120270@c4r6s3 app % echo '<h1>Hello from Docker Python Server!</h1>' > index.html

kinch06120270@c4r6s3 app % # 해결
# zsh에선 큰따옴표 안에 있는 !를 예약어로 사용함. 그래서 엉뚱하게 </h1>가 호출됨.
```