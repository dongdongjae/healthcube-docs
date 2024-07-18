의료 마이데이터 샘플 파일을 조회합니다.

> Request:
>
> ```bash
> curl -X 'POST' \
> 'https://{base_url}/mydata/sample' \
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
>   "sample": {
>     "entry": [{"resource": ...}],
>     "link" : [...],
>     "id" : "428f3...f0429",
>     "type": "transaction-response",
>     "resourceType": "Bundle"
>   }
> }
> ```

<br />
