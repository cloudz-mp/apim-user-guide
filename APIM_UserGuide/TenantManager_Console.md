#  Tenant-Manager

- [권한 (Role)](#권한-(Role))
- [사용자 관리](#사용자-관리)
    - [SSO 사용자 조회 및 사용자 추가](#SSO-사용자-조회-및-사용자-추가)
    - [사용자 관리](#사용자-관리) 
    - [권한 수정](#권한-수정)
    - [사용자 삭제](#사용자-삭제)
- [프로젝트 관리](#프로젝트-관리)
    - [프로젝트 생성](#프로젝트-생성)
    - [프로젝트 사용자 관리](#프로젝트-사용자-관리)
    - [프로젝트 삭제](#프로젝트-삭제)

## 권한 (Role)

### 시스템 권한
| 권한  | 설명  |
|---|---|
| apim-admin | APIM 전체 관리자 |
| apim-member | APIM 일반 사용자 권한 <br> Cloud Z CP의 사용자를 APIM으로 SSO사용자 가져오기 시 적용할 수 있는 기본 권한 |
| devportal-admin | Developers Portal 전체 관리자 |
| devportal-api-admin | Developers Portal Product 및 API 관리자 <br> Developers Portal 에 게시된 특정 Product-API의 관리, 설명 작성, Q&A, 결함 개선 등을 담당하는 권한|
| devportal-member | Developers Portal 일반 사용자 권한 <br> Developers Portal 에 사용자로 회원 가입 시 부여되는 기본 권한 <br> My Application 생성 및 멤버 초대 가능|

  
### 프로젝트 권한
APIM에서 프로젝트는 2가지 type으로 표시 합니다.

 - type: apim - APIM Console의 내부 API 개발용 조직/팀의 개념이고, APIM Console에서 "프로젝트(Project)"로 표시됨
 - type: developers - Developers Portal의 일반 사용자가 개발하기 위한 "Application 또는 My Application"

| type | 권한  | 설명  |
|---|---|---|
|apim   |apim-pjt-admin	| APIM 프로젝트 관리자<br>프로젝트 API 기본 정책, API KEY, 멤버 관리|
|apim   |apim-pjt-member | APIM 프로젝트 멤버|
|developers   |devportal-pjt-admin<br>(App. 관리자)	| Developers Portal의 Application 관리자|
|developers   |devportal-pjt-member | Developers Portal의 Application 멤버|
## 사용자 관리
### **SSO 사용자 조회 및 사용자 추가**
---
Apim은 ZCP SSO와 연동하여 사용자를 추가하며 사용자 권한을 따로 관리합니다. 
1. Tenant-Manager 메뉴에서 사용자 관리를 클릭합니다.
![user1](./img/TenantManager/user1.png)
2. SSO 사용자 가져오기 버튼을 눌러 SSO 사용자를 조회한 후 추가할 사용자를 선택합니다.
![user3](./img/TenantManager/user3.png)
3. 추가할 사용자를 선택하고 가져오기 버튼을 누르면 대항 사용자에 대한 권한을 선택합니다. 
![user5](./img/TenantManager/user5.png)
4. 권한 선택 후 사용자 권한 설정 및 가져오기 버튼으로 사용자를 추가할 수 있습니다.
![user6](./img/TenantManager/user6.png)

### **사용자 정보 수정**

---
1. 사용자 정보 관리를 위해 해당 사용자의 상세 버튼을 클릭합니다
![user1](./img/TenantManager/user1.png)
2. 사용자의 정보를 수정 할 수 있습니다.
![user7](./img/TenantManager/user7.png)
### **권한 수정**
---

1. 권한 수정을 위해 해당 사용자의 권한 변경 버튼을 클릭합니다.
![user1](./img/TenantManager/user1.png)
2. 사용자의 권한을 수정 할 수 있습니다.
![user9](./img/TenantManager/user9.png)
### **사용자 삭제**
---
1. 사용자 삭제를 위해 해당 사용자의 삭제 버튼을 클릭합니다
![user1](./img/TenantManager/user1.png)
2. 사용자 정보 확인 후 삭제 버튼을 클릭하면 해당 사용자가 삭제됩니다.
![user8](./img/TenantManager/user8.png)
## 프로젝트 관리
### **프로젝트 생성**
---

1. Tenant-Manager 메뉴에서 프로젝트 관리를 클릭합니다.
![project1](./img/TenantManager/project1.png)
2. 각 항목을 입력합니다
![project2](./img/TenantManager/project2.png)
    - 프로젝트 환경에 따라 Apim, Developer Portal 타입을 선택합니다.

### **프로젝트 사용자 관리**
---
1. 프로젝트 사용자 권한 관리를 위해 해당 프로젝트의 상세 버튼을 클릭합니다.
![project1](./img/TenantManager/project1.png)
2. 프로젝트 사용자 관리 탭의 프로젝트 사용자 추가버튼을 클릭합니다.
![project4](./img/TenantManager/project4.png)
3. 추가할 사용자를 조회하여 선택합니다.
![project5](./img/TenantManager/project5.png)
4. 추가할 사용자의 권한을 선택 후 프로젝트 사용자 권한 설정 및 추가버튼을 클릭합니다.
![project7](./img/TenantManager/project7.png)
5. 사용자가 추가되면 권한변경, 삭제가 가능합니다.
![project8](./img/TenantManager/project8.png)

### **프로젝트 삭제**
---

1. 삭제할 프로젝트의 삭제 버튼을 클릭합니다.
![project1](./img/TenantManager/project1.png)
2. 프로젝트 정보 확인 후 삭제 버튼을 클릭하면 해당 프로젝트가 삭제됩니다.
![project11](./img/TenantManager/project11.png)