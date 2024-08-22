## Login

Parameta 서비스 계정 정보로 로그인을 합니다.

1. 파라메타 계정으로 로그인  
   `request.param.type`을 `parameta`로 지정하여 요청합니다.

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
   >         "action": "sign-in",
   >         "param": {
   >             "type": "parameta",
   >             "user_info": {
   >                 "username": "user0001@healthcube",
   >                 "password": "user0001athealthcube"
   >             }
   >         },
   >         "faucet": "yes"
   >        }
   >     }'
   > ```

   > Response:
   >
   > ```http
   > HTTP/1.1 200 OK
   > Content-Type: application/json
   >
   > {
   >   "access_token": "eyJ0eX...sg2vBI",
   >   "token_type": "bearer",
   >   "username": "user0001@healthcube",
   >   "password": "user0001athealthcube"
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
>         "action": "user-info",
>         "param": {
>             "token": "eyJhbGciOiJIU..."
>         },
>        "faucet": "yes"
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
>   "email" : "user0001@healthcube",
>   "is_active" : true,
>   "is_superuser" : false,
>   "id" : 9429,
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
>         "action": "net-info",
>         "param": {
>             "token": "eyJhbGciOiJIU..."
>         },
>        "faucet": "yes"
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
>           "network_id" : "0x1",
>           "network_name" : "icon",
>           "endpoint_url": "https://ctz.solidwallet.io",
>           "chain_name": "icon",
>           "id": 1
>         },
>         {
>           "network_id" : "0x2",
>           "network_name" : "lisbon",
>           "endpoint_url": "https://lisbon.net.solidwallet.io",
>           "chain_name": "icon",
>           "id": 2
>         },
>           ...
>   ],
>   "total" : 6,
>   "limit" : 50,
>   "offset" : 0
> }
> ```

<br />
