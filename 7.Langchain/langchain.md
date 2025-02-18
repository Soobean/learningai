## 1. LangChain 개요

**정의 및 목적**

LangChain은 대규모 언어 모델(LLM)을 단순히 텍스트를 생성하는 도구로 사용하는 것을 넘어, 다양한 데이터 소스(문서, 데이터베이스, API, 웹 스크래핑 등)와 외부 도구(예: API 호출, 코드 실행 등)를 통합하여 복잡한 응용 프로그램을 구축할 수 있도록 돕는 오픈 소스 프레임워크입니다.

- 주로 파이썬(Python) 환경에서 사용되며, OpenAI, Hugging Face 등 여러 LLM 공급자와 연동되어 재훈련 없이 기존 모델을 다양한 방식으로 활용할 수 있도록 지원합니다.

LangChain에 데이터 흐름도(출처 : [*https://docs.langchain.com/](https://docs.langchain.com/))*

---

## 2. 주요 구성 요소 및 개념

### 2.1 체인(Chains)

- **개념:**
체인은 여러 LLM 호출이나 기타 함수 호출을 순차적으로 연결하여 하나의 워크플로우로 만드는 단위입니다.
- **용도:**
복잡한 작업(예: 문서 요약 → 질문 응답 → 결과 정리)을 여러 단계로 나누어 처리하며, 각 단계의 출력이 다음 단계의 입력으로 전달됩니다.

### 2.2 에이전트(Agents)

- **개념:**
에이전트는 LLM이 상황에 따라 동적으로 어떤 작업을 수행할지 결정하고, 외부 API 호출, 데이터베이스 검색 등 다양한 도구와 상호작용할 수 있게 합니다.
- **특징:**
    - **의사 결정:** LLM이 스스로 필요한 작업 단계를 선택할 수 있도록 합니다.
    - **도구 활용:** 여러 도구와 연동해 작업을 진행하며, 예를 들어 챗봇에서 사용자의 질의에 맞춰 추가 데이터를 검색하거나 API를 호출하는 역할을 수행합니다.

### 2.3 메모리(Memory)

- **개념:**
체인이나 에이전트가 진행하는 대화나 작업의 문맥(context)을 저장해, 이전 단계의 정보를 기억하고 이를 기반으로 일관된 결과를 제공할 수 있도록 합니다.
- **용도:**
대화형 애플리케이션이나 여러 단계의 작업에서 이전 히스토리를 활용해 보다 정확한 응답이나 결과를 생성하는 데 필수적입니다.

### 2.4 프롬프트 템플릿(Prompt Templates)

- **개념:**
LLM에게 전달할 입력값을 일정한 형식으로 구성하는 도구입니다.
- **장점:**
    - **일관성:** 여러 작업에서 동일한 형식의 프롬프트를 사용하여 안정적인 출력을 유도합니다.
    - **유연성:** 사용자 입력이나 외부 데이터에 따라 동적으로 템플릿 내용을 변경할 수 있습니다.

### 2.5 다양한 LLM 및 외부 도구와의 통합

- **호환성:**
LangChain은 OpenAI의 GPT, Hugging Face의 Transformers 등 다양한 LLM 공급자와 쉽게 연동되며, 웹 스크래핑, 데이터베이스 연결, API 호출 등 외부 시스템과의 통합을 통해 단순 텍스트 생성 이상의 복잡한 응용 프로그램을 구현할 수 있습니다.

---

## 3. LangChain의 기본 프레임워크

LangChain은 전체 LLM 애플리케이션 라이프사이클(개발 → 테스트 → 배포)을 지원하는 다양한 오픈 소스 라이브러리와 도구들로 구성되어 있습니다.

- **개발:**
    - **langchain:** 체인, 에이전트, 검색 전략 등 인지 아키텍처를 구성하는 핵심 빌딩 블록 제공.
    - **langchain-core:** 기본 추상화 및 LangChain 표현 언어(LCEL)를 포함하여, 체인의 구조와 동작을 정의.
    - **langchain-community:** OpenAI, Anthropic 등 서드파티 통합 모듈 제공.
- **테스트:**
    - **LangSmith:** 체인을 디버깅, 테스트, 평가, 모니터링할 수 있는 개발자 플랫폼.
    (실행 로그, 성능 분석 등 문제 해결에 도움을 줌)
- **배포:**
    - **LangGraph:** 체인을 그래프의 에지와 노드로 모델링하여, 복잡한 “stateful” 멀티 액터 애플리케이션을 구축할 수 있도록 지원.
    - **LangServe:** LangChain 체인을 REST API로 배포하여 프로덕션 환경에서 활용할 수 있게 합니다.

---

## 4. 기술적 세부사항

### 4.1 아키텍처 및 실행 메커니즘

- **모듈화 및 Runnable 인터페이스:**
    
    LangChain의 구성 요소들은 공통의 Runnable 인터페이스(동기/비동기 실행, 스트리밍, 배치 처리)를 구현하여, 동일한 방식으로 호출하고 조합할 수 있습니다.
    
- **비동기 및 병렬 처리:**
    
    여러 단계의 임베딩 생성이나 외부 API 호출 등은 ThreadPoolExecutor나 async/await를 활용하여 병렬 처리할 수 있으며, 캐싱(In-Memory, Redis 등)을 통해 반복 호출에 따른 성능 저하를 방지합니다.
    
- **출력 파서(Output Parsers):**
    
    LLM의 원시 텍스트 출력을 JSON, XML, Pydantic 모델 등으로 구조화하여 후속 처리에 적합한 데이터 형태로 변환합니다.
    

### 4.2 외부 도구 및 API 연동

- **문서 로더(Document Loaders):**
웹페이지, PDF, CSV 등 다양한 파일 형식에서 데이터를 추출하여 LLM의 입력으로 활용할 수 있습니다.
- **벡터 데이터베이스:**
임베딩을 생성하고 FAISS, Chroma, Milvus 등의 벡터 저장소에 저장한 후 유사도 기반 검색을 통해 관련 정보를 효율적으로 조회할 수 있습니다.
- **LangGraph 및 LangServe:**
LangGraph를 통해 복잡한 에이전트 상호작용을 그래프 기반으로 모델링하고, LangServe를 통해 체인을 REST API로 배포하여 운영 환경에 적용합니다.

---

## 5. 기술적 장점과 한계

### 장점

1. **다양한 데이터 소스 및 도구와의 손쉬운 통합:**
    
    여러 외부 데이터 소스 및 API와 쉽게 연동되어 문서 요약, 질의응답, 데이터 분석 등 복잡한 작업을 수행할 수 있습니다.
    
2. **모듈화 및 유연성:**
    
    체인, 에이전트, 메모리, 프롬프트 템플릿 등이 독립적으로 설계되어 있어, 개발자가 필요한 기능을 자유롭게 조합하고 교체할 수 있습니다.
    
3. **재훈련 없이 다양한 응용:**
    
    기존 LLM을 그대로 활용하면서 프롬프트 엔지니어링과 체인 구성만으로 다양한 응용 프로그램을 빠르게 구축할 수 있습니다.
    
4. **확장성 및 활발한 커뮤니티 지원:**
    
    오픈 소스 커뮤니티를 통해 최신 기능과 서드파티 통합이 지속적으로 추가되어, 프로덕션 환경에서도 확장이 용이합니다.
    

### 한계

1. **학습 곡선의 가파름:**
    
    다양한 구성 요소와 복잡한 기능을 이해하고 효과적으로 활용하기 위해서는 상당한 학습이 필요합니다.
    
2. **디버깅 및 문제 해결의 복잡성:**
    
    여러 모듈이 상호 연동되어 있어 오류 발생 시 어느 단계에서 문제가 생겼는지 파악하기 어려워, LangSmith와 같은 디버깅 도구가 필수적입니다.
    
3. **성능 최적화 문제:**
    
    대량 데이터 처리, API 호출, 임베딩 생성 등의 과정에서 성능 최적화를 위한 추가적인 하드웨어 자원 및 코드 개선이 요구됩니다.
    
4. **외부 API 의존성:**
    
    OpenAI, Hugging Face 등 외부 API에 의존하다 보니, API 호출 제한, 네트워크 지연, 보안 이슈 등 외부 서비스의 제약이 전체 시스템에 영향을 미칠 수 있습니다.
    

---

## 6. 결론 및 종합 정리

LangChain은 단순 텍스트 생성 이상의 복잡한 LLM 기반 애플리케이션을 구축할 수 있도록 설계된 혁신적인 프레임워크입니다.

- **핵심 기술적 요소:**
체인, 에이전트, 메모리, 프롬프트 템플릿 등의 모듈화된 구성 요소를 통해 복잡한 워크플로우를 구축하며, 비동기 및 병렬 처리, 출력 파서, 캐싱 등을 활용하여 성능과 확장성을 보장합니다.
- **통합 기능:**
웹 데이터, PDF, CSV 등 다양한 데이터 소스를 로드하고, 임베딩 및 벡터 검색, 외부 API 호출, 그리고 LangGraph와 LangServe를 통해 프로덕션 환경으로 쉽게 배포할 수 있습니다.
- **장단점:**
유연성과 확장성, 재훈련 없이 다양한 응용 가능 등의 장점이 있는 반면, 학습 곡선, 디버깅 난이도, 성능 최적화, 외부 API 의존성 등의 한계가 존재합니다.

---

### 간단한 구현

**환경 설정** 

```python
$ pip install langchain-openai langchain-core
```

**질문-응답 체인 구현** 

```python
import getpass
import os
from langchain_openai import AzureChatOpenAI
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser

# Azure OpenAI Endpoint 설정 
if "AZURE_OPENAI_API_KEY" not in os.environ:
    os.environ["AZURE_OPENAI_API_KEY"] = getpass.getpass(
        "Enter your AzureOpenAI API key: "
    )
os.environ["AZURE_OPENAI_ENDPOINT"] = "https://YOUR-ENDPOINT.openai.azure.com/"

# api_version 설정 
llm = AzureChatOpenAI(
    azure_deployment="gpt-4o",  # or your deployment
    api_version="2024-08-01-preview",  # or your api version
    temperature=0,
    max_tokens=None,
    timeout=None,
    max_retries=2,
)

# 프롬프트 연쇄(Chain)
prompt = ChatPromptTemplate.from_messages(
    [
        (
            "system",
             "You are a helpful assistant who always takes an extra moment to carefully {Reasoning} before answering the user's question. Provide your final answer after thinking it through.",
        ),
    (
        "user", 
        "Question: {input}"
    ),
    ]
)
# 단순 문자열 출력 Parser 생성
parser = StrOutputParser()

# 체인 구성 : 프롬프트 -> Azure OpenAI 모델 -> 출력 파서
chain = prompt | llm | parser
result = chain.invoke({
    "Reasoning": "analyzing",
    "input": "What is the capital of France?"
})

print(result)
```

[Azure_LangChain.ipynb](attachment:6f7bc023-1d38-4143-9930-8c2fa1668a20:Azure_LangChain.ipynb)

### **출처**

1. https://python.langchain.com/docs/introduction/
2. https://python.langchain.com/docs/integrations/chat/azure_chat_openai/
3. https://nikhilpentapalli.medium.com/langchain-in-detail-6cf8ecfb2464
4. https://rudaks.tistory.com/entry/langchain-Conceptual-guide
5. https://revf.tistory.com/280
6. https://www.samsungsds.com/kr/insights/what-is-langchain.html
7. https://github.com/easonlai/azure_openai_langchain_sample