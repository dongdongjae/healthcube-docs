# Home

Healthcube 서버에서 제공하는 API에 대한 사용자 가이드를 제공합니다.

### Base URL

https://healthcube.snu.ac.kr

### healthcube API docs

https://healthcube.snu.ac.kr/docs

!!! note
    `healthcube.snu.ac.kr`은 이하 {base_url}으로 사용합니다.

<br />

<span style="font-size: 0.8em;">11월 14일 업데이트</span>  
<span style="font-size: 0.8em; padding-left: 15px;">1. `/parameta/relay` api의 `pds-policy-add`, `pds-up-enc` 요청 파라미터가 변경되었습니다.</span>  
<span style="font-size: 0.7em; padding-left: 30px;">- `pds-policy-add` : threshold, proxy_count, expire_at을 더 이상 받지 않습니다.</span>  
<span style="font-size: 0.7em; padding-left: 30px;">- `pds-up-enc`: category, replication_min, replication_max을 더 이상 받지 않습니다.</span>
<br />
<span style="font-size: 0.8em;">11월 11일 업데이트</span>  
<span style="font-size: 0.8em; padding-left: 15px;">1. 사용자 인증 및 연구참여 동의 VC 발급 API 요청 시 header에 토큰을 받지 않도록 변경되었습니다.</span>  
<br />
<span style="font-size: 0.8em;">11월 6일 업데이트</span>  
<span style="font-size: 0.8em; padding-left: 15px;">1. 시나리오에 맞게 로그인 과정 수정되었습니다.</span>  
<span style="font-size: 0.8em; padding-left: 15px;">2. wallet과 did 생성 요청 시, 서버에서 생성한 것이 있다면 새로운 wallet과 did가 생성되지 않습니다.</span>  
<span style="font-size: 0.8em; padding-left: 15px;">3. `wallet-info`(wallet 정보 조회) 요청 파라미터에서 `wallet_address`를 받지 않도록 변경되었습니다.</span>  
<span style="font-size: 0.8em; padding-left: 15px;">4. 사용자 인증 및 연구 참여 동의 VC발급 시 요청 파라미터에서 `vc_id`, `username`을 받지 않도록 변경되었습니다.</span>  
<span style="font-size: 0.8em; padding-left: 15px;">5. DID 생성 및 조회 응답 값이 변경되었습니다.</span>  
