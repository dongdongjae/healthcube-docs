사용자의 정보를 이용하여 로그인을 합니다.

로그인 요청 시, 사용자의 PARAMETA-W 계정 및 Wallet, DID가 없는 경우에는 서버에서 생성하여 사용자에게 전달합니다.

사용자의 PARAMETA-W 계정에 대해 **사용자 인증** 및 **연구참여 동의** VC가 발급되어 있지 않은 경우에는 Healthcube Server의 token이 발급되지 않습니다.(모두 등록이 되어 있어야 token을 얻을 수 있습니다.)

**Request:**

```bash
curl -X 'POST' \
  'https://{base_url}/token' \
  -H 'Content-Type: application/json' \
  -d '{
    "project_code": "snuh-healthcube",
    "name": "홍길동",
    "birthdate": "1990-01-01",
    "sex": "남성",
    "phone": "010-1234-5678"
}'
```

**Response:**

```json
{
  "id": 1,
  "name": "홍길동",
  "parameta_info": {
    "username": "user0001@healthcube.snu.ac.kr",
    "password": "user0001athealthcube",
    "wallets": {
      "name": "user0001@healthcube.snu.ac.kr",
      "id": 9451,
      "network_info_id": 2,
      "secret_id": 10369,
      "address": "hxd28c384e489722da95a90b52dfcce8aa6f7626bd",
      "user_id": 9436
    },
    "dids": {
      "id": "did:icon:02:7d9fa35fde5c6b13532cd3423a73036336c13bf75b3b1db6",
      "user_id": 9436,
      "network_info_id": 2,
      "did_did_keys": [
        {
          "id": 9919,
          "did": "did:icon:02:7d9fa35fde5c6b13532cd3423a73036336c13bf75b3b1db6",
          "kid": "user0001@healthcube.snu.ac.kr",
          "algorithm": "ES256K"
        },
        {
          "id": 9920,
          "did": "did:icon:02:7d9fa35fde5c6b13532cd3423a73036336c13bf75b3b1db6",
          "kid": "PRE",
          "algorithm": "ES256K"
        }
      ]
    }
  },
  "parameta_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJ1c2VyMDAwMUBoZWFsdGhjdWJlLnNudS5hYy5rciIsInBlcm1pc3Npb25zIjoidXNlciIsImV4cCI6MTczMDk0MDIyMH0.o1JmvhCN1dj-xMh82Z6kkA1Ddm4N0r3t30YaNQJ7RwE",
  "vc_status": {
    "is_user_credential": true,
    "is_research_participation": true
  },
  "detail": "Login successful on 'Healthcube'"
}
```

- `parameta_info`: 파라메타 계정 정보
    - `username`: 파라메타 계정 아이디
    - `password`: 파라메타 계정 비밀번호
    - `wallets`: 사용자의 wallet 정보
    - `dids`: 사용자의 did 정보
- `parameta_token`: 파라메타 계정 토큰
- `vc_status`: VC 상태 정보
    - `is_user_credential`: 사용자 정보 VC 발급 상태
    - `is_research_participation`: 연구참여 동의 VC 발급 상태

<br />


<!-- 로그인 요청한 사용자의 PARAMETA-W 게정이 있는지 확인합니다. (PARAMETA-W 계정이 없는 경우 서버에서 계정 및 Wallet, DID 생성)
PARAMETA-W 계정에 대해 사용자 인증 및 연구참여 동의 VC 검증이 되어 있는지 확인합니다.  -->

<!-- > Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/token' \
> -H 'Content-Type: application/json' \
> -d '{
> "project_code": "snuh-healthcube",
> "name": "홍길동",
> "birthdate": "1990-01-01",
> "sex": "남성",
> "phone": "010-1234-5678"
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
> Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NTI2MjcyNTYsImlhdCI6MTcyMTA5MTI1Niwic2NvcGUiOiJhY2Nlc3NfdG9rZW4iLCJkYXRhIjp7ImlkIjoxfX0.sLkFUre8YlnZOC9rknmSvXZ85-9D2_yvZz-CqZPkDW8
>
> {
>  "id": 1,
>  "name": "홍길동",
>  "detail": "User login successful",
>  "parameta": {
>    "username": "user0001@healthcube",
>    "password": "user0001athealthcube"
>   }
> }
>
> ```
>
> `parameta.username`과 `parameta.password`는 Parameta API 로그인 할 때 사용되는 사용자 정보입니다. -->