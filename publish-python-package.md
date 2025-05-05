
# 🧠 YouTube MCP 서버 PyPI 배포 가이드  
**(uv 패키지 관리 툴을 이용)**

---

## 📦 Python 패키지란?

**파이썬 패키지**는 하나 이상의 모듈을 포함하는 디렉토리로, 다른 프로젝트에서 재사용 가능한 코드의 단위입니다.  
`pip install`로 설치하고, `import` 또는 CLI 실행(`uvx`)이 가능해야 진정한 "패키지"로 취급됩니다.

### ✅ 패키지로 인식되기 위한 조건

1. **디렉토리 구조**
   - 보통 `src/패키지명/` 구조
   - 예: `src/youtubeinsights_mcp_server_test/`

2. **`__init__.py` 파일**
   - 해당 폴더를 Python 패키지로 인식하게 함
   - 버전, 함수, 엔트리 포인트 등을 export 가능

3. **`pyproject.toml`**
   - 메타데이터 (`name`, `version`, `dependencies`, 등)
   - 빌드 시스템 (`hatchling`, `setuptools`, 등)
   - 실행 명령어 설정 (`[project.scripts]`)

4. **(선택)** `__main__.py`
   - `python -m 패키지명` 형태로 실행하고 싶을 때 필요

---

## ✅ 1. 사전 준비

### 1-1. uv 설치

```bash
pip install uv
````

* 최신 Python 프로젝트 툴체인
* `pip`, `venv`, `hatch`, `poetry` 기능 통합

### 1-2. PyPI 계정 및 API 토큰 준비

* 회원가입: [https://pypi.org/account/register/](https://pypi.org/account/register/)
* 토큰 생성: [https://pypi.org/manage/account/token/](https://pypi.org/manage/account/token/)

> CLI 배포 시 환경 변수로 등록

---

## 📦 2. 프로젝트 생성

```bash
uv init --package youtubeinsights-mcp-server-test --build-backend hatch
cd youtubeinsights-mcp-server-test
```

### 🔍 왜 `--package` 옵션이 필요한가?

* PyPI에 배포하려면 패키지로 구성된 프로젝트 구조가 필요
* `--package`를 통해 자동으로 다음과 같은 구조 생성됨:

```
youtubeinsights-mcp-server-test/
├── src/
│   └── youtubeinsights_mcp_server_test/
│       └── __init__.py
├── pyproject.toml
├── README.md
```

---

## 🧠 3. 주요 파일 구성

### 3-1. `src/youtubeinsights_mcp_server_test/__init__.py`

```python
__version__ = "0.1.2"

from .server import main
__all__ = ["main"]
```

### 3-2. `src/youtubeinsights_mcp_server_test/server.py`

```python
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("youtube_agent_server")

# MCP Tool 예시
@mcp.tool()
def get_youtube_transcript(url: str) -> str:
    ...

def main():
    print("✅ Starting YouTube MCP Server")
    mcp.run()

if __name__ == "__main__":
    main()
```

### 3-3. (선택) `__main__.py`

```python
from .server import main

if __name__ == "__main__":
    main()
```

> `python -m youtubeinsights_mcp_server_test` 실행 지원 시 필요

---

## ⚙️ 4. pyproject.toml 설정

```toml
[project]
name = "youtubeinsights-mcp-server-test"  # 🔥 PyPI에 등록될 이름
version = "0.1.2"
description = "A deployable MCP server for YouTube insights"
readme = "README.md"
requires-python = ">=3.9"
dependencies = [
  "mcp",
  "httpx",
  "python-dotenv",
  "youtube-transcript-api"
]

[project.scripts]
youtubeinsights-mcp-server-test = "youtubeinsights_mcp_server_test:main"

[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"
```

### ⚠️ PyPI 이름 중복 주의

* `name` 필드에 이미 등록된 이름을 사용하면 **배포 시 에러 발생**

```bash
HTTPError: 400 Bad Request from https://upload.pypi.org/legacy/
The name 'youtubeinsights-mcp-server' is already taken.
```

→ 이름 뒤에 `-test`, `-dev`, `-agent` 등을 붙여 조정

---

## 🧪 5. 실행 테스트 (로컬)

```bash
$env:YOUTUBE_API_KEY="your_api_key"
uv run youtubeinsights-mcp-server-test
```

또는:

```bash
uv --directory ./ run youtubeinsights-mcp-server-test
```

---

## 📦 6. 빌드 및 PyPI 배포

### 6-1. 빌드 도구 설치

```bash
uv add build twine
```

### 6-2. 빌드

```bash
uv build
```

→ `dist/` 폴더에 `.whl`, `.tar.gz` 생성

### 6-3. PyPI 배포

```bash
$env:TWINE_PASSWORD="pypi-AgEIcH..."  # 발급받은 토큰
uv publish --token $env:TWINE_PASSWORD
```

---

## ✅ 7. 설치 및 실행 테스트

```bash
pip install youtubeinsights-mcp-server-test
uvx youtubeinsights-mcp-server-test
```

> `uvx`는 격리된 임시 환경에서 CLI 스크립트를 실행함

---


