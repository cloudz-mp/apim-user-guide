# APIM Console 가이드

- [Gateway 관리](#gateway-관리)
- [API 관리](#api-관리)
- [API 배포 관리](#api-배포-관리)
- [API Document](#api-document)
- [Monitoring](#monitoring)

---
## Gateway 관리

1. Gateway 생성하기(Kong)
> Gateway 생성 전 Project, Namespace 생성이 필요합니다. <br> 
> - Project 생성 : APIM 관리 - 사용자 관리(Tenant Manaer Console) 에서 프로젝트 생성이 가능합니다. [여기](./TenantManager_Console.md#프로젝트-관리) 를 클릭하여 Tenant Manager 가이드로 이동합니다. <br>
>   - 1개 Project 당 1개의 Gateway를 생성할 수 있습니다.
>   - 여러 개의 Project를 통해 여러 개의 Gateway를 통합 관리할 수 있습니다.
> - Kong이 설치될 Namespace 생성: ZCP console - Administration - Namespaces 메뉴에서 Kubernetes Namespace 생성이 가능합니다.

- Gateway 타임: kong (AWS 추후 제공)
- Gateway 이름: 필수항목 입니다. 영문, 숫자, 공백, '-', '_', ':' 만 허용됩니다.
- Gateway 설명: Gateway의 설명을 적을 수 있습니다.
- Gateway 태그: 태그 설정이 가능합니다. Gateway 록목록 화면에서 태그 기반으로 검색이 가능합니다. (사용법: 태그를 입력하고 Enter키를 누르세요.)
- Kong Namespace: Kong이 설치될 Namespace를 선택합니다. 
- Gateway URL: Gateway로 들어가는 URL 입니다. API생성 시 사용됩니다.
- tls.crt, tls.key: 입력 시 https 로 호출이 가능합니다. 미 입력 시 http로 호출 가능합니다.

<kbd><img style="width:100%" src="./img/Gateway/gateway01.png" /></kbd>


2. Gateway 생성 후 화면


Gateway 목록 화면 (육각형 모향은 배포된 Kong Pod의 replicas 수를 뜻합니다.) 

<kbd><img style="width:100%" src="./img/Gateway/gateway02.png" /></kbd>

Gateway 상세 화면
- Kong Replcas 수를 설정 할 수 있습니다.
- 설명, 태크, replicas, Gateway URL 부분을 수정할 수 있습니다.
- Gateway를 삭제할 수 있습니다. **주의!! Gateway를 삭제하면 Gateway에 속한 모든 데이터가 삭제됩니다.**

<kbd><img style="width:100%" src="./img/Gateway/gateway03.png" /></kbd>

## API 관리

1. API 생성하기
> API 생성 전 Gateway 생성이 필요합니다. [여기](#gateway-관리) 를 클릭하여 Gateway 생성 가이드로 이동합니다.

- API 이름: 필수항목 입니다. 영문, 숫자, 공백, '-', '_', ':' 만 허용됩니다.
- API 설명: API 설명을 적을 수 있습니다.
- API 태그: 태그 설정이 가능합니다. API 목 화면에서 태그 기반으로 검색이 가능합니다. (사용법: 태그를 입력하고 Enter키를 누르세요.)
- API 타입: 통신 타입을 선택할 수 있습니다. (HTTP or Socket)
- Gateway: API를 생성하려는 Gateway를 선택할 수 있습니다.
- Gateway URL: Gateway에 속한 Gateway URL을 선택할 수 있습니다. API 호출 시 사용됩니다.
- Base Path: 해당 API 호출 시 사용되는 Path입니다. https://<GatewayURL>/<BasePath>
- Backend URL: API 호출 시 맵핑되는 Upstream URL 입니다. https://<GatewayURL>/<BasePath> --> https://<BackendURL> 
- Developers Portal 게시: 체크 시 Developers Portal에 해당 API가 노출됩니다. [여기](../developers/README.md) 를 클릭하면 Developers Portal 가이드로 이동합니다.

<kbd><img style="width:100%" src="./img/Gateway/api01.png" /></kbd>

2. API 상세화면

<kbd><img style="width:100%" src="./img/Gateway/api02.png" /></kbd>

2-1. Frontend - Backend

>Frontend: API 호출 시 사용되는 API URL입니다.
> 
>Backend: Frontend 이랑 맵핑된 Upstream URL 입니다. 

**수정** 버튼 클릭 시 API 수정 화면으로 이동합니다.

2-2. Gateway Policy 수정하기

**Policy 수정** 버튼 클릭 시 Policy 수정 화면으로 이동합니다.

- 미적용 영역에서 + 버튼을 누르면 적용 영역으로 넘어갑니다.
- 적용 영역에서 - 버튼을 누르면 미적용 영역으로 넘어갑니다.
- 각각의 policy 이름을 클릭하면 설정 영역에 config를 설정할 수 있는 화면이 나타납니다. 

<kbd><img style="width:100%" src="./img/Gateway/api03.png" /></kbd>


2-3. API 문서 (Swagger)

- Swagger 문서를 수동으로 입력 가능합니다.
- Backend URL에 Swagger문서가 존재한다면 /v2/api-docs 경로에서 json 형식의 Swagger 문서를 받을 수 있습니다. 이 문서를  Swagger JSON Editor에 넣으면 Swagger UI가 보여집니다.

API Swagger 적용 예시 화면입니다.

<kbd><img style="width:100%" src="./img/Gateway/api04.png" /></kbd>

2-4. API TEST 기능

- API 배포 전 충분한 테스트가 가능합니다.
- Method (GET, POST, PUT, DELETE, HEAD, OPTIONS, PATCH) 선택 가능하고, 특정 URL Path를 입력해 테스트할 수 있습니다. Template, Header, Query 입력도 가능합니다.
- Template: Path가 /{key1} 이고, Template이 { "key1" : "value1" } 이면 최종 Path는 /value1 로 자동 변환 됩니다.

2-5 배포 하기

- 충분한 테스트를 거친 후 API를 배포하여 외부로 노출시킬 수 있습니다.
- <배포하기> 버튼을 클릭하면 배포 버전에 대한 설명을 적어야 합니다. (필수입력)
- **배포는 여러번** 가능합니다. 배포할때마다 현재 시간을 버전명으로 배포가 됩니다. **단, 배포할때마다 최신버전만 외부로 노출됩니다.**(하나의 버전만 노출이 가능합니다.)

## API 배포 관리

API 배포 현황 화면 - 프로젝트에 속한 배포된 API들을 보여줍니다.

<kbd><img style="width:100%" src="./img/Gateway/deploy01.png" /></kbd>

API 배포 상세 화면

- API 상세화면과 비슷합니다. 하지만 이 화면에서는 Frontend, Backend, Policy, Swagger 문서를 수정할 수 없습니다.
- 과거에 배포한 버전으로 롤백이 가능합니다. 기존 버전 목록에서 버전을 선택 후 <선택 버전 배포>를 클릭하면 해당 버전으로 바뀝니다.

<kbd><img style="width:100%" src="./img/Gateway/deploy02.png" /></kbd>

## API Document

API Document 목록을 보여줍니다. API 생성 당시 Swagger 문서를 입력했다면 목록에 나옵니다.

<kbd><img style="width:100%" src="./img/Gateway/doc01.png" /></kbd>

API Document 상세 화면에서는 아래 사진과 같이 Swagger UI를 보여줍니다.

<kbd><img style="width:100%" src="./img/Gateway/doc02.png" /></kbd>


## Monitoring

Monitoring 메뉴 클릭 시 Grafana 화면으로 이동합니다. 

Grafana에는 Kong 리소스를 확인할 수 있는 Dashboard가 존재합니다. (Dashboards --> General --> Kong)

<kbd><img style="width:100%" src="./img/Gateway/monitoring01.png" /></kbd>



