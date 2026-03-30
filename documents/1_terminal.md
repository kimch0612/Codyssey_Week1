Subject 1: Terminal 실습
----

> 현재 위치 확인
```bash
kinch06120270@c4r6s3 week1 % pwd
/Users/kinch06120270/Desktop/week1

kinch06120270@c4r6s3 week1 % 
```

> 숨김 파일을 포함해서 목록 확인
```bash
kinch06120270@c4r6s3 week1 % ls -alh
total 8
drwxr-xr-x   6 kinch06120270  kinch06120270   192B Mar 30 17:09 .
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:08 ..
drwxr-xr-x  14 kinch06120270  kinch06120270   448B Mar 30 17:23 .git
drwxr-xr-x   5 kinch06120270  kinch06120270   160B Mar 30 17:22 documents
drwxr-xr-x   3 kinch06120270  kinch06120270    96B Mar 30 17:09 images
-rw-r--r--@  1 kinch06120270  kinch06120270   533B Mar 30 17:23 README.md

kinch06120270@c4r6s3 week1 % 
```

> 파일 생성
```bash
kinch06120270@c4r6s3 week1 % ls -alh
total 8
drwxr-xr-x   6 kinch06120270  kinch06120270   192B Mar 30 17:09 .
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:08 ..
drwxr-xr-x  14 kinch06120270  kinch06120270   448B Mar 30 17:23 .git
drwxr-xr-x   5 kinch06120270  kinch06120270   160B Mar 30 17:22 documents
drwxr-xr-x   3 kinch06120270  kinch06120270    96B Mar 30 17:09 images
-rw-r--r--@  1 kinch06120270  kinch06120270   533B Mar 30 17:23 README.md

kinch06120270@c4r6s3 week1 % touch TESTFILE

kinch06120270@c4r6s3 week1 % ls -alh
total 8
drwxr-xr-x   7 kinch06120270  kinch06120270   224B Mar 30 17:28 .
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:08 ..
drwxr-xr-x  14 kinch06120270  kinch06120270   448B Mar 30 17:23 .git
drwxr-xr-x   5 kinch06120270  kinch06120270   160B Mar 30 17:22 documents
drwxr-xr-x   3 kinch06120270  kinch06120270    96B Mar 30 17:09 images
-rw-r--r--@  1 kinch06120270  kinch06120270   533B Mar 30 17:23 README.md
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 17:28 TESTFILE

kinch06120270@c4r6s3 week1 % 
```

> 파일 복사
```bash
kinch06120270@c4r6s3 week1 % ls -alh ~/Downloads   
total 16
drwx------+  4 kinch06120270  kinch06120270   128B Mar 30 17:08 .
drwxr-x---+ 21 kinch06120270  kinch06120270   672B Mar 30 17:15 ..
-rw-r--r--@  1 kinch06120270  kinch06120270   6.0K Mar 30 17:08 .DS_Store
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 16:49 .localized
kinch06120270@c4r6s3 week1 % cp TESTFILE ~/Downloads 

kinch06120270@c4r6s3 week1 % ls -alh ~/Downloads    
total 16
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:30 .
drwxr-x---+ 21 kinch06120270  kinch06120270   672B Mar 30 17:15 ..
-rw-r--r--@  1 kinch06120270  kinch06120270   6.0K Mar 30 17:08 .DS_Store
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 16:49 .localized
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 17:30 TESTFILE

kinch06120270@c4r6s3 week1 % 
```

> 파일 삭제
```bash
kinch06120270@c4r6s3 week1 % rm ~/Downloads/TESTFILE 

kinch06120270@c4r6s3 week1 % ls -alh ~/Downloads    
total 16
drwx------+  4 kinch06120270  kinch06120270   128B Mar 30 17:30 .
drwxr-x---+ 21 kinch06120270  kinch06120270   672B Mar 30 17:15 ..
-rw-r--r--@  1 kinch06120270  kinch06120270   6.0K Mar 30 17:08 .DS_Store
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 16:49 .localized
kinch06120270@c4r6s3 week1 % 
```

> 파일 이동
```bash
kinch06120270@c4r6s3 week1 % ls -alh ~/Downloads    
total 16
drwx------+  4 kinch06120270  kinch06120270   128B Mar 30 17:30 .
drwxr-x---+ 21 kinch06120270  kinch06120270   672B Mar 30 17:15 ..
-rw-r--r--@  1 kinch06120270  kinch06120270   6.0K Mar 30 17:08 .DS_Store
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 16:49 .localized
kinch06120270@c4r6s3 week1 % mv TESTFILE ~/Downloads 

kinch06120270@c4r6s3 week1 % ls -alh ~/Downloads    
total 16
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:32 .
drwxr-x---+ 21 kinch06120270  kinch06120270   672B Mar 30 17:15 ..
-rw-r--r--@  1 kinch06120270  kinch06120270   6.0K Mar 30 17:08 .DS_Store
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 16:49 .localized
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 17:28 TESTFILE

kinch06120270@c4r6s3 week1 % ls -alh .              
total 8
drwxr-xr-x   6 kinch06120270  kinch06120270   192B Mar 30 17:32 .
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:08 ..
drwxr-xr-x  14 kinch06120270  kinch06120270   448B Mar 30 17:23 .git
drwxr-xr-x   5 kinch06120270  kinch06120270   160B Mar 30 17:22 documents
drwxr-xr-x   3 kinch06120270  kinch06120270    96B Mar 30 17:09 images
-rw-r--r--@  1 kinch06120270  kinch06120270   533B Mar 30 17:23 README.md

kinch06120270@c4r6s3 week1 % 
```

> 파일 이름 변경
```bash
kinch06120270@c4r6s3 week1 % mv ~/Downloads/TESTFILE ~/Downloads/TESTTEST

kinch06120270@c4r6s3 week1 % ls -alh ~/Downloads
total 16
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:33 .
drwxr-x---+ 21 kinch06120270  kinch06120270   672B Mar 30 17:15 ..
-rw-r--r--@  1 kinch06120270  kinch06120270   6.0K Mar 30 17:08 .DS_Store
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 16:49 .localized
-rw-r--r--   1 kinch06120270  kinch06120270     0B Mar 30 17:28 TESTTEST

kinch06120270@c4r6s3 week1 %
```

> 빈 파일 생성, 파일 내용 확인
```bash
kinch06120270@c4r6s3 week1 % touch TEST.txt

kinch06120270@c4r6s3 week1 % cat TEST.txt

kinch06120270@c4r6s3 week1 % echo "Hello World" > TEST.txt

kinch06120270@c4r6s3 week1 % cat TEST.txt
Hello World

kinch06120270@c4r6s3 week1 % 
```