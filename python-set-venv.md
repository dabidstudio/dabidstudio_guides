# 가상환경 설치하기 (기본 venv 모델 사용,윈도우 기준)

윈도우 10에서 원하는 폴더에 가상환경을 새로 만들고 사용하는 방법에 대해 설명합니다.

[가상환경 구조]
![image](https://github.com/user-attachments/assets/a68f40da-40c7-40ef-afda-d68ae3b91fbe)


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
source venv/bin/activate
```
활성화되면 터미널에 스크립트 위에 괄호가 나타납니다.

## 4. 다른 가상환경에서 사용하던 라이브러리 사용
`requirements.txt` 파일을 사용하여 필요한 라이브러리를 설치합니다:
```bash
pip install -r requirements.txt
```

## 5. 가상환경의 pip 리스트 추출
특정 가상환경 안의 pip 패키지 리스트를 `requirements.txt` 파일로 추출하려면, 가상환경이 활성화된 상태에서 다음 명령어를 실행합니다:


## venv 설정 후 팁
- venv를 설정한 후 venv를 실행하면 자동으로 venv 폴더가 있는 폴더의 .env 파일을 환경변수로 인식합니다 (python-dotenv 같은 프로그램을 사용하지 않아도 되는 간편함이 있습니다)
- 그러나 만약 .env 파일에서 변경사항이 있는 경우 터미널을 반드시 종료하고 새롭게 가상환경을 실행해야 해당사항들이 적용되기 때문에 유의가 필요합니다.
    - 그런 면에서는 load_env()이 더 편할 수 있습니다.
```bash
pip freeze > requirements.txt
```

