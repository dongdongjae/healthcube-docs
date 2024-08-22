## Create Wallet

Parameta 서비스 User의 wallet을 만듭니다.  
network_info_id가 2인 `lisbon` network에 `wallet name`으로 wallet을 만듭니다.

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
>             "wallet_name": "my wallet",
>             "network_info_id": 2,
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
>             "wallet_id": 93,
>             "wallet_address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
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
>   "result": "0xe321a11a00278d739d3c8430b2dc6917361b86a42566a8615338aa14efcbe806"
> }
> ```

## Coin Balace (추후 변경 예정)

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
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "wallet_address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
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
>   "wallet_id": 93,
>   "network_id": "0x2",
>   "network_name": "lisbon",
>   "result": {
>        "stake": "0x0",
>        "unstakes": []
>       }
> }
> ```

<br />
