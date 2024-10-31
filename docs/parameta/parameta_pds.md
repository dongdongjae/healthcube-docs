## Data Upload

사용자의 파일을 PDS에 암호화 하여 올립니다.  
`label_id`는 임의로 생성할 수 있으나 Url Safe 해야 하며, PDS 내에서 유일한 값을 가져야 합니다.

> Param Form:

| KEY             | TYPE   | DESCRIPTION                  |
| --------------- | ------ | ---------------------------- |
| token           | string | 파라메타 로그인 토큰         |
| file            | string | 업로드 파일 (Base 64 format) |
| file_name       | string | 업로드 파일 명               |
| wallet_id       | int    | 사용할 wallet ID             |
| did             | string | 사용할 DID                   |
| label_id        | string | 데이터를 구분할 label_id     |
| replication_max | int    | BFS에서 복사본 수 최대값     |
| replication_min | int    | BFS에서 복사본 수 최소값     |
| category        | string | 파일을 분류할 카테고리       |

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
>         "action": "pds-up-enc",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "file": "/9j/4AAQSkZJR...",
>             "file_name": "upload_file.json",
>             "wallet_id": 93,
>             "did": "id:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9",
>             "label_id": "test_label_id",
>             "replication_max": 1,
>             "replication_min": 1,
>             "category": "vc"
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
>   "wallet_id": 93,
>   "replication_min": 1,
>   "replication_max": 1,
>   "label_id": "test_label_id",
>   "capsule_cid": "QmTUM2...",
>   "data_cid": "QmVRDE...",
>   "pinned": True,
>   "txhash": "0x9c0c...",
> }
> ```

## Add Policy

PDS Data를 다운로드 할 수 있는 사용자 정책을 등록합니다.  

> Param Form:

| KEY          | TYPE   | DESCRIPTION                                          |
| ------------ | ------ | ---------------------------------------------------- |
| token        | string | 파라메타 로그인 토큰                                 |
| wallet_id    | int    | 사용자 wallet ID                                     |
| owner_did    | string | Label 소유자의 DID                                   |
| label_id     | string | Label ID (PDS DATA IDentifier)                       |
| policy_name  | string | Policy 이름                                          |
| threshold    | int    | PRE 의 Threshold 값                                  |
| proxy_count  | int    | PRE 에서 사용할 Proxy Node 수                        |
| expire_at    | string | Policy 유효 기간 timestamp seconds, 예) "1767139200" |

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
>         "action": "pds-policy-add",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "label_id": "test_label_id",
>             "policy_name": "test_policy",
>             "owner_did": "did:icon:02:06ed65bb5b4d8b1afa754c824484e2da4c39225231c8bf67",
>             "threshold": 1,
>             "proxy_count": 1,
>             "expire_at": "1767139200"
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
>   "policy_id": "3FBa8..."
> }
> ```
>
> 반환된 `policy_id`는 PDS 다운로드 정책 ID 입니다.

## Remove Policy

등록한 PDS 사용자 정책을 삭제합니다.

> Param Form:

| KEY       | TYPE   | DESCRIPTION          |
| --------- | ------ | -------------------- |
| token     | string | 파라메타 로그인 토큰 |
| wallet_id | int    | 사용자 Wallet ID     |
| policy_id | string | PDS 다운로드 정책 ID |

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
>         "action": "pds-policy-rm",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "wallet_id": 93,
>             "policy_id": "3FBa8..."
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
>   "policy_id": "3FBa8..."
> }
> ```

## Data Request

암호화 된 PDS Data를 복호화 할 수 있는 `key_base`와 Data를 다운로드할 수 있는 링크를 받습니다.

> Param Form:

| KEY       | TYPE   | DESCRIPTION                |
| --------- | ------ | -------------------------- |
| token     | string | 파라메타 로그인 토큰       |
| label_id  | string | 다운받을 PDS Data Label ID |
| did       | string | 다운받을 사용자의 DID      |
| wallet_id | int    | 사용자 Wallet ID           |

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
>         "action": "pds-down",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "label_id": "test_label_id",
>             "did": "id:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9",
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
>   "wallet_id": 93,
>   "key_base": "4d90d9...",
>   "data_cid": "QmWB3T...",
>   "download_link": "http://perme-bfs-dev.icon...",
> }
> ```
>
> !!! note
    다운로드 된 데이터는 암호화 되어 있으며, `key_base` 값을 이용하여 복호화 하여야 합니다.  
    <a href="https://github.com/perme-io/chacha20_decryption_example" target="_blank">데이터복호화 Java Sample</a>

## Data List

PDS 데이터 목록을 조회합니다.

> Param Form:

| KEY    | TYPE   | DESCRIPTION          |
| ------ | ------ | -------------------- |
| token  | string | 파라메타 로그인 토큰 |
| did    | string | 사용할 DID           |
| limit  | int    | 최대 항목 수         |
| offset | int    | 시작 위치            |

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
>         "action": "pds-list",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "did": "id:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9",
>             "limit": 50,
>             "offset": 0,
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
>   "items": [
>       {
>        "pds_label_id" : "test_label_id",
>        "owner_did" : "id:icon:02:e18516c6adb5ac79e014d98ea0b29573d7dc50a92663c8a9",
>        "category" : "vc"
>       },
>       ...
>   ]
> }
> ```

<br />
