# Api Policy

- [Policy](#Policy)
    - [Key Auth](#Key-Auth)
    - [Rate Limit](#Rate-Limit)
    - [Txid](#Txid)
    - [OIDC](#OIDC)
    - [Cors](#Cors)
    - [Proxy Cache](#Proxy-Cache)
    - [Request Transformer](#Request-Transformer)
    - [Response Transformer](#Response-Transformer)
    - [Http Log](#Http-Log)
- [Api 정책 설정](#Api-정책-설정)
- [Api 기본정책 설정](#Api-기본정책-설정)
---
## Api 정책 설정
1. Api에 정책을 설정하기 위해 Api 관리메뉴 > Api 상세페이지로 이동합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy1.png"></img></kbd>
2. Overview > Gateway 탭의 Policy 수정 버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
3. 미적용 탭에서 적용할 정책의 Plus/Minus 버튼으로 적용/미적용 설정이 가능합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy3.png"></img></kbd>
    - 각 정책에 대한 설명은 [Policy](#Policy) 참조
4. 적용된 정책을 클릭하여 상세 정보를 입력하고 저장버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy4.png"></img></kbd>
5. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>

---
## Policy
### Key Auth
---
Api에 Key인증을 추가합니다. Api 호출 시 Header에 API 키를 추가하여 인증할 수 있습니다.
#### Apikey 생성
1. APIM 관리 -> API KEY 페이지로 이동하여 프로젝트를 선택합니다.
<kbd><img style="width:100%" src="./img/Policy/CreateKey1.png"></img></kbd>
2. API KEY 생성버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/CreateKey2.png"></img></kbd>
3. Api Key의 간단한 설명을 적고 생성합니다. 
- Api Key는 임의의 값으로 자동생성 되며 생성된 Api Key는 Project의 모든 Api가 공유합니다.

#### Key Auth 설정  
1. Key Auth를 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 Key Auth의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/KeyAuth.png"></img></kbd>
3. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
- API 호출 시 현재 프로젝트의 API KEY 로 인증 합니다. <br>
만약 가능한 API KEY가 없는 경우, API를 정상 호출할 수 없음에 유의 바랍니다.<br>
API KEY Header Name은 x-apim-key 입니다.

### Rate Limit
---
Rate Limit는 API 호출 시 초당 최대 요청수를 설정하며 최대요청수 이상으로는 API를 호출할 수 없습니다.
1. Rate Limit를 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 Rate Limit의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/RateLimiting.png"></img></kbd>
3. 초당 최대요청수를 설정한 수 저장합니다.
4. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
### Txid
---
Txid는 API 호출 시 매 요청마다 HTTP Header에 Transaction ID가 자동 부여 됩니다. 
1. Txid를 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 Txid의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/txid.png"></img></kbd>
3. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
### OIDC
---
OIDC Provider와 연동하여 Api 인증합니다.
1. OIDC 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 OIDC의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/oidc.png"></img></kbd>
    | 항목  | 설명  |
    |---|---|
    | Client ID | OIDC 클라이언트 ID |
    | Client Secret | OIDC 클라이언트 Secret |
    | Realm | OIDC 클라이언트 Realm |
    | Discovery | OIDC Provider의 Discovery Endpoint를 입력합니다 <br> ex) http://oidcprovider/openid-connect/.well-known/openid-configuration|
    | Introspection Endpoint | Token introspection endpoint를 입력합니다 <br> ex) http://oidcprovider/openid-connect/token/introspect|
    | Bearer Only | OIDC 리다이렉트 없이 토큰만 검사합니다.|
3. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
### Cors
---
Cors는 API 호출 시 Cors 설정을 추가합니다.
1. Cors를 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 Cors의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/cors.png"></img></kbd>
    | 항목  | 설명  |
    |---|---|
    | methods | CORS 설정의 Access-Control-Allow-Methods Header |
    | origins | CORS 설정의 Access-Control-Allow-Origin Header|
3. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
### Proxy Cache
---
API 가 호출되면 응답코드, 콘텐츠 유형, 요청방법을 기반으로 응답을 캐싱합니다. 동일한 요청이 들어오면 메모리에 저장된 리소스를 가져오며 후속 요청에 대한 응답을 다시 캐싱합니다.
설정이 응답 헤더에 x-cache-key, x-cache-status 헤더가 추가되며 x-cache-status로 캐시 상태를 알 수 있습니다.     
| 캐시 상태  | 설명  |
|---|---|
| Miss | Caching된 데이터가 없는 상태 현재 응답을 Caching 합니다. |
| Hit | Caching된 데이터를 가져옴|
| Refresh | Caching 데이터를 가져왔지만 TTL이 만료된 경우|
| Bypass | Caching 할 수 없는 상태|
1. Proxy Cache를 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 Proxy Cache의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/ProxyCache.png"></img></kbd>
    | 항목  | 설명  |
    |---|---|
    | TTL, in seconds, of cache entities | 캐싱된 데이터의 저장시간 해당시간이 지나면 캐싱된 데이터가 삭제됩니다.|
3. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
### Request Transformer
---
Request Transformer는 API 호출 시 Request Header, Body에 특정 데이터를 추가할 수 있습니다.
1. Request Transformer를 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 Request Transformer의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/request.png"></img></kbd>
    - 설정탭에서 데이터를 추가, 삭제 할 수 있습니다.
    - 작성 방식
        | 필드1  |필드2|필드3| 설명  |
        |---|---|---|---|
        | config | remove |headers<br>querystring<br>body|Request에 해당 header, queryString, body가 있으면 삭제합니다. 없으면 무시|
        |        | rename |headers<br>querystring<br>body|Key : Value 형태로 입력합니다. <br>Request에 해당 header, queryString, body가 있으면 이름을 변경합니다. 없으면 무시|
        |        | replace |headers<br>querystring<br>body<br>uri|Request에 해당 header, queryString, body가 있으면 데이터를 대체합니다. 없으면 무시<br>**uri**<br>해당 값으로 Api의 Path를 변경합니다.|
        |        | add |headers<br>querystring<br>body|Key : Value 형태로 입력합니다. <br>Request에 해당 header, queryString, body가 없으면 새로운 데이터를 추가합니다.|
        |        | append |headers<br>querystring<br>body|Key : Value 형태로 입력합니다. <br>Request에 해당 header, queryString, body에 새로운 데이터를 추가합니다. 중복 가능|
    - 예 config.add.headers=h1:v1,h2:v2, config.append.headers=h1:v1,h1:v2
3. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
### Response Transformer
---
Response Transformer는 API 호출 시 Response Header, Body에 특정 데이터를 추가할 수 있습니다.
1. Response Transformer를 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 Response Transformer의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/response.png"></img></kbd>
    - 설정탭에서 데이터를 추가, 삭제 할 수 있습니다.
    - 작성 방식
        | 필드1  |필드2|필드3| 설명  |
        |---|---|---|---|
        | config | remove |headers<br>json|Response에 해당 header, JSON body가 있으면 삭제합니다. 없으면 무시|
        |        | rename |headers|**original_header_name : new_header_name**  형태로 입력합니다. <br>Response에 해당 header가 있으면 헤더 명을 변경합니다. 없으면 무시|
        |        | replace |headers<br>json<br>json_types|**headers, json** <br> header/body명 : 값 형태로 입력합니다.<br> Response에 해당 header, body가 있으면 데이터를 대체합니다. 없으면 무시<br> **json_types**<br> body 명:type 형태로 입력합니다. <br>Response에서 대체할 body의 type를 입력합니다. (number, string)|
        |        | add |headers<br>json<br>json_types|**headers, json** <br> header/body명 : 값 형태로 입력합니다.<br> Response에 해당 header, body가 있으면 데이터를 추가합니다. 없으면 무시<br> **json_types**<br> body 명:type 형태로 입력합니다. <br>Response에서 추가할 body의 type를 입력합니다. (number, string)|
        |        | append |headers<br>json<br>json_types|**headers, json** <br> header/body명 : 값 형태로 입력합니다.<br> Response에 해당 header, body가 있으면 데이터를 추가 합니다. 없으면 무시<br> **json_types**<br> body 명:type 형태로 입력합니다. <br>Response에서 추가할 body의 type를 입력합니다. (number, string)|
    - 예 config.add.json=p1:v1,p2=v2, config.add.json_types=p1:string
3. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
### Http Log
---
Http Log는 API 호출 시 설정된 Http 서버로 요청, 응답 로그를 전송합니다.
1. Http Log를 설정할 Api의 Api 상세페이지로 이동하여 Policy 수정버튼을 클릭합니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy2.png"></img></kbd>
2. 미적용 탭에서 Http Log의 Plus 버튼을 클릭하여 적용합니다.
<kbd><img style="width:100%" src="./img/Policy/HttpLog.png"></img></kbd>
    | 항목  | 설명  |
    |---|---|
    | HTTP Endpoint for Sending Log | 로그를 전송할 Http 서버 Endpoint|
    | HTTP Method for HTTP Endpoint | Http 서버 Endpoint의 Method|
3. Api 상세 페이지에서 배포버튼을 클릭하여 Api를 배포하면 정책이 적용됩니다.
<kbd><img style="width:100%" src="./img/Policy/ApiPolicy5.png"></img></kbd>
---
## Api 기본정책 설정
신규 API가 생성될 때, 기본으로 적용될 공통 API 정책을 설정합니다. 
1. APIM 관리 -> APIM 기본 정책 메뉴로 이동합니다.
<kbd><img style="width:100%" src="./img/Policy/PolicyInit.png"></img></kbd>
2. Plus/Minus 버튼으로 적용/미적용, 정책 클릭 시 세부 설정이 가능합니다. 
