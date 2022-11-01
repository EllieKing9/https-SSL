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
대칭키: 동일한 키(password)로 암호화와 복호화를 진행
$openssl enc -e -des3 -salt -in input.txt -out outtext.bin
$openssl enc -d -des3 -in outtxt.bin -out input.txt

공개키(비대칭키): 
  두개의 키를 가진다. 공개(public)키와 비공개(private)키
  공개키 B로 복호화   <- 비공개 A키로 암호화
  공개키 B키로 암호화 -> 비공개 A로 복호화
$openssl genrsa -out private.pem 1024
$cat private.pem

$openssl rsa -in private.pem -out public.pem outform PEM -pubout
$echo 'coding everybody' > file.txt
$openssl rsautl -encrypt -inkey public.pem -pubin -in file.txt -out file.ssl
$openssl rsautl -decrypt -inkey private.pem -in file.ssl -out decrypted.txt
```

SSL
```
SSL 인증서
- 서비스의 정보(인증서를 발급한 CA, 서비스의 도메인 등)
- 서버 측 공개키

브라우저는 CA 리스트와 CA별 공개키를 이미 가지고 있으며 (CA에서 제공된)

실제 데이터 : 대칭키
대칭키의 키 : 공개키
```

접속

https://wan-blog.tistory.com/47
```
Client Hello
1. 클라이언트가 서버에 접속하며 클라이언트 측에서 생성한 랜덤 데이터
2. 클라이언트가 지원하는 암호화 방식들
3. 세션 아이디 전송

Server Hello
4. 서버측에서 생성한 랜덤 데이터
5. 서버가 선택한 클라이언트 암호화 방식
6. 서버 인증서(공개키) 전송

Client 
7. 서버에서 받은 인증서가 CA에 의해서 발급된 것인지를 확인(CA 리스트 확인)
8. CA 리스트에 없다면 경고 메세지
9. CA의 공개키를 이용해서 인증서를 복호화
10. 서버의 랜덤데이터와 클라이언트의 랜덤데이터를 조합하여 pre master secret라는 키(대칭키)를 생성하여 서버의 공개키를 이용해서 암호화하여 전송

Server
11. pre master secret 값을 서버의 비공개키로 복호화

추 후, 대칭키(pre master secret 값)를 가지고 암호화하여 통신
```

인증서 발급
```
CA에서 제공 :
서비스의 정보(인증서를 발급한 CA, 서비스의 도메인 등)과
발급되는 서버의 공개키를 
CA가 가지고 있는 비공개키(개인키)로 암호화하여 인증서를 만들어 제공


```
