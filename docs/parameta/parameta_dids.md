# DIDs

## Create DID

User의 DID를 생성합니다. (`kid`: DID의 public key ID)

DID 생성 요청 시, 서버에서 생성한 DID가 있다면 해당 DID을 사용자에게 전달합니다.

**Request:**

```bash
curl -X 'POST' \
  'https://{base_url}/parameta/relay' \
  -H 'Authorization: Bearer eyJhbG...kDW8' \
  -H 'Content-Type: application/json' \
  -d '{
    "id": 1,
    "request": {
        "action": "did-create",
        "param": {
            "token": "eyJhbGciOiJIU...",
            "wallet_id": 93,
            "kid": "my_did"
        },
        "faucet": {
            "req": "yes",
            "net": "lisbon",
            "wallet": "hx5443d0de..."
        }
    }
}'
```

**Response:**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "did:icon:02:1e96d53125b5b9a606a8c643f264a2c08959a8a4cdc9a4ee",
  "user_id": 101,
  "network_info_id": 2,
  "did_did_keys": [
    {
      "id": 9941,
      "did": "did:icon:02:1e96d53125b5b9a606a8c643f264a2c08959a8a4cdc9a4ee",
      "kid": "my_did",
      "algorithm": "ES256K"
    },
    {
      "id": 9942,
      "did": "did:icon:02:1e96d53125b5b9a606a8c643f264a2c08959a8a4cdc9a4ee",
      "kid": "PRE",
      "algorithm": "ES256K"
    }
  ]
}
```

## DID Info

DID 정보를 요청합니다.

**Request:**

```bash
curl -X 'POST' \
'https://{base_url}/parameta/relay' \
-H 'Authorization: Bearer eyJhbG...kDW8' \
-H 'Content-Type: application/json' \
-d '{
    "id": 1,
    "request": {
        "action": "did-info",
        "param": {
            "token": "eyJhbGciOiJIU...",
            "did": "did:icon:02:1e96d53125b5b9a606a8c643f264a2c08959a8a4cdc9a4ee"
        },
        "faucet": {
            "req": "yes",
            "net": "lisbon",
            "wallet": "hx5443d0de..."
        }
    }
}'
```

**Response:**

```http
HTTP/1.1 200 OK
Content-Type: application/json
{
  "id": "did:icon:02:1e96d53125b5b9a606a8c643f264a2c08959a8a4cdc9a4ee",
  "user_id": 101,
  "network_info_id": 2,
  "did_did_keys": [
    {
      "id": 9941,
      "did": "did:icon:02:1e96d53125b5b9a606a8c643f264a2c08959a8a4cdc9a4ee",
      "kid": "dids9",
      "algorithm": "ES256K"
    },
    {
      "id": 9942,
      "did": "did:icon:02:1e96d53125b5b9a606a8c643f264a2c08959a8a4cdc9a4ee",
      "kid": "PRE",
      "algorithm": "ES256K"
    }
  ]
}
```

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
<br />

VC 관련 API를 사용하기 위해서는 parameta service의 Wallet과 DID가 존재해야 합니다.

## Get VC type

VC type 정보를 조회합니다.

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
>         "action": "vct-info",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "vc_id": 3,
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
>  "type": "HealthCubeUserCredential",
>  "verifier_did_key_id": 9869,
>  "issuer_did_key_id": 9869,
>  "vc_context": {
>    "@version": 1,
>    "protected": true,
>    "xsd": "http://schema.org",
>    "schema": "http://schema.org",
>    "healthcube": "https://parametaw.com/healthcube#",
>    "HealthCubeUserCredential": "HealthCubeUserCredential",
>    "userId": "healthcube:researchId"
>  },
>  "service_id": 8,
>  "id": 3
> }
> ```

## Get all VC type

등록된 모든 VC type을 조회합니다.

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
>         "action": "vct-info-all",
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
>  "items": [
>    ... ,
>
>    {
>      "type": "HealthCubeUserCredential",
>      "verifier_did_key_id": 9869,
>      "issuer_did_key_id": 9869,
>      "vc_context": {
>        "@version": 1,
>        "@protected": true,
>        "xsd": "http://schema.org",
>        "schema": "http://schema.org",
>        "healthcube": "https://parametaw.com/healthcube#",
>        "HealthCubeUserCredential": "healthcube:HealthCubeUserCredential",
>        "userId": "healthcube:userId"
>      },
>      "service_id": 8,
>      "id": 3
>    },
>    {
>      "type": "HealthCubeParticipateCredential",
>      "verifier_did_key_id": 9869,
>      "issuer_did_key_id": 9869,
>      "vc_context": {
>        "@version": 1,
>        "@protected": true,
>        "xsd": "http://schema.org",
>        "schema": "http://schema.org",
>        "healthcube": "https://parametaw.com/healthcube#",
>        "userId": "healthcube:userId",
>        "HealthCubeParticipateCredential": "healthcube:HealthCubeParticipateCredential",
>        "researchId": "healthcube:researchId"
>      },
>      "service_id": 8,
>      "id": 4
>    }
>  ]
> }
> ```

## Issue user credential VC

사용자 인증 Owner VC를 발급합니다.

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
>         "action": "ovc-user-issue",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "didkey_id": 9781,
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
>    "vc_id": 3,
>    "label_id": "QmecKsqxSEPGkGuuuZ2JFGE4u9AneHvpto9RCy2UGTfRxP",
>    "tx_hashes": {
>      "issuance_hash": "0x91dc987b2f78e92bb62571a07e95830d53b56c56494a61b8348cb67e2ca9bf99"
>    }
> }
> ```

## Issue research participation consent VC

연구 참여 동의 Owner VC를 발급합니다.

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
>         "action": "ovc-research-issue",
>         "param": {
>             "token": "eyJhbGciOiJIU...",
>             "didkey_id": 9781,
>             "wallet_id": 93,
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
>    "vc_id": 4,
>    "label_id": "QmecKsqxSEPGkGuuuZ2JFGE4u9AneHvpto9RCy2UGTfRxP",
>    "tx_hashes": {
>      "issuance_hash": "0x91dc987b2f78e92bb62571a07e95830d53b56c56494a61b8348cb67e2ca9bf99"
>    }
> }
> ```
