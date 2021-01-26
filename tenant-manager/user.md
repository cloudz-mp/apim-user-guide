# User

##  목차

1. 개요
2. SSO 사용자 조회 및 사용자 추가
3. 사용자 관리 및 권한 수정
5. 사용자 삭제

## 1. 개요
---
본 문서는 Apim 및 Developer Portal의 사용자, 권한 관리 방법을 다루는 문서입니다.

## 2. SSO 사용자 조회 및 사용자 추가
---
Apim은 ZCP SSO와 연동하여 사용자를 추가하며 사용자 권한을 따로 관리합니다. 
1. Tenant-Manager 메뉴에서 사용자 관리를 선택합니다.
![user main](./img/user1.png)
2. SSO 사용자 가져오기 버튼을 눌러 SSO 사용자를 조회한 후 추가할 사용자를 선택합니다.
![user main](./img/user3.png)
3. 추가할 사용자를 선택하고 가져오기 버튼을 누르면 대항 사용자에 대한 권한을 선택합니다. 
![user main](./img/user5.png)

    | 권한  | 설명  |
    |---|---|---|---|---|
    | apim-admin | APIM 관리자 |
    | apim-member | APIM 멤버 |
    | devportal-admin | DEV. PORTAL 관리자 |
    | devportal-api-admin | DEV. PORTAL API 관리자 |
    | devportal-member | DEV. PORTAL 일반 사용자 권한 |

4. 권한 선택 후 사용자 권한 설정 및 가져오기 버튼으로 사용자를 추가할 수 있습니다.
![user main](./img/user6.png)

## 3. 사용자 관리
---
1. 사용자 정보 관리를 위해 해당 사용자의 상세 버튼을 선택합니다
![user main](./img/user1.png)
2. 사용자의 정보를 수정 할 수 있습니다.
![user main](./img/user7.png)
3. 권한 수정을 위해 해당 사용자의 권한 변경 버튼을 선택합니다.
![user main](./img/user1.png)
4. 사용자의 권한을 수정 할 수 있습니다.
![user main](./img/user9.png)
## 4. 사용자 삭제
---
1. 사용자 삭제를 위해 해당 사용자의 삭제 버튼을 선택합니다
![user main](./img/user1.png)
2. 사용자를 삭제 할 수 있습니다.
![user main](./img/user8.png)