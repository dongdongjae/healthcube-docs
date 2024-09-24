# Parameta(블록체인 서비스)

블록체인 서비스를 요청합니다.  
블록체인 서비스 계정은 [Healthcube 로그인](../token.md) 시에 전달받은 `username`과 `password`를 사용합니다.


```json
{
  "id": 1,
  "request": {
    "action": "sign-in",
    "param": {
      "type": "parameta",
      "user_info": {
        "username": "user0001@healthcube.snu.ac.kr",
        "password": "user0001athealthcube"
      }
    },
    "faucet": {
      "req": "yes",
      "net": "lisbon",
      "wallet": "hx5443d0de..."
    }
  }
}
```

- `id` : Healthcube 로그인 시에 전달받은 사용자 ID
- `action` : 서버에 요청하는 블록체인 서비스에 대한 정의
- `param` : 블록체인 서비스 요청에 사용되는 데이터
- `faucet` : 사용자 wallet coin balance를 확인하여 남은 잔액이 1보다 적은 경우 코인 발급  
    - `faucet.req` : Whether to check the coin balance ("yes" or "no")
    - `faucet.net` : Parameta network name
    - `faucet.wallet` : Parameta user wallet address  


!!! note
    `faucet.req : "no"` 인 경우, 나머지 parameter(net, wallet)는 빈 문자열 값을 넣어서 요청합니다.
    ```json
    "faucet": {
        "req": "no",
        "net": "",
        "wallet": ""
    }
    ```


<br />

### 블록체인 서비스 API 종류

1. Wallet 서비스 [⮕](./parameta_wallet.md)
    - `wallet-create`: Wallet 생성
    - `wallet-info`: Wallet 정보 조회
    - `wallet-icx-request`: Wallet 코인 발급 (관리자 계정에서 전송)
    - `wallet-icx-balance`: Wallet 코인 잔고 조회
2. DID 서비스 [⮕](./parameta_dids.md)
    - `did-create`: DID 생성
    - `did-info`: DID 정보 조회
    - `did-info-my-all`: (사용자)전체 DID 정보 조회
    - `vct-info`: VC type 정보 조회
    - `vct-info-all`: 전체 VC type 정보 조회
    - `ovc-user-issue`: 사용자 인증 Owner VC 발급
    - `ovc-research-issue`: 연구참여 동의 Owner VC 발급
3. PDS 서비스 [⮕](./parameta_pds.md)
    - `pds-up-enc`: PDS 데이터 암호화 업로드
    - `pds-policy-add`: PDS 정책 추가 (제3자에 권한 부여: 데이터 사용 동의)
    - `pds-policy-rm`: PDS 정책 삭제 (제3자의 권한 삭제 : 데이터 사용 동의 철회)
    - `pds-down`: PDS 데이터 조회 (복호화 키, 다운로드 링크)
    - `pds-list`: PDS 데이터 목록 조회
4. 블록체인 서비스 연결, 정보 조회 등 [⮕](./parameta_users.md)
    - `sign-in` : 서비스 로그인
    - `user-info` : 서비스 사용자 정보 조회
    - `net-info` : 서비스 Network 정보 조회

<br />
