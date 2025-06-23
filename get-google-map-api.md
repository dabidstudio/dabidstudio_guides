# 구글 맵 API 키 발급받기

## 1. Google Cloud 프로젝트 생성 및 API 키 발급받기

1. **Google Cloud Console**([https://console.cloud.google.com)에](https://console.cloud.google.com%29에) 로그인
2. 상단의 **“프로젝트 선택” → “새 프로젝트”** 클릭 후 이름 입력
3. 프로젝트 생성 후 왼쪽 메뉴에서 \*\*“API 및 서비스 → 라이브러리”\*\*로 이동
4. **Places API**, **Directions API**, **Geocoding API**를 각각 검색하여 하나씩 **‘사용(Enable)’**
5. \*\*“API 및 서비스 → 사용자 인증 정보”\*\*로 이동
6. **“자격 증명 만들기 → API 키”** 클릭
7. 키가 생성되면 **클립보드에 복사**
8. (선택) **보안 강화**: 키 설정 → ‘애플리케이션 제한’ → HTTP referrer 또는 IP 추가, ‘API 제한’ → 위 세 가지 API만 선택 ([developers.google.com][1], [developers.google.com][2], [wpsocialninja.com][3])

---

## 2. 간단 GET 요청으로 확인하기

복사한 **API 키**를 아래 URL에 붙여 넣고 브라우저 주소창에 입력해 보세요:

```
https://maps.googleapis.com/maps/api/geocode/json?address=Seoul&key=YOUR_API_KEY
```

* JSON 형태로 응답이 오면 정상!
* 예: `"results"`, `"geometry"` 등 데이터 포함&#x20;

다른 API도 같은 방식으로 웹 요청 테스트 가능합니다:

* **Geocoding API** (주소 → 좌표)
* **Directions API** (출발→도착 길찾기):

  ```
  https://maps.googleapis.com/maps/api/directions/json?origin=Seoul&destination=Busan&key=YOUR_API_KEY
  ```
* **Places API** (장소 검색):

  ```
  https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=37.5665,126.9780&radius=500&key=YOUR_API_KEY
  ```

각 API에 맞는 엔드포인트만 바꿔주면 브라우저에서 즉시 확인 가능해요.

---

## 3. 브라우저 테스트 요약

| API            | 설명      | 테스트 URL (브라우저 입력)                                                          |
| -------------- | ------- | -------------------------------------------------------------------------- |
| **Geocoding**  | 주소 → 좌표 | `...?geocode/json?address=Seoul&key=...`                                   |
| **Directions** | 길찾기     | `...?directions/json?origin=Seoul&destination=Busan&key=...`               |
| **Places**     | 장소 검색   | `...?place/nearbysearch/json?location=37.5665,126.9780&radius=500&key=...` |

> `"results"` 와 `"status": "OK"` 같이 JSON이 정상적으로 반환되면 발급, 활성화, 요청 모두 성공한 것입니다!

---

## ✅ 정리

1. Google Cloud 프로젝트 생성
2. Places, Directions, Geocoding API 활성화
3. API 키 발급 → *(선택)* 보안 설정
4. 브라우저로 간단 GET 요청 예시 실행 → 결과 확인

이 가이드만 따라도 **5분 안에** API 키 발급부터 브라우저 테스트까지 완료할 수 있어요.
궁금한 점 있으면 언제든 물어보세요!

[1]: https://developers.google.com/maps/documentation/geocoding/get-api-key?utm_source=chatgpt.com "Use API Keys with Geocoding API | Google for Developers"
[2]: https://developers.google.com/maps/documentation/geocoding/start?utm_source=chatgpt.com "Get Started | Geocoding API - Google for Developers"
[3]: https://wpsocialninja.com/get-google-places-api-key/?utm_source=chatgpt.com "How to Generate Google Places API Key (Ultimate Guide)"
