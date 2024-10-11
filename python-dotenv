# Python에서 Dotenv로 안전하게 환경 변수 관리하기

## 1. 소개

Python으로 프로그램을 개발할 때, 외부 API를 사용하기 위해 API 키를 코드에 직접 하드코딩하는 경우가 있습니다:

```python
import openai

OPENAI_API_KEY = "sk-xxxxxxxxxxxxxxxx"
```

하지만 이러한 방법은 여러 문제점을 야기합니다.

### 하드코딩의 문제점

1. **보안 위험**: 코드에 API 키를 하드코딩하면 코드 유출 시 키도 함께 노출됩니다. 특히 GitHub와 같은 공개 저장소에 실수로 업로드되면 심각한 보안 문제가 발생합니다.

2. **환경 설정의 비유연성**: 개발 환경과 운영 환경에서 다른 설정이 필요할 때, 하드코딩된 값은 환경별 설정을 어렵게 만듭니다. 매번 코드를 수정해야 하므로 비효율적입니다.

3. **유지 보수의 복잡성**: 여러 파일에서 동일한 API 키를 사용할 경우, 각 파일마다 키를 업데이트해야 합니다. 이는 실수의 여지를 높이고 관리가 번거로워집니다.

## 2. Dotenv로 문제 해결하기

이러한 문제를 해결하기 위해, 중요한 정보를 `.env` 파일에 저장하고 `python-dotenv` 패키지를 사용하여 관리할 수 있습니다.

### 1) 패키지 설치

```bash
pip install python-dotenv
```

### 2) `.env` 파일 생성

프로젝트 루트 디렉토리에 `.env` 파일을 생성하고 다음과 같이 작성합니다:

```env
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxx
```

### 3) 코드 수정

`.env` 파일의 내용을 불러와서 사용합니다:

```python
import openai
from dotenv import load_dotenv
import os

load_dotenv()
openai.api_key = os.getenv("OPENAI_API_KEY")
```

이제 API 키는 코드에 하드코딩되지 않고, 안전하게 관리됩니다.

## 3. 결론

API 키를 하드코딩하면 보안 위험과 유지 보수의 어려움이 발생합니다. `python-dotenv`를 사용하면 이러한 문제를 효과적으로 해결하고, 환경 변수 관리를 더욱 안전하고 편리하게 할 수 있습니다.
