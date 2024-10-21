# 연합학습

## 연합학습 기본 모델 조회

연합학습 기본 모델을 조회합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/flower/model' \
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
>  {
>    "basic_model": "HAAAAFRGTD..." // Base64-encoded data
>  }
>
> ```

서버로부터 전달받은 모델은 `.tflite` 형식의 파일입니다.

## 연합학습 샘플 데이터 조회

연합학습 샘플 데이터를 조회합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/flower/sample' \
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
>  {
>    "sample_data": "c2VwYWwgbG..." // Base64-encoded data
>  }
>
> ```

서버로부터 전달받은 샘플 데이터는 `.csv` 형식의 파일입니다.

<br />
