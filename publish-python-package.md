
# YouTube MCP 서버 PyPI 배포 가이드  

## 1. Python 패키지란?

Python 패키지는 하나 이상의 모듈을 포함한 코드 디렉토리로, `import`, `pip install`, 또는 CLI 실행이 가능하도록 구조화된 코드 단위입니다.  
타인이나 다른 프로젝트에서 재사용하기 위해 PyPI 등에 배포 가능한 형태여야 합니다.

### 패키지로 인식되기 위한 조건

1. `src/패키지명/` 구조를 갖출 것
2. `__init__.py` 파일이 존재할 것 (빈 파일이어도 됨)
3. `pyproject.toml` 파일에 메타데이터 및 빌드 시스템 정보가 포함될 것

---

## 2. 사전 준비

### 2.1 uv 설치

```bash
pip install uv
````

uv는 pip, venv, poetry, hatch의 기능을 통합한 프로젝트 관리 도구입니다.

### 2.2 PyPI 계정 및 API 토큰

* 계정 생성: [https://pypi.org/account/register/](https://pypi.org/account/register/)
* API 토큰 발급: [https://pypi.org/manage/account/token/](https://pypi.org/manage/account/token/)

PyPI 업로드 시 CLI에서 토큰을 환경 변수로 등록합니다.

---

## 3. 프로젝트 초기화

다음 명령어로 패키지 구조의 프로젝트를 생성합니다.

```bash
uv init --package youtubeinsights-mcp-server-test --build-backend hatch
cd youtubeinsights-mcp-server-test
```

`--package` 플래그는 PyPI 배포를 위한 구조 (`src/`)를 생성해줍니다.

디렉토리 구조 예시:

```
youtubeinsights-mcp-server-test/
├── src/
│   └── youtubeinsights_mcp_server_test/
│       └── __init__.py
├── pyproject.toml
├── README.md
```

---

## 4. 핵심 파일 구성

### 4.1 `src/youtubeinsights_mcp_server_test/__init__.py`

```python
__version__ = "0.1.2"

from .server import main
```

### 4.2 `src/youtubeinsights_mcp_server_test/server.py`

```python
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("youtube_agent_server")

@mcp.tool()
def get_youtube_transcript(url: str) -> str:
    ...

def main():
    print("Starting YouTube MCP Server")
    mcp.run()

if __name__ == "__main__":
    main()
```
* server.py 파일에는 반드시 main() 함수가 선언되어 있어야 함
---



## 6. 로컬 실행 테스트

```bash
uv run youtubeinsights-mcp-server-test
```


---

## 7. 빌드 및 PyPI 배포

### 7.1 빌드 도구 설치

```bash
uv add build twine
```

### 7.2 빌드

```bash
uv build
```

`dist/` 폴더에 `.whl`, `.tar.gz` 파일이 생성됩니다.

### 7.3 배포

API 토큰을 환경 변수에 등록한 후 다음 명령어로 배포합니다.

```bash
uv publish --token {발급받은 PyPI 토큰}
```


### 주의 1 : PyPI 패키지명 중복 오류

`project.name`에 이미 사용된 이름을 입력하면, `uv publish` 시 다음과 같은 에러가 발생합니다.

```
HTTPError: 400 Bad Request from https://upload.pypi.org/legacy/
The name 'youtubeinsights-mcp-server' is already taken.
```

이 경우 `-test`, `-dev`, `-agent` 등으로 이름을 변경해야 함
 - pyproject.toml에서 파일명 변경 + src/{패키지명} 부분에서도 파일명 변경
 - dist 폴더 삭제 후 uv build로 다시 빌드한 후 배포 시도


## 주의 2 : 코드를 수정했을 때 배포
- 코드 수정 사항이 있어서 수정한 후 배포를 하고 싶으면 그냥 바로 uv build + uv publish하면 에러가 발생함 (이미 같은 버전으로 PyPI에 배포되어 있기 때문임)
- pyproject.toml에서 버전을 수정한 후 dist 폴더 삭제, uv build 후 uv publish

---

---




