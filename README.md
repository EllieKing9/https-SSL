# https-SSL

https://opentutorials.org/course/1334/1450

도메인 캐시 변경: https://opentutorials.org/course/1334/1457
```
도메인(Domain) 를 IP 와 매칭

1. local cache 를 검색
>ipconfig /displaydns
//>ipconfig /renew

2. hosts 파일 검색

3. 도메인 네임서버를 검색

```

HTTPS와 SSL

https://opentutorials.org/course/1334/4894

https://jackerlab.com/nginx-redirect-port-forwarding/
```
HTTPS: Hypertext Transfer Protocol over Secure Socket layer
SSL 인증서: 클라이언트와 서버간의 통신을 제3자가 보증해주는 전자화된 문서 -> 키
```

키
```
$openssl enc -e -des3 -salt -in input.txt -out outtext.bin
$openssl enc -d -des3 -in outtxt.bin -out input.txt

대칭키: 동일한 키로 암호화와 복호화를 진행
공개키(비대칭키): 
```
