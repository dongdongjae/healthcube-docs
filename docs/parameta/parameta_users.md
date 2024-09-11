## Login

Parameta 서비스 로그인을 합니다.  
로그인은 'parameta' 계정 정보를 사용하는 방법과 'healthcube' 사용자 정보를 사용하는 방법이 있습니다.

1. Parameta 계정 정보를 사용한 로그인  
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
      >               "username": "user0001@healthcube.snu.ac.kr",
      >               "password": "user0001athealthcube"
      >               }
      >             },
      >         "faucet": {
      >             "req": "yes",
      >             "net": "lisbon",
      >             "wallet": "hx5443d0de..."
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
      >   "token_type": "bearer",
      >   "username": "user0001@healthcube.snu.ac.kr",
      >   "password": "user0001athealthcube"
      > }
      > ```  

2. Healthcube 사용자 정보를 사용한 로그인  
   `request.param.type`을 `healthcube`로 지정하여 요청합니다.

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
      >             "type": "healthcube",
      >             "user_info": {
      >                 "name": "홍길동",
      >                 "birthdate": "1990-01-01",
      >                 "sex": "남성",
      >                 "phone": "010-1234-5678"
      >             }
      >         },
      >         "faucet": {
      >             "req": "yes",
      >             "net": "lisbon",
      >             "wallet": "hx5443d0de..."
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
      >   "token_type": "bearer",
      >   "username": "user0001@healthcube.snu.ac.kr",
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
>         "faucet": {
>             "req": "yes",
>             "net": "lisbon",
>             "wallet": "hx5443d0de..."
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
>         "faucet": {
>             "req": "yes",
>             "net": "lisbon",
>             "wallet": "hx5443d0de..."
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
