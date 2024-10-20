# 가상환경 설치하기 

컴퓨터에 파이썬을 설치하게 되면 자동으로 파이썬 환경 1개가 만들어집니다.  
그런데 상황에 따라서 파이썬 환경이 1개가 아니라 여러 개가 필요할 수 있는데,  
각각의 파이썬 환경을 ‘가상환경’이러고 합니다. 

파이썬 가상환경 없이 1개의 환경에 패키지를 설치하게 되면  
패키지 충돌, 버전 충돌 등의 에러가 발생할 수 있습니다.  
그래서 내 파이썬 코드을 최대한 에러없이 실행하고 싶으면  
아래 가이드대로 가상환경을 먼저 만들고 실행하는 것을 권장드립니다.

### <가상환경 구조>
![image](https://github.com/user-attachments/assets/a68f40da-40c7-40ef-afda-d68ae3b91fbe)


## 1. 프로젝트 폴더로 들어갑니다.
먼저 VS Code로 내 파이썬 파일이 있는 폴더로 들아와서 터미널(Ctrl+`)을 실행합니다.  
보통 터미널의 경로가 지금 열려 있는 폴더로 되어있습니다.
![image](https://github.com/user-attachments/assets/31749776-0864-44c5-9725-eae2c3a38d23)


## 2. 가상환경 생성
폴더 안에서 다음 명령어를 실행합니다:
```bash
python -m venv venv
```
- Mac의 경우 다음과 같이 실행합니다:
```bash
python3 -m venv venv
```

이 명령어를 제대로 실행했으면 다음과 같이 venv 폴더가 생성될 것입니다.
![image](https://github.com/user-attachments/assets/15a5461e-4d84-44d3-bb87-23774bdeed8b)



## 3. 가상환경 활성화
가상환경을 만들었으니
다음 명령어를 이용해서 활성화를 해줍니다. 

```bash
.\venv\Scripts\activate
```
Mac에서는 다음 명령어를 사용합니다:
```bash
source venv/bin/activate
```
활성화되면 터미널에 스크립트 위에 괄호가 나타납니다.
![image](https://github.com/user-attachments/assets/67195cde-b79e-4dbb-aa5c-5bd6b7cc00f3)


## 4. 패키지 설치
활성화 된 상태에서 패키지 설치 명령어를 입력하면 그 가상환경에 패키지가 설치됩니다.
```bash
pip install [패키지이름]
```

### 다른 가상환경에서 사용하던 라이브러리 사용
만약 requirements.txt 파일이 같은 경로에 있으면   
`requirements.txt` 파일을 사용하여 필요한 라이브러리를 설치합니다:
```bash
pip install -r requirements.txt
```

## 가상환경 비활성화
더이상 가상환경을 사용하지 않아도 되면 다음 명령어로 비활성화 해줍니다.
```bash
deactivate
```

## (기타) venv 설정 후 팁
- venv를 설정한 후 venv를 실행하면 자동으로 venv 폴더가 있는 폴더의 .env 파일을 환경변수로 인식합니다 (python-dotenv 같은 프로그램을 사용하지 않아도 되는 간편함이 있습니다)
- 그러나 만약 .env 파일에서 변경사항이 있는 경우 터미널을 반드시 종료하고 새롭게 가상환경을 실행해야 해당사항들이 적용되기 때문에 유의가 필요합니다.
    - 그런 면에서는 load_env()이 더 편할 수 있습니다.


