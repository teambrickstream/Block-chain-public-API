# Blockchain API Explanation Document
Ver 1.11<br />
[Blockchain Explorer](http://search.glueapp.net)


## 1. API 서버 기본 개요
<ul>
  <li>
    ■ 블록체인 API 서버 (이하 API 서버) 기본 정보
    
    API Server Address :
    http://api.glueapp.net/
  </li>
  
  <li>
    ■ API 서버 지원 코인 종류
  
  |Symbol|Decimal|
  |------|---|
  |ETH|Decimal 18|
  |BTC|Decimal 8|
  |EOS|Decimal 18|
  |Klay|Decimal 18|
  |Tron|Decimal 18|
  </li>
</ul>

## 2. 블록체인 API 구성
### 2.1 블록체인 별 블록 생성 조회
<ul>
  <li>
    ■ REQUEST State :<br />
      &nbsp;http://URL/dashboard/[ctype]<br /><br />
    ■ Form :

      ETHEREUM
      {
          Request :
          http://URL/dashboard/eth

          Response :    
      }

      KLAYTN
      {
          Request :
          http://URL/dashboard/klaytn
      }

      BTC
      {
          Request :
          http://URL/dashboard/btc
      }

      EOS
      {  
          Request :
          http://URL/dashboard/eos
      }
  </li>
</ul>

### 2.2 블록체인 정보 조회
<ul>
  <li>
    ■ 주소, TX Hash 값으로 해당 블록체인 메인넷의 정보 조회<br />
  </li><br />
  
  <li>
    ■ REQUEST Common Information<br />
    &nbsp;: http://URL/information/any=[address|account|hash]
  </li><br />
  
  <li>
    ■ 이더리움, 클레이튼, 비트코인, 이오스 주소로 정보 조회<br />
    &nbsp;: http://URL/information?any=계정주소
  </li><br />
  
  <li>
    ■ 이더리움, 클레이튼, 비트코인, 이오스 Tx Hash로 정보 조회<br />
    &nbsp;: http://URL/information?any=hash
  </li><br />
  
  <li>
    ■ 검색 정보 옵션<br />
    &nbsp;: ex) http://URL/information?any=[계정주소][&ctype=eos&][&eos_limit=20][&eos_cursor=]

  |Parameter|설명|
  |------|---|
  |ctype=[symbol]|입력한 계정주소가 symbol에 해당하는 주소임을 정의|
  |[symbol]_limit=[number]|Symbol의 action 정보를 number 개수만큼 조회|
  |[symbol]_cursor=|Action의 cursor 값으로 Action을 검색|
  </li><br />
  
  <li>
    ■ Form
  
    ETHEREUM
    {
        Request Address :
        http://URL/information?any=0x95216B0CC9110B22824Deaa968b215B4C3DD09f8
        http://URL/information?any=0x95216B0CC9110B22824Deaa968b215B4C3DD09f8[&ctype=eth]
        http://URL/information?any=0x95216B0CC9110B22824Deaa968b215B4C3DD09f8[&ctype=eth][&startblock=0][&endblock=9999999]

        Request Hash :
        http://URL/information?any=0x2304c59c30c3e83c811e143b54c074cd202c0e3d3f07debeac9c5ff2662dbc3e[&ctype=eth]
    }

    KLAYTN
    {
        Request Address :
        http://URL/information?any=0x386ca3cb8bb13f48d1a6adc1fb8df09e7bb7f9c8[&ctype=klaytn][&page=1][&size=20]

        Request Hash :
        http://URL/information?any=0x1d59fed3bb8ab799faa68cf93dccd1e5ea64c0bb7d2e2eb0791ab538f94cfa8d[&ctype=klaytn]
    }

    BTC
    {
        Request Address :
        http://URL/information?any=35hK24tcLEWcgNA4JxpvbkNkoAcDGqQPsP[&ctype=btc][&btc_offset=0][&btc_limit=20]

        Request Hash :
        http://URL/information?any=0x1d59fed3bb8ab799faa68cf93dccd1e5ea64c0bb7d2e2eb0791ab538f94cfa8d[&ctype=btc]
    }

    EOS
    {   
        Request Account :
        http://URL/information?any=glueaccount1[&ctype=eos][&eos_limit=20][&eos_cursor=]

        Request Hash :
        http://URL/information?any=752bb4b068fc8bff74ffa5c471b0bba3624804c7bfca31b797332779c038d178[&ctype=eos]
    }

  </li><br />
</ul>


## 2.3 블록체인 별 주소로 정보 조회
<ul>
  <li>
    ■ REQUEST Balance<br />
      : http://URL/balance/[address| account]
  </li><br />
  
  <li>
    ■ Result Parameter<br />
      
  |Parameter|설명|
  |------|---|
  |Allow|주소 조회 결과 성공/실패|
  |[symbol]|주소의 블록체인 메인넷 표시<br />해당 주소의 밸런스 표시|
  </li><br />
</ul>



현재 지원 코인
---
<ul>
  <li><img width="16" src="http://search.glueapp.net/icon_coin/i_klaytn.png" /> KLAYTN</li>
  <li><img width="16" src="http://search.glueapp.net/icon_coin/i_eth.png" /> ETH</li>
  <li><img width="16" src="http://search.glueapp.net/icon_coin/i_btc.png" /> BTC</li>
  <li><img width="16" src="http://search.glueapp.net/icon_coin/i_eos.png" /> EOS</li>
</ul>


현재 지원 타입
---
<ul>
  <li>Address</li>
  <li>Txhash</li>
</ul>


@http://URL


