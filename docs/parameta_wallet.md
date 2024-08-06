# Parameta(블록체인 서비스)

블록체인 서비스를 요청합니다.

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
>         "action": "create_wallet",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_name": "my wallet",
>             "network_info_id": 2,
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
>         "action": "wallet_info",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "wallet_address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
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

## Get Coin

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
>         "action": "request_coin",
>         "param": {
>             "receiver_wallet_address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
>             "coin_value": 1
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
>   "wallet_id": 93,
>   "network_id": "0x2",
>   "network_name": "lisbon",
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
>         "action": "coin_balance",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "wallet_address": "hxc3a9ed829a552f543f4447ca8c8f482cadb3d3e3",
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
>   "wallet_id": 93,
>   "network_id": "0x2",
>   "network_name": "lisbon",
>   "result": {
>        "stake": "0x0",
>        "unstakes": []
>       }
> }
> ```

## Coin Transfer

나의 wallet에 있는 코인을 다른 wallet으로 입금합니다.  
`wallet_id`는 전송하는 wallet의 id이며, `receiver_wallet_address`는 코인을 받는 wallet의 주소입니다.

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
>         "action": "transfer_tx",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "receiver_wallet_address": "hx0b68950d744654aad004a9ac5375f7d1370a43c4",
>             "coin_value": 1
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
>   "wallet_id": 93,
>   "network_id": "0x2",
>   "network_name": "lisbon",
>   "result": "0xeff55acc46ed9f267a19c379e01bcaec2e8c82841b28ae0749bbdb9308d5982e"
> }
> ```

## Coin Transfer with Message

나의 wallet에 있는 코인과 message를 함께 전달합니다.  
`wallet_id`는 전송하는 wallet의 id이며, `receiver_wallet_address`는 코인을 받는 wallet의 주소입니다.

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
>         "action": "message_tx",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "receiver_wallet_address": "hx0b68950d744654aad004a9ac5375f7d1370a43c4",
>             "coin_value": 1,
>             "message" : "my message"
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
>   "wallet_id": 93,
>   "network_id": "0x2",
>   "network_name": "lisbon",
>   "result": "0x541b18cda8b33509d7c9d1fda30fe8d30e1126eeb4a0d0d873698917f409d128"
> }
> ```

## Get Transaction Result

txhash 로 transaction result 를 조회합니다.

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
>         "action": "tx_info",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "txhash": "0x541b18cda8b33509d7c9d1fda30fe8d30e1126eeb4a0d0d873698917f409d128"
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
>   "wallet_id": 93,
>   "network_id": "0x2",
>   "network_name": "lisbon",
>   "result": {...},
>   "id": 1720591364
> }
> ```

<br />
