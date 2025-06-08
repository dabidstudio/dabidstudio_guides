# 텔레그램 봇 토큰 발급 + 내 CHAT ID 확인 방법

## 텔레그램 봇 토큰 발급받기

### 1. 텔레그램 실행하기

* [웹 텔레그램](https://web.telegram.org/) 또는 모바일 앱에 접속합니다.
* 계정이 없다면 회원가입을 먼저 진행하세요.

---

### 2. BotFather 검색해서 대화 시작하기

* 상단 검색창에 `@BotFather` 또는 `botfather` 입력
* 파란 체크마크가 있는 공식 계정을 클릭
* 대화창이 열리면 `/start` 명령어로 시작

<img src="https://github.com/user-attachments/assets/0cd81852-77c2-46fa-9c57-447241a47aa2" alt="BotFather 검색" width="800"/>

---

### 3. 새 봇 생성 및 이름/아이디 정하기

* `/newbot` 입력 후 전송
* BotFather가 봇 **이름**을 물어보면 원하는 이름 입력 (예: `MyTestBot`)
* 다음으로 **사용자 이름(아이디)** 입력
  반드시 `bot`으로 끝나야 하며, 중복된 아이디는 사용 불가
  예: `mytest_bot`, `sample123_bot`

<img src="https://github.com/user-attachments/assets/ff27704b-8c44-4606-812d-cee1e056ddb2" alt="봇 생성 및 이름 정하기" width="800"/>

---

### 4. 봇 생성 완료 — 링크 & API 토큰 확인

* 봇 생성이 완료되면 아래와 같은 메시지가 표시됩니다.
* 스크린샷 **상단에 표시된 링크**(예: `https://t.me/googleaidabidbot`)를 클릭하면
  방금 만든 봇으로 바로 이동할 수 있습니다.
* `"Use this token to access the HTTP API"` 아래에 표시된 **긴 문자열**은 **API 토큰**입니다.
  → 이 토큰은 **봇을 제어하는 열쇠**이므로 꼭 안전하게 저장하세요!

<img src="https://github.com/user-attachments/assets/0557e141-a936-457a-b53d-96fa02c16f9e" alt="토큰과 링크 확인" width="800"/>

---

## 내 CHAT ID 확인하기
나에게 메시지를 보내는 챗봇을 만들기 위해서는 내 텔레그램 계정의 CHAT ID를 확인해야 합니다.

### 1. @userinfobot 검색해서 대화 시작하기

* 상단 검색창에 `@userinfobot` 입력해서 봇 선택하고 대화 시작
<img src="https://github.com/user-attachments/assets/3ae507ef-4f49-4eac-8f7e-133953bcffb5" alt="BotFather 검색" width="600"/>

### 2. 내 ID 받기
Id로 표시되어 있는것이 내 텔레그램 Id
<img src="https://github.com/user-attachments/assets/8d7d6d4e-91b4-4ef3-a06e-e3a5a833320b" alt="BotFather 검색" width="600"/>




