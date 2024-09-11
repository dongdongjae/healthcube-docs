## Create DID

User의 DID를 생성합니다.  
`kid`는 DID의 public key ID 입니다.

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
>         "action": "did-create",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "kid": "my_did"
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
>   "id": 9781,
>   "did": "did:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9",
>   "kid": "battery",
>   "algorithm": "ES256K",
>   "user_id": 101,
>   "network_info_id": 2
> }
> ```

## DID Info

DID 정보를 요청합니다.

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
>         "action": "did-info",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "did": "did:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9"
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
>   "did": "did:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9",
>   "user_id": 101,
>   "network_id": "0x2",
>   "did_did_keys": [...]
> }
> ```

## My All DID Info

사용자의 모든 DID 정보를 요청합니다.

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
>         "action": "did-info-my-all",
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
>    "items": [
>        {
>            "id": "did:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9",
>            "user_id": 101,
>            "network_info_id": 2,
>            "did_did_keys": "did_did_keys": [...]
>        },
>
>        ...
>
>    ],
>    "total": 10,
>    "limit": 100,
>    "offset": 0
> }
> ```

<br />