현재 사용자의 정보를 조회합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/users/me' \
> -H 'Content-Type: application/json' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -d '{
> "id": 1,
> "name": "홍길동"
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
 > "id" : 1,
>  "project_code": "snuh-healthcube",
>  "name": "홍길동",
>  "birthdate": "1990-01-01",
>  "sex": "남성",
>  "phone": "010-1234-5678"
> }
>
> ```

<br />
