# 동기/비동기 프로그래밍

컴퓨터 프로그램에서 동기(synchronous) 프로그래밍과 비동기(asynchronous) 프로그래밍이라는 두 가지 주요 실행 방식이 있음

### 동기(Synchronous)
- 동기(Synchronous) 프로그래밍에서는 코드가 한 줄씩 순서대로 실행되는 방식
- 예를 들어 A와 B 라는 함수가 차례대로 있으면 순서대로 코드가 실행됩니다. 기본적으로 파이썬은 동기 프로그래밍

### 비동기(Asynchronous) 
- 비동기(Asynchronous) 프로그래밍은 어떤 작업이 끝나기를 기다리지 않고, 다른 작업을 먼저 실행할 수 있는 방식
- 예를들어 A라는 함수가 오래 걸린다면 그 결과를 기다리는 동안 B, C 등 다른 함수도 함께 실행될 수 있음
- 그래서 여러 함수나 작업을 동시에 처리하는 병렬처리를 위해서는 비동기 방식으로 코드를 실행해야 함

<p align="center">
  <img src="https://github.com/user-attachments/assets/0f8ba981-c062-45ce-b7db-bc1c0647b382" width="500" />
</p>


### asyncio, async/await

- 파이썬에서는 비동기 프로그래밍을 위해 asyncio라는 표준 라이브러리를 사용
- 여기서 async def로 비동기 함수를 정의하고, 비동기 작업 앞에는 await를 붙임
- 그리고 asyncio.run()을 이용하면 다음과 같이 async로 정의된 비동기 함수를 실행할 수 있음

```python
import asyncio

async def say_hello():
    await asyncio.sleep(1)
    print("Hello, world!")

asyncio.run(say_hello())  # 비동기 함수 실행
```