***: REQUEST Common Information***
http://URL/information/any=[address|account|hash]

요약 - 주소 및 hash 로 잔액, transaction 정보를 조회 합니다.

<ul>
  <li>
  이더리움, 클레이튼, 비트코인, 이오스의 주소(계정)로 잔액 및 정보를 조회합니다.

    http://URL/information?any=계정주소
  </li>

  <li>
  이더리움, 클레이튼, 비트코인, 이오스의 hash로 transaction 및 action 정보를 조회합니다.

    http://URL/information?any=hash
  </li>

  <li>
  추가로 옵션을 주어서 정보 검색을 컨트롤 할수 있습니다.

    http://URL/information?any=이오스계정[&ctype=eos&][&eos_limit=20][&eos_cursor=]

    ctype=eos : any의 계정이 eos주소임을 알려줍니다.
    eos_limit=20 : 계정의 action정보를 20개까지 가져옵니다.
    eos_cursor=index : 이오스 계정의 action의 cursor값으로 다음 action들을 추가 검색 하게 합니다.
  </li>
</ul>
    
<br><br><br>

<img width="20" src="http://search.glueapp.net/icon_coin/i_eth.png">***ETHEREUM***

    Request Address :
    http://URL/information?any=0x95216B0CC9110B22824Deaa968b215B4C3DD09f8

    http://URL/information?any=0x95216B0CC9110B22824Deaa968b215B4C3DD09f8[&ctype=eth]

    http://URL/information?any=0x95216B0CC9110B22824Deaa968b215B4C3DD09f8[&ctype=eth] [&startblock=0][&endblock=9999999]

    Request Hash :
    http://URL/information?any=0x2304c59c30c3e83c811e143b54c074cd202c0e3d3f07debeac9c5ff2662dbc3e[&ctype=eth]

<img width="20" src="http://search.glueapp.net/icon_coin/i_klaytn.png">***KLAYTN***

    Request Address :
    http://URL/information?any=0x386ca3cb8bb13f48d1a6adc1fb8df09e7bb7f9c8[&ctype=klaytn][&page=1][&size=20]

    Request Hash :
    http://URL/information?any=0x1d59fed3bb8ab799faa68cf93dccd1e5ea64c0bb7d2e2eb0791ab538f94cfa8d[&ctype=klaytn]


<img width="20" src="http://search.glueapp.net/icon_coin/i_btc.png">***BTC***

    Request Address :
    http://URL/information?any=35hK24tcLEWcgNA4JxpvbkNkoAcDGqQPsP[&ctype=btc][&btc_offset=0][&btc_limit=20]

    Request Hash :
    http://URL/information?any=0x1d59fed3bb8ab799faa68cf93dccd1e5ea64c0bb7d2e2eb0791ab538f94cfa8d[&ctype=btc]


<img width="20" src="http://search.glueapp.net/icon_coin/i_eos.png">***EOS***

    Request Account :
    http://URL/information?any=glueaccount1[&ctype=eos][&eos_limit=20][&eos_cursor=]

    Request Hash :
    http://URL/information?any=752bb4b068fc8bff74ffa5c471b0bba3624804c7bfca31b797332779c038d178[&ctype=eos]

---
<br><br><br>

***: REQUEST State***
http://URL/dashboard/[ctype]

요약 - 각 코인별 최근 블록 생성 정보 조회
<br>

<img width="20" src="http://search.glueapp.net/icon_coin/i_eth.png">***ETHEREUM***

    Request :
    http://URL/dashboard/eth

    Response :    

<img width="20" src="http://search.glueapp.net/icon_coin/i_klaytn.png">***KLAYTN***

    Request :
    http://URL/dashboard/klaytn


<img width="20" src="http://search.glueapp.net/icon_coin/i_btc.png">***BTC***

    Request :
    http://URL/dashboard/btc

<img width="20" src="http://search.glueapp.net/icon_coin/i_eos.png">***EOS***

    Request :
    http://URL/dashboard/eos


---
<br><br><br>


***: REQUEST Balance***
http://URL/balance/[address| account]

요약 - 각 코인별 주소(계정)로 잔액을 조회 합니다.

<img width="20" src="http://search.glueapp.net/icon_coin/i_eth.png">***ETHEREUM***

    Reqeust :
    http://URL/balance/0x829BD824B016326A401d083B33D092293333A830

    Response :
    {
        "allow": true,
        "eth": "4368.119903933051574229",
        "klaytn": "0"
    }

<img width="20" src="http://search.glueapp.net/icon_coin/i_klaytn.png">***KLAYTN***

    Reqeust :
    http://URL/balance/0x386ca3cb8bb13f48d1a6adc1fb8df09e7bb7f9c8

    Response :
    {
        "allow": true,
        "eth": "0",
        "klaytn": "0.999474999999999999"
    }

<img width="20" src="http://search.glueapp.net/icon_coin/i_btc.png">***BTC***

    Reqeust :
    http://URL/balance/35hK24tcLEWcgNA4JxpvbkNkoAcDGqQPsP

    Response :
    {
        "allow": true,
        "btc": "247502.16273241"
    }

<img width="20" src="http://search.glueapp.net/icon_coin/i_eos.png">***EOS***

    Reqeust :
    http://URL/balance/glueaccount1

    Response :
    {
        "allow": true,
        "eos": "7.3701 EOS"
    }

<br>

***실패 - 잘못된 주소(계정)***

    Reqeust :
    http://URL/balance/홍길동

    Response :
    {
        "allow": false
    }
    
    

제공자 : BRICKSTREAM
