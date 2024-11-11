## Create Wallet

Parameta 서비스 User의 wallet을 `wallet name`으로 만듭니다.

Wallet 생성 요청 시, 서버에서 생성한 wallet이 있다면 해당 wallet을 사용자에게 전달합니다.

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
>         "action": "wallet-create",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_name": "my wallet"
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
>   "name" : "my wallet",
>   "id": 93,
>   "network_info_id": 2,
>   "secret_id": 147,
>   "address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
>   "user_id": 101
> }
> ```

## Wallet Info

wallet의 정보를 조회합니다.

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
>         "action": "wallet-info",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93
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
>   "name" : "my wallet",
>   "id": 93,
>   "network_info_id": 2,
>   "secret_id": 147,
>   "address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
>   "user_id": 101
> }
> ```

## Request Coin

`dev`계정으로부터 코인을 받습니다.  
`receiver_wallet_address`는 코인을 받는 wallet의 주소입니다.

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
>         "action": "wallet-icx-request",
>         "param": {
>             "receiver_wallet_address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
>             "coin_value": 1
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
>   "result": "0xe321a11a00278d739d3c8430b2dc6917361b86a42566a8615338aa14efcbe806"
> }
> ```

## Coin Balace

wallet의 코인 잔고를 조회합니다.

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
>         "action": "wallet-icx-balance",
>         "param": {
>             "wallet_id": 93,
>             "wallet_address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
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
>   "result": 6009.6634468875
> }
> ```

<br />
