# Parameta(블록체인 서비스)

블록체인 서비스를 요청합니다.

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
>         "action": "create_did",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "kid": "my_did"
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

## DID info

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
>         "action": "did_info",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "did": "did:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9"
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

<br />
