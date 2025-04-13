# uv 가이드: 빠르고 편리한 파이썬 환경 관리 도구

<img src="https://github.com/user-attachments/assets/487696ed-5126-47f5-9a18-45852702ae9d" width="600"/>


## 1. uv란?

`uv`는 Python 생태계를 위한 **초고속 패키지 설치 + 가상환경 관리 + Python 버전 관리** 도구입니다.  
Rust로 작성되어 있어 **pip + venv보다 수십 배 빠르고 편리**합니다.

---

## 2. uv의 핵심 강점 3가지

### 1) 뛰어난 속도
- 패키지 설치 속도가 매우 빠름 (Rust 언어와 병렬 처리 기술 덕분)
- 실제 예시: `pip install streamlit` (10초) vs `uv pip install streamlit` (2초)

### 2) 프로젝트 관리의 편리성
- **기존 pip/venv 방식**:
  - `python -m venv venv`
  - `venv\scripts\activate`
  - `pip install [패키지]`
  - 매번 새 세션에서 activate 필요
  - 공유 시 `pip freeze > requirements.txt` 필요

- **uv 방식**:
  - `uv init`으로 프로젝트 시작 (필요 파일 자동 생성)
  - `uv add [패키지]`로 가상환경 자동 생성 및 패키지 설치
  - `uv run main.py`로 바로 실행 (activate 불필요)
  - 공유 시 다른 사람도 바로 `uv run main.py`로 실행 가능

### 3) 떠오르는 업계 표준
- 최신 AI 관련 패키지와 예제에서 널리 사용됨
- MCP Python SDK에서 권장하는 도구
- 많은 MCP 서버가 uv로 개발되어 공유됨
- A2A 프레임워크 등 최신 기술 스택에서 권장

이전에도 pip/venv의 대안으로 poetry, pipx, pyenv 등이 있었지만,
uv는 실질적인 속도와 편의성 개선으로 실제 도입 가치가 높은 도구

---

## 3. 설치 방법

**윈도우 (PowerShell)**

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**macOS / Linux (bash)**

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

설치 확인:

```bash
uv --version
```

**공식 설치 문서**: [https://docs.astral.sh/uv/getting-started/installation/#standalone-installer](https://docs.astral.sh/uv/getting-started/installation/#standalone-installer)

---

## 4. uv 사용 예시

### (1) 프로젝트 초기화

```bash
uv init
```

또는 특정 폴더로 초기화:

```bash
uv init my_project
```

### (2) 패키지 설치

```bash
uv add streamlit
```

### (3) 패키지 제거

```bash
uv remove streamlit
```

### (4) 실행

```bash
uv run main.py
```

### (5) Python 버전 바꾸기

```bash
echo 3.11.7 > .python-version
```

Python 버전 변경 시 `pyproject.toml` 파일도 업데이트하는 것이 좋습니다:

```toml
[project]
requires-python = ">=3.11.7"
```

`uv run main.py` 실행 시 필요한 Python 버전이 자동으로 설치되므로, 별도 설치 과정 없이도 프로젝트 실행이 가능합니다.

---
## 5. 샘플 uv 프로젝트 실행

```bash
# 1) 저장소 복제
git clone https://github.com/dabidstudio/uv_python_example

# 2) 프로젝트 폴더로 이동 및 초기화
cd uv_python_example

# 3) 프로젝트 실행
uv run main.py
```

---

## 6. uvx란?

`uvx`는 **설치 없이 파이썬패키지를 즉시 실행**할 수 있는 명령어입니다.

```bash
uvx elevenlabs/elevenlabs-mcp
```
- pypi에 등록되어 있는 패키지여야 함
- 사용 후 자동 정리
- MCP 서버로서 빠른 사용 및 실행에 최적

## ✅ 마무리

`uv`는 이제 단순한 실험용 도구가 아니라,  
현대적인 Python 개발 워크플로우를 구성하기 위한 **표준**이 되어가고 있습니다.  
특히 AI/에이전트 개발을 하는 분이라면 필수 도구로 강력히 추천드립니다.
