Subject 0: 트러블슈팅
----

## 1. 가장 어려웠던 지점: zsh에서 `!` 문자로 인한 HTML 작성 실패

### 문제 상황

웹 서버 실습을 위해 `index.html`을 터미널에서 바로 만들려고 했는데, 아래 명령이 실패했다.

```bash
kinch06120270@c4r6s3 app % echo "<h1>Hello from Docker Python Server!</h1>" > index.html
zsh: event not found: </h1>
```

### 왜 어려웠는가

처음에는 HTML 문법이 잘못되었거나 리다이렉션(`>`) 때문에 생긴 문제라고 생각했다. 하지만 `<h1>` 태그 자체는 단순한 문자열이라서 어떤 부분이 원인인지 바로 떠오르지 않았다.

### 원인 가설

오류 메시지가 `</h1>` 부분을 가리키고 있었기 때문에, 닫는 태그 안에 포함된 `!` 문자를 zsh가 히스토리 확장 문자로 해석했을 가능성을 의심했다.

### 확인 과정

- 에러 위치가 항상 `</h1>` 쪽에서 발생하는지 확인했다.
- 같은 문자열을 작은따옴표로 감싸서 다시 실행해 보았다.
- 작은따옴표로 바꾸자 같은 내용이 정상적으로 파일에 기록되었다.

```bash
kinch06120270@c4r6s3 app % echo '<h1>Hello from Docker Python Server!</h1>' > index.html

kinch06120270@c4r6s3 app % cat index.html
<h1>Hello from Docker Python Server!</h1>
```

### 조치

큰따옴표 대신 작은따옴표를 사용해 zsh가 `!`를 특수문자로 해석하지 않도록 했다.

### 결과와 배운 점

문제는 Docker나 Python 서버가 아니라 셸(zsh)의 문법 처리에서 발생했다. 이번 경험을 통해 CLI 작업에서는 실행 대상뿐 아니라 셸의 확장 규칙도 같이 확인해야 한다는 점을 배웠다.

## 2. Docker 이미지 이름 대문자 사용으로 인한 실행 실패

### 문제 상황

Ubuntu 이미지를 실행하려고 아래 명령을 입력했지만 실행되지 않았다.

```bash
kinch06120270@c4r6s3 week1 % docker run -d Ubuntu /bin/bash
docker: invalid reference format: repository name (library/Ubuntu) must be lowercase

Run 'docker run --help' for more information
```

### 원인 가설

에러 메시지에 `must be lowercase`가 명확하게 보였기 때문에, 이미지 참조 이름을 대문자로 입력한 것이 원인이라고 판단했다.

### 확인 과정

- 오류 메시지에 포함된 `lowercase` 문구를 확인했다.
- 동일한 이미지 ID를 사용하고, 이름을 소문자로 바꿔 다시 실행했다.

```bash
kinch06120270@c4r6s3 week1 % docker run -d --name ubuntu f794f40ddfff /bin/bash
dbccb6e7683fd38f06d1d47faef7695d3b3939946844c45b3beff2f67538e6b1
```

### 조치

Docker 이미지 이름과 레포지토리 참조는 소문자로만 작성해야 한다는 규칙에 맞춰 명령을 수정했다.

### 결과와 배운 점

Docker는 이미지 참조 형식이 엄격하므로, 실행 전 에러 메시지에 나온 키워드를 먼저 읽는 습관이 중요하다는 점을 확인했다. 단순 오타처럼 보이는 문제도 규칙을 모르면 바로 해결하기 어렵다.
