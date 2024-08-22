계정 정보를 사용하여 로그인을 합니다.

> Request:
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
> `parameta.username`과 `parameta.password`는 Parameta API 로그인 할 때 사용되는 사용자 정보입니다.

<br />

