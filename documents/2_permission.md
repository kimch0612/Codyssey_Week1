Subject 2: Permission 실습
----

> 권한 확인하기
```bash
kinch06120270@c4r6s3 week1 % ls -alh
total 16
drwxr-xr-x   7 kinch06120270  kinch06120270   224B Mar 30 17:34 .
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:08 ..
drwxr-xr-x  14 kinch06120270  kinch06120270   448B Mar 30 17:35 .git
drwxr-xr-x   5 kinch06120270  kinch06120270   160B Mar 30 17:22 documents
drwxr-xr-x   3 kinch06120270  kinch06120270    96B Mar 30 17:09 images
-rw-r--r--@  1 kinch06120270  kinch06120270   533B Mar 30 17:23 README.md
-rw-r--r--   1 kinch06120270  kinch06120270    12B Mar 30 17:34 TEST.txt

kinch06120270@c4r6s3 week1 % 
```

> 파일 권한 변경하기
```bash
kinch06120270@c4r6s3 week1 % chmod 600 TEST.txt

kinch06120270@c4r6s3 week1 % ls -alh
total 16
drwxr-xr-x   7 kinch06120270  kinch06120270   224B Mar 30 17:34 .
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:08 ..
drwxr-xr-x  14 kinch06120270  kinch06120270   448B Mar 30 17:35 .git
drwxr-xr-x   5 kinch06120270  kinch06120270   160B Mar 30 17:22 documents
drwxr-xr-x   3 kinch06120270  kinch06120270    96B Mar 30 17:09 images
-rw-r--r--@  1 kinch06120270  kinch06120270   533B Mar 30 17:23 README.md
-rw-------   1 kinch06120270  kinch06120270    12B Mar 30 17:34 TEST.txt

kinch06120270@c4r6s3 week1 % 
```

> 폴더 권한 변경하기
```bash
kinch06120270@c4r6s3 week1 % mkdir testfolder

kinch06120270@c4r6s3 week1 % ls -alh
total 16
drwxr-xr-x   8 kinch06120270  kinch06120270   256B Mar 30 17:40 .
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:08 ..
drwxr-xr-x  14 kinch06120270  kinch06120270   448B Mar 30 17:35 .git
drwxr-xr-x   5 kinch06120270  kinch06120270   160B Mar 30 17:22 documents
drwxr-xr-x   3 kinch06120270  kinch06120270    96B Mar 30 17:09 images
-rw-r--r--@  1 kinch06120270  kinch06120270   533B Mar 30 17:23 README.md
-rw-------   1 kinch06120270  kinch06120270    12B Mar 30 17:34 TEST.txt
drwxr-xr-x   2 kinch06120270  kinch06120270    64B Mar 30 17:40 testfolder

kinch06120270@c4r6s3 week1 % chmod 777 testfolder

kinch06120270@c4r6s3 week1 % ls -alh
total 16
drwxr-xr-x   8 kinch06120270  kinch06120270   256B Mar 30 17:40 .
drwx------+  5 kinch06120270  kinch06120270   160B Mar 30 17:08 ..
drwxr-xr-x  14 kinch06120270  kinch06120270   448B Mar 30 17:35 .git
drwxr-xr-x   5 kinch06120270  kinch06120270   160B Mar 30 17:22 documents
drwxr-xr-x   3 kinch06120270  kinch06120270    96B Mar 30 17:09 images
-rw-r--r--@  1 kinch06120270  kinch06120270   533B Mar 30 17:23 README.md
-rw-------   1 kinch06120270  kinch06120270    12B Mar 30 17:34 TEST.txt
drwxrwxrwx   2 kinch06120270  kinch06120270    64B Mar 30 17:40 testfolder

kinch06120270@c4r6s3 week1 % 
```

### 간단한 정리
- 폴더는 맨 첫번째 권한 키워드에 d가 붙는다
- 파일은 맨 첫번째 권한 키워드에 아무것도 들어가지 않는다 (-)