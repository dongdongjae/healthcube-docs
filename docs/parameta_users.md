# Parameta(블록체인 서비스)

블록체인 서비스를 요청합니다.

## Sign up

Parameta 서비스 계정을 생성합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/parameta/relay' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -H 'Content-Type: application/json' \
> -d '{
>     "id": 1,
>     "request": {
>         "action": "signup",
>         "param": {
>             "username": "test01@healthcube",
>             "password": "pass01@healthcube"
>         }
>     }
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>   "access_token": "eyJ0eX...sg2vBI",
>   "token_type": "bearer"
> }
> ```

## Login

Parameta 서비스 계정 정보로 로그인을 합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/parameta/relay' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -H 'Content-Type: application/json' \
> -d '{
>     "id": 1,
>     "request": {
>         "action": "login",
>         "param": {
>             "username": "test01@healthcube",
>             "password": "pass01@healthcube"
>         }
>     }
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>   "access_token": "eyJ0eX...sg2vBI",
>   "token_type": "bearer"
> }
> ```

## User Info

Parameta 서비스의 계정 정보를 조회합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/parameta/relay' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -H 'Content-Type: application/json' \
> -d '{
>     "id": 1,
>     "request": {
>         "action": "user_info",
>         "param": {
>             "token": "eyJhbGciOiJIU..."
>         }
>     }
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>   "email" : "test01@healthcube",
>   "is_active" : true,
>   "is_superuser" : false,
>   "id" : 101,
>   "wallets" : [...],
>   "dids" : [...]
> }
> ```

## Net Info

Parameta 서비스의 네트워크 정보를 조회합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/parameta/relay' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -H 'Content-Type: application/json' \
> -d '{
>     "id": 1,
>     "request": {
>         "action": "net_info",
>         "param": {
>             "token": "eyJhbGciOiJIU..."
>         }
>     }
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>   "items" : [
>         {
>             "network_id" : "0x1",
>             "network_name" : "icon",
>             "endpoint_url": "https://ctz.solidwallet.io",
>             "id": 1
>         },
>           ...
>       ]
> }
> ```

<br />
