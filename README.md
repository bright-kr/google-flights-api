# Google Flights Scraper

[![Promo](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.co.kr/products/web-scraper/google-flights)

이 리포지토리는 Google Flights에서 항공편 데이터를 추출하는 두 가지 방법을 제공합니다:

1. **무료 Google Flights Scraper:** 소규모 추출에 적합합니다
2. **Google Flights Scraper API:** 무제한 리クエスト로 대용량 실시간 데이터 추출을 위해 설계되었습니다. Bright Data의 [SERP Scraping API](https://brightdata.co.kr/products/serp-api)의 일부입니다.


## Table of Contents
2. [Free Scraper](#free-scraper)
   - [Setup Requirements](#setup-requirements)
   - [Quick Start](#quick-start)
   - [Sample Output](#sample-output)
   - [Limitations](#limitations)
3. [Google Flights Scraper API](#google-flights-api)
   - [Key Features](#key-features)
   - [Prerequisites](#prerequisites)
   - [Direct API Access](#direct-api-access)
   - [Native Proxy-Based Access](#native-proxy-based-access)
4. [Additional Parameters](#additional-parameters)
   - [Localization Parameters](#localization-parameters)
   - [Currency Parameter](#currency-parameter)
5. [Support & Resources](#support--resources)

## Free Scraper
Google Flights에서 제한된 데이터 추출을 위한 빠르고 간단한 スクレイピング 도구입니다.

<img width="800" alt="google-flights-scraper" src="https://github.com/bright-kr/google-flights-api/blob/main/images/424383720-44ae10b1-4974-497e-9a7c-c1a762614f0e.png" />

### Setup Requirements
- [Python 3.9+](https://www.python.org/downloads/)
- 브라우저 자동화를 위한 [Playwright](https://playwright.dev/)

```bash
pip install playwright
playwright install chromium
```

> **Webスクレイピング이 처음이신가요?** [Python으로 Webスクレイピング 시작하기 가이드](https://brightdata.co.kr/blog/how-tos/web-scraping-with-python)를 확인해 보시기 바랍니다.
>

### Quick Start
1. [google-flights-scraper.py](https://github.com/bright-kr/google-flights-api/blob/main/google-flights-scraper/google-flights-scraper.py)를 여십시오.
2. 다음 변수를 업데이트하십시오:
    - `url`: Google Flights URL을 붙여 넣으십시오(일반적으로 `tfs`를 포함합니다).
3. 스크립트를 실행하십시오.

💡 Pro Tip: `HEADLESS = False`로 설정하면 Google의 anti-scraping 조치에 의한 탐지를 최소화할 수 있습니다.

### Sample Output
```json
{
  "airline": "Emirates",
  "departure_time": "4:15 AM",
  "arrival_time": "2:00 PM",
  "duration": "22 hr 15 min",
  "stops": "1 stop in DXB",
  "price": "$1,139",
  "co2_emissions": "1,092 kg CO2e",
  "emissions_variation": "+6% emissions"
}
```

👉  [전체 출력 샘플 보기](https://github.com/bright-kr/google-flights-api/blob/main/google-flights-results/flight_results.json)


### Limitations
무료 Scraper에는 몇 가지 제약이 있습니다:
- IP 차단 위험이 높습니다
- 리クエスト 볼륨이 제한적입니다
- CAPTCHA가 자주 발생합니다
- 프로덕션 용도로는 신뢰성이 낮습니다

이러한 제한 없이 견고하고 확장 가능한 スクレイピング을 위해서는 아래의 Bright Data 전용 API를 고려해 보시기 바랍니다. 👇

## Google Flights Scraper API
[Bright Data의 Google Flights Scraper API](https://brightdata.co.kr/products/web-scraper/google-flights)는 [SERP Scraping API](https://brightdata.co.kr/products/serp-api)에 통합되어 있으며, 광범위한 [プロキシ network](https://brightdata.co.kr/proxy-types)를 활용하여 CAPTCHA나 IP 차단 없이 가격, 일정, 항공사 상세 정보를 포함한 실시간 항공편 데이터를 대규모로 추출합니다.

### Key Features

- **글로벌 정확도:** 특정 위치에 맞춘 결과를 제공합니다
- **성공 기반 과금(Pay-Per-Success):** 성공한 리クエスト에 대해서만 비용이 청구됩니다
- **실시간 데이터:** 최신 항공편 데이터를 몇 초 만에 가져옵니다
- **무제한 확장성:** 대용량 スクレイピング을 손쉽게 처리합니다
- **비용 효율적:** 비용이 큰 인프라 필요성을 제거합니다
- **신뢰할 수 있는 성능:** 내장된 anti-blocking 기술을 제공합니다
- **24/7 전문가 지원:** 필요 시 언제든지 지원을 받을 수 있습니다

### Prerequisites

1. [Bright Data 계정 생성](https://brightdata.co.kr/) (신규 사용자는 $5 크레딧을 받습니다).
2. [API key](https://docs.brightdata.com/general/account/api-token)를 생성하십시오.
3. [단계별 가이드](https://github.com/bright-kr/google-flights-api/blob/main/setup-serp-api-guide.md)를 따라 SERP API를 구성하고 자격 증명을 설정하십시오.

### Direct API Access

API エンドポイント로 직접 리クエ스트를 보내십시오.

**cURL Example:**

```bash
curl https://api.brightdata.com/request \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer API_TOKEN" \
  -d '{
        "zone": "ZONE_NAME",
        "url": "https://www.google.com/travel/flights/search?tfs=CBwQAhojEgoyMDI1LTA0LTAxagcIARIDREVMcgwIAxIIL20vMDRqcGxAAUgBcAGCAQsI____________AZgBAg",
        "format": "raw"
      }'
```

**Python Example:**

```python
import requests

url = "https://api.brightdata.com/request"
headers = {"Content-Type": "application/json", "Authorization": "Bearer API_TOKEN"}
payload = {
    "zone": "ZONE_NAME",
    "url": "https://www.google.com/travel/flights/search?tfs=CBwQAhojEgoyMDI1LTA0LTAxagcIARIDREVMcgwIAxIIL20vMDRqcGxAAUgBcAGCAQsI____________AZgBAg",
    "format": "raw",
}

response = requests.post(url, headers=headers, json=payload)

with open("google-flights-data.html", "w", encoding="utf-8") as file:
    file.write(response.text)
print("HTML response saved to 'google-flights-data.html'.")
```

### Native Proxy-Based Access

대신 Bright Data의 プロキシ 라우팅 방식을 사용할 수 있습니다.

**cURL Example:**

```bash
curl -i \
  --proxy brd.superproxy.io:33335 \
  --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
  -k \
  "https://www.google.com/travel/flights/search?tfs=CBwQAhojEgoyMDI1LTA0LTAxagcIARIDREVMcgwIAxIIL20vMDRqcGxAAUgBcAGCAQsI____________AZgBAg"
```

**Python Example:**

```python
import requests
import urllib3

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

host = "brd.superproxy.io"
port = 33335
username = "brd-customer-<customer-id>-zone-<zone-name>"
password = "<zone-password>"
proxy_url = f"http://{username}:{password}@{host}:{port}"

proxies = {"http": proxy_url, "https": proxy_url}
url = "https://www.google.com/travel/flights/search?tfs=CBwQAhojEgoyMDI1LTA0LTAxagcIARIDREVMcgwIAxIIL20vMDRqcGxAAUgBcAGCAQsI____________AZgBAg"
response = requests.get(url, proxies=proxies, verify=False)

with open("google-flights-data.html", "w", encoding="utf-8") as file:
    file.write(response.text)

print("Response saved to 'google-flights-data.html'.")
```

👉 [전체 HTML 출력 보기](https://github.com/bright-kr/google-flights-api/blob/main/google-flights-api-output/google-flights-data.html).

**Note:** 프로덕션 용도에서는 [SSL Certificate Guide](https://docs.brightdata.com/general/account/ssl-certificate)에 따라 Bright Data의 SSL 인증서를 로드하십시오.


## Additional Parameters
다음 선택적 파라미터로 Google Flights 데이터 추출을 세밀하게 조정할 수 있습니다.

### Localization Parameters
<img width="800" alt="bright-data-google-flights-api-localization" src="https://github.com/bright-kr/google-flights-api/blob/main/images/424454961-e77f10c9-8e44-46aa-be3d-64c756741479.png" />

위치 및 언어에 따라 검색 결과를 사용자 지정하십시오:

| Parameter | Description | Example |
| --- | --- | --- |
| gl | 두 글자 국가 코드 | `gl=us` (United States) |
| hl | 두 글자 언어 코드 | `hl=en` (English) |


**Example:** 프랑스어로 파리에서 런던으로 가는 항공편을 검색하십시오:

```bash
curl --proxy brd.superproxy.io:33335 --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
"https://www.google.com/travel/flights/search?tfs=CBwQAhojEgoyMDI1LTA0LTAxagcIARIDQ0RHcgwIAxIIL20vMDRqcGxAAUgBcAGCAQsI____________AZgBAg&hl=fr&gl=fr"
```

### Currency Parameter

<img width="800" alt="bright-data-google-flights-api-currency" src="https://github.com/bright-kr/google-flights-api/blob/main/images/424820088-c571e99f-b854-449e-abc2-60149611ad5b.png" />

`curr` 파라미터를 사용하여 반환되는 가격의 통화를 정의하십시오.

**Example:** 가격을 USD로 반환합니다.

```bash
curl --proxy brd.superproxy.io:33335 --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
"https://www.google.com/travel/flights/search?tfs=CBwQAhojEgoyMDI1LTA0LTAxagcIARIDQ0RHcgwIAxIIL20vMDRqcGxAAUgBcAGCAQsI____________AZgBAg&hl=fr&gl=fr&curr=USD"
```

## Support & Resources

- **Docs:** [SERP API Documentation](https://docs.brightdata.com/scraping-automation/serp-api/)
- **Related APIs:** [Web Unlocker API](https://github.com/bright-kr/web-unlocker-api), [SERP API](https://github.com/bright-kr/serp-api), [Google Search API](https://github.com/bright-kr/google-search-api), [Google News Scraper](https://github.com/bright-kr/Google-News-Scraper), [Google Trends API](https://github.com/bright-kr/google-trends-api), [Google Reviews API](https://github.com/bright-kr/google-reviews-api), [Google Hotels API](https://github.com/bright-kr/google-hotels-api)
- **Google スクレイピング 튜토리얼:**
    - [How to Scrape Google Flights](https://brightdata.co.kr/blog/web-data/how-to-scrape-google-flights)
    - [How to Scrape Google Search Results](https://brightdata.co.kr/blog/web-data/scraping-google-with-python)
    - [How to Scrape Google Maps](https://brightdata.co.kr/blog/web-data/how-to-scrape-google-maps)
- **Use Cases:**
    - [SEO & SERP Tracking](https://brightdata.co.kr/use-cases/serp-tracking)
    - [Travel Industry Data](https://brightdata.co.kr/use-cases/travel)
- **Additional Reading:** [Best SERP APIs](https://brightdata.co.kr/blog/web-data/best-serp-apis)
- **Contact Support:** [support@brightdata.com](mailto:support@brightdata.com)