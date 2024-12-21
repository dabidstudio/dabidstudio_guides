# **챗 GPT잘쓰는 팁 : 질문을 최대한 길게 하자**

## 그 이유

- 챗GPT는 질문(프롬프트)를 넣으면 응답이 나오는 함수
    
![image](https://github.com/user-attachments/assets/e18e431a-c9f8-4af4-a5a7-fa85be79d458)


- 프롬프트 엔지니어링은 질문을 잘하는 기술
    
    

- 질문을 잘한다 = 질문을 길게 한다
    
    예전에 비해서 질문+응답이 가질 수 있는 최대 길이가 너무 길어짐 
    → 앞으로도 계속 길어질 예정
    
    | **모델명** | **출시연월** | **지원 토큰 수** | **워드 페이지 수 (한글 기준)** |
    | --- | --- | --- | --- |
    | GPT-3.5 | '22년 11월 | 약 4,096 | 약 5페이지 |
    | GPT-4-32K | '23년 03월 | 약 32,768 | 약 40페이지 |
    | GPT-4o | '24년 05월 | 약 128,000 | 약 160페이지 |
    
    * 워드 기준 1 페이지에 1,300자 (맑은고딕 10포인트) → 약 800토큰
    

## 구체적인 방법 4가지

### **1. 질문 자체를 최대한 구체적으로 하기**

- 챗 GPT는 아무것도 모르는 똑똑이
- **흡수력은 뛰어나지만 처음 입사한 신입사원 친구에게 지시한다면?**

- 구체적인 요약 프롬프트
    
    위 내용을 한글로 요약해줘
    
    - 핵심 내용 3가지를 언급해줘.
    - 핵심내용은  “~하였음, 했음” 등의 어조를 이용해줘
    - 각 핵심 내용을 뒤받침하는 내용을 2개씩 추가해줘
    - 그래서 총 3 * 2, 즉 6문장으로 말해줘
    - 핵심내용은 헤딩 3, 뒷받침내용은 불렛포인트로 해줘

### **2. 구체적인 역할을 부여하기**

영어 번역을 할 때

- 일반적인 프롬프트 : “위 내용을 번역해줘”
- 역할이 부여된 프롬프트
    
    챗 GPT한테 번역을 시킨 이유에 맞게 역할을 부여하는 것
    
    번역을 하는 이유 : 영어와 업계 용어에 대해서 잘 이해하고 싶음
    
    부여된 역할 : **영어 선생님이자 AI 전문가**
    
    - 수정된 프롬프트 :
        
        너는 나의 영어 선생님이자 AI 전문가야
        
        - 영어 선생님으로서는 나에게 영어 문장의 문법적인 구조를 분석하고 이해하기 쉽게 설명해주는 게 중요해
            - 자주 쓰는 관용적인 표현이나  단어는 꼭 기억해달라고 알려줘
        - AI 전문가로서는 어렵거나 모르는 용어와 개념에 대해서 아주 쉽고 직관적으로 주석 설명을 추가해주는 것이 중요해
        
        위와 같은 관점에서 아래 내용을 번역해줘
        
    

### **3. 원하는 답변 예시를 구체적으로 제시하기**

- By January 2023, ChatGPT had become what was then the fastest-growing consumer software application in history, gaining over 100 million users in two months[[8]](https://en.wikipedia.org/wiki/ChatGPT#cite_note-:8-8)[[9]](https://en.wikipedia.org/wiki/ChatGPT#cite_note-9) and contributing to the growth of OpenAI's current [valuation](https://en.wikipedia.org/wiki/Business_valuation) of $86 billion.[[10]](https://en.wikipedia.org/wiki/ChatGPT#cite_note-10)[[11]](https://en.wikipedia.org/wiki/ChatGPT#cite_note-11)
위 영어 문장을 분석해줘
- 구체적인 답변 예시 추가
    
    
    By January 2023, ChatGPT had become what was then the fastest-growing consumer software application in history, gaining over 100 million users in two months[[8]](https://en.wikipedia.org/wiki/ChatGPT#cite_note-:8-8)[[9]](https://en.wikipedia.org/wiki/ChatGPT#cite_note-9) and contributing to the growth of OpenAI's current [valuation](https://en.wikipedia.org/wiki/Business_valuation) of $86 billion.[[10]](https://en.wikipedia.org/wiki/ChatGPT#cite_note-10)[[11]](https://en.wikipedia.org/wiki/ChatGPT#cite_note-11)
    
    위 문장을 분석해줘
    
    - 아래 예시 응답의 형식에 맞게 분석해줘
    
    ## 예시 응답
    
    (예시 문장 : ChatGPT initially used a [Microsoft Azure](https://en.wikipedia.org/wiki/Microsoft_Azure) [supercomputing](https://en.wikipedia.org/wiki/Supercomputer) infrastructure, powered by [Nvidia](https://en.wikipedia.org/wiki/Nvidia) [GPUs](https://en.wikipedia.org/wiki/GPU), that [Microsoft](https://en.wikipedia.org/wiki/Microsoft) built specifically for OpenAI and that reportedly cost "hundreds of millions of dollars".)
    
    ### 1. 문장구조분석 테이블
    
    | **구분** | **내용** | **번역** | **비고** |
    | --- | --- | --- | --- |
    | **주어** | ChatGPT | ChatGPT | 문장의 주체, 기술 주도 기업이 개발한 AI 모델을 지칭. |
    | **서술어** | initially used | 초기에는 사용했습니다. | 과거 시제 동사 "used"로 ChatGPT의 초기 인프라 사용을 설명. |
    | **보어** | a Microsoft Azure supercomputing infrastructure | Microsoft Azure의 슈퍼컴퓨팅 인프라 | 보어는 구체적으로 ChatGPT가 사용한 기술적 자원을 설명. |
    | **기타** | - powered by Nvidia GPUs                                                                              - that Microsoft built specifically for OpenAI                                               - that reportedly cost "hundreds of millions of dollars" | - Nvidia GPU로 구동되는                                                                          - Microsoft가 OpenAI를 위해 특별히 구축한                                                    - 보고에 따르면 "수억 달러"가 들었습니다. | 관계대명사와 분사구문으로 주요 내용 보완. 기술적 특징과 비용 강조. |
    
    ---
    
    ### 2. 핵심 관용어/단어 분석 테이블
    
    | **항목** | **구분** | **뜻** | **비고** |
    | --- | --- | --- | --- |
    | initially | 부사 | 초기에는 | 시간적 시점을 강조하며 과거 동사와 자주 사용. |
    | supercomputing infrastructure | 명사구 | 슈퍼컴퓨터 인프라 | 고성능 컴퓨팅 자원을 포함하는 시스템 전체를 포괄. |
    | powered by | 동사구 | ~에 의해 구동되는 | 기술적 원천이나 에너지원 설명 시 사용. |
    | Nvidia GPUs | 고유명사/명사구 | Nvidia사의 그래픽 처리 장치 | 고성능 컴퓨팅을 위한 하드웨어 설명. |
    | specifically for | 관용구 | ~을 위해 특별히 | 특정 목적에 맞춰 설계됨을 강조. |
    | reportedly | 부사 | 보고에 따르면 | 정보 출처가 명확하지 않을 때 간접적 사실 전달에 사용. |
    | "hundreds of millions of dollars" | 숫자 표현/관용구 | 수억 달러 | 비용 규모를 강조하며 기술적 인프라의 고비용을 부각. |

### **4. 사전정보 제시하기 (RAG)**

챗 GPT 유저 플랜에 따른 컨텍스트길이를 표로 비교해줘
