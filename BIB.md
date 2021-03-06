### Prerequisites / 선행 조건

```
OS : Linux(Debian 10)
```

### Installing / 설치

아래 명시된 Package Install은 필수 사항 입니다.

```
Nginx : 1.10.3
IPFS : 0.7.0
Incron : 0.5.10
Node.js : v12.19.0
MongoDB : v4.4.1
```

## Test / 테스트

아래의 순서대로 테스트를 진행할 수 있습니다.
### [접속 URL Click](http://52.231.26.54:3000/)

### 테스트는 Seller -> Buyer -> Seller 순서로 진행
![login](https://user-images.githubusercontent.com/41175032/99395632-0f77c100-2924-11eb-842e-3499b5852608.PNG)
```
Seller와 Buyer의 계정은 아래를 참고하시면 됩니다.
Seller
  ID : alice
  PW : Alice!234
Buyer
  ID : bob
  PW : Bob!234
```
![sell_1](https://user-images.githubusercontent.com/41175032/99398815-359f6000-2928-11eb-98d5-d999f83a91d4.png)
```
[인증서 판매 등록]
  1. 화면 우측에 배터리 정보 입력 및 파일  후 Local에 저장되어 있는 인증서(Pdf) 선택
  2. '인증서 올리기' 클릭하여 판매 등록
  3. 업로드된 인증서는 거래전까지 'SEND'버튼 비활성화.
  4. 우측 상단의 계정 클릭 후 'Logout' 클릭
```
![buy_1](https://user-images.githubusercontent.com/41175032/99398812-346e3300-2928-11eb-8ec8-39db03b2bf04.png)
```
[인증서 구매 및 진위 확인]
  5. 구매하려는 인증서 Section에서 'Download(Preview)' 클릭 후 인증서 파일 확인
  6. 'Buy' 클릭을 통해 인증서 진위여부 확인 및 송금
  7. 우측 상단의 계정 클릭 후 'Logout' 클릭
```
![sell_2](https://user-images.githubusercontent.com/41175032/99398818-3637f680-2928-11eb-9e21-d0de5af8d25b.png)
```
[인증서 구매 및 진위 확인]
  8. My Wallet과 Recent Transaction Hitory에서 송금 받은 금액 토큰 및 이력 확인.
  9. 결제되어진 인증서는 활성화 된 'Send'버튼으로 인증서 양도 가능하며 양도되어진 인증서는 My Batteries에서 사라짐.
```

## Deployment / 배포

### Jenkins 사용
```
Git Bash 및 Jenkins를 통한 배포 방법입니다.
  1. master Branch에 Push
  2. OO.OO...:8080 (Jenkins Server)에 접속
    ID : azureadmin
    PW : OO..
  3. 'skbcweb' 작업을 클릭 후 Build Now 클릭
```
### VScode 사용
```
VScode 사용시 ftp-simple을 설치 후 Config를 아래와 같이 설정합니다.
  1. F1키 입력 후 'ftp-simple:Config - FTP connection setting' 클릭
  2. 설정 정보(입력 후 저장)
    host : WEB Server IP
    port : 22
    type : sftp
    username : WEB Server 접속 계정명
    password : WEB Server 접속 계정 암호
    paht : WEB 코드가 있는 최상위 Directory
  3. 'ftp-simple: Remote directory open to workspace' 클릭
  4. 해당 디렉토리 및 코드들이 보이면 수정 후 저장하면 서버에 배포
```
*단, 해당 배포는 서버의 재기동이 필요 없을 경우(필요시 서버 직접 접근 후 아래 방법으로 재기동)*
### 서버 재기동
```
  1. 52.231.26.54로 SSH 접근
    username : azureadmin
    password : OO..(보안상의 이유로 미작성)
  2. /home/azureadmin/.....해당 디렉토리 접근
  3. command 입력
    forever stop 0
    forever start main.js or node main.js
```
