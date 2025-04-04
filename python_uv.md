# uv 가이드: 빠르고 편리한 파이썬 환경 관리 도구

## 1. uv 소개

`uv`는 빠르고 현대적인 Python 패키지 매니저이자 가상환경 관리 도구입니다.  
기존의 `pip`, `venv`, `virtualenv`, `pyenv` 등을 대체할 수 있으며,  
특히 다음과 같은 이유로 주목받고 있습니다.

### ✅ uv의 특징

1. **매우 빠릅니다**  
   `uv`는 Rust로 개발되어 기존의 `pip`이나 `venv`보다 훨씬 빠른 속도로 패키지를 설치하고 환경을 세팅할 수 있습니다.  
   복잡한 의존성 설치도 순식간에 완료됩니다.

2. **매우 편리합니다**  
   복잡하고 번거로웠던 Python 개발 환경 세팅이 `uv` 하나면 해결됩니다.
   - **가상환경 관리가 편리**합니다  
     기존에는 `python -m venv`, `source activate` 등을 매번 입력해야 했지만, 이제는  
     `uv run main.py` 명령어 하나면 자동으로 가상환경이 생성되고 실행까지 완료됩니다.
   - **파이썬 버전 관리도 간편**합니다  
     `uv venv-python 3.12`처럼 커맨드 한 줄로 원하는 Python 버전을 설치하고 사용할 수 있습니다.  
     별도로 `pyenv`나 수동 설치가 필요 없습니다.

3. **MCP의 표준 도구입니다**  
   `uv`는 OpenAI 기반 에이전트 개발 프로토콜인 **MCP (Model Context Protocol)** 에서도 표준처럼 사용되는 툴입니다.  
   Agent 개발자라면 필수로 알아야 할 도구입니다.


## 2. uv 설치법

### 📦 간단 설치 명령어

#### 1) macOS 및 Linux (wget 이용)
```bash
wget -qO- https://astral.sh/uv/install.sh | sh
```

#### 2) Windows (PowerShell 사용)
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

---


## 3. uv 주요 명령어 및 활용법

### 📁 1) 프로젝트 초기화
```bash
uv init
```
현재 폴더에 `uv`용 가상환경 및 설정 파일(pyproject.toml)을 생성합니다.

---

### ▶️ 2) 파일 실행 (자동 가상환경 생성 포함)
```bash
uv run main.py
```
- 기존에 가상환경이 없으면 자동으로 생성해주고, 바로 `main.py` 실행까지 진행합니다.
- 매우 편리한 올인원 실행 명령어입니다.

---

### ➕ 3) 패키지 설치
```bash
uv add numpy pandas
```
- 필요한 패키지를 `pyproject.toml`에 자동으로 등록하고 설치합니다.
- 기존의 `pip install`과 동일한 역할을 하면서 더 빠르고 안정적으로 작동합니다.

---

### ➖ 4) 패키지 삭제
```bash
uv remove numpy
```
- 설치된 패키지를 가상환경에서 제거하고, 설정 파일에서도 자동 삭제해줍니다.

---

### 🐍 5) 파이썬 버전 지정 및 변경
```bash
uv venv-python 3.12
```
- 현재 가상환경을 Python 3.12로 교체합니다.
- Python이 설치되어 있지 않으면 자동으로 다운로드하여 설치까지 해줍니다.

---

### 🔍 6) 사용 가능한 파이썬 버전 보기
```bash
uv python list
```
- 사용 가능한 Python 버전들을 확인할 수 있습니다.

### 📥 7) 새로운 파이썬 버전 설치
```bash
uv python install 3.11
```
- pyenv 없이도 간단하게 다양한 Python 버전을 설치할 수 있습니다.

---

## 💡 Tip: uv는 왜 좋은가요?

| 기능 | 기존 방식 | uv 사용 시 |
|------|------------|--------------|
| 가상환경 생성 | `python -m venv venv` | 자동 생성 (`uv run`) |
| 가상환경 활성화 | `source venv/bin/activate` | 불필요 (자동 인식) |
| 패키지 설치 | `pip install` | `uv add` (빠름) |
| Python 버전 관리 | `pyenv`, 수동 설치 | `uv venv-python`, `uv python install` |

---

## ✅ 마무리

`uv`는 이제 단순한 실험용 도구가 아니라,  
현대적인 Python 개발 워크플로우를 구성하기 위한 **표준**이 되어가고 있습니다.  
특히 AI/에이전트 개발을 하는 분이라면 필수 도구로 강력히 추천드립니다.
