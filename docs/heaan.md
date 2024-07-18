# Heaan(동형암호 분석)

!!! note
    데이터를 암호화할 때 반드시 서버에서 전달받은 `Encryption key`를 사용해야합니다.

## Encryption key 조회

동형 암호 Encryption key를 조회합니다.  
클라이언트는 조회한 Encryption key를 이용하여 데이터를 암호화합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/heaan/enckey' \
> -H 'Content-Type: application/json' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -d '{
> "id": "1"
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>  "enckey": "AAAAAN...kandKQ=" // Base64-encoded data
> }
>
> ```

## 동형암호 샘플 데이터 조회

동형 암호 샘플 데이터를 조회합니다.  
샘플 데이터는 아래 타입을 선택하여 조회할 수 있습니다.

    (1) 남성 데이터 : male
    (2) 여성 데이터 : female
    (3) 동형암호로 암호화된 남성 데이터 : enc_male
    (4) 동형암호로 암호화된 여성 데이터 : enc_female

### 남성 데이터

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/heaan/sample' \
> -H 'Content-Type: application/json' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -d '{
> "id": "1",
> "data_type : "male"
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>  "sample_data": [0, 53, 110, ... , 0, 0]
> }
>
> ```

### 여성 데이터

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/heaan/sample' \
> -H 'Content-Type: application/json' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -d '{
> "id": "1",
> "data_type : "female"
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>  "sample_data": [1, 68, 130, ... , 0, 0]
> }
>
> ```

### 암호화된 남성 데이터

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/heaan/sample' \
> -H 'Content-Type: application/json' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -d '{
> "id": "1",
> "data_type : "enc_male"
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>  "sample_data": "07mcX...2AQAA"" // Base64-encoded data
> }
>
> ```

### 암호화된 여성 데이터

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/heaan/sample' \
> -H 'Content-Type: application/json' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -d '{
> "id": "1",
> "data_type : "enc_female"
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>  "sample_data": "07mcX..FAAAA" // Base64-encoded data
> }
>
> ```

## 동형암호 기반 CVD 위험도 계산

동형암호로 암호화된 데이터를 전달하여 CVD 위험도를 계산합니다.  
`calc_step`에 `result`, `y`, `risk` 중 하나를 입력하면 해당 단계까지 계산된 값을 얻을 수 있습니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/heaan/ana/cvd' \
> -H 'Content-Type: application/json' \
> -H 'Authorization: Bearer eyJhbG...kDW8' \
> -d '{
> "id": "1",
> "sex : "male"
> "calc_step : "result"
> "enc_data : 동형암호로 암호화된 데이터(Base64-encoded data)
> }'
> ```

> Response:
>
> ```http
> HTTP/1.1 200 OK
> Content-Type: application/json
>
> {
>  "res_cal": 0.762...
> }
>
> ```

<br />
