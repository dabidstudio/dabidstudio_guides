# 윈도우 10에서 가상환경 설치하기 (기본 venv 모델 사용)

윈도우 10에서 원하는 폴더에 가상환경을 새로 만들고 사용하는 방법에 대해 설명합니다.

## 1. 프로젝트 폴더 만들기
먼저 새로운 프로젝트 폴더를 만들고 터미널의 경로를 해당 폴더로 설정합니다.
- 해당 폴더에서 바로 Git Bash 실행하거나, 상위 폴더에서 `cd 프로젝트_폴더_이름` 명령어를 사용합니다.

## 2. 가상환경 생성
폴더 안에서 다음 명령어를 실행합니다:
```bash
python -m venv venv
```
- Mac의 경우 다음과 같이 실행합니다:
```bash
python3 -m venv venv
```

### 명령어 의미:
- `python`: Python을 실행시킵니다.
- `-m venv`: `venv` 모듈을 실행시킵니다.
- `venv`: 가상환경의 이름을 `venv`로 설정합니다.

가상환경을 잘못 만들어서 삭제하고 싶으면, 해당 폴더를 삭제하면 됩니다.

## 3. 가상환경 활성화
가상환경에서 다른 라이브러리를 설치하려면 활성화가 필요합니다. 
윈도우 10에서는 다음 명령어를 사용합니다:
```bash
.\venv\Scripts\activate
```
Mac에서는 다음 명령어를 사용합니다:
```bash
source venv/Scripts/Activate
```
활성화되면 터미널에 스크립트 위에 괄호가 나타납니다.

## 4. 다른 가상환경에서 사용하던 라이브러리 사용
`requirements.txt` 파일을 사용하여 필요한 라이브러리를 설치합니다:
```bash
pip install -r requirements.txt
```

## 5. 주피터 노트북에 연동
가상환경에 맞는 파일을 다루기 위해 주피터 노트북을 설정합니다.
가상환경이 활성화된 상태에서 다음 명령어를 실행합니다:
```bash
python -m pip install ipykernel
ipython kernel install --user --name=프로젝트_폴더_이름
```
그 후 비활성화 상태에서 주피터 노트북을 실행합니다:
```bash
jupyter-notebook
```

## 6. 가상환경 비활성화
가상환경을 비활성화하려면 다음 명령어를 사용합니다:
```bash
deactivate
```

## 7. 주피터 커널 관리
현재 사용 가능한 주피터 커널을 확인하려면 다음 명령어를 사용합니다:
```bash
jupyter-kernelspec list
```
특정 커널을 삭제하려면 다음 명령어를 사용합니다:
```bash
jupyter-kernelspec uninstall '커널_이름'
```

## 8. 가상환경의 pip 리스트 추출
특정 가상환경 안의 pip 패키지 리스트를 `requirements.txt` 파일로 추출하려면, 가상환경이 활성화된 상태에서 다음 명령어를 실행합니다:
```bash
pip freeze > requirements.txt
```

