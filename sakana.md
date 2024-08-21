# SAKANA AI

## Introduction
- LLM(Large Language Models)과 같은 Foundation Models가 독립적으로 연구를 수행할 수 있도록 하는 완전 자동 과학적 발견을 위한 최초의 포괄적인 시스템 **THe AI Scientist**
- 완전 자동화된 개방형 과학적 발견을 지향 

1. 기꼐 학습 연구에 적용되 자동화된 과학적 발견을 위한 완전 AI 기반 시스템을 제안
2. AI Scientist는 새로운 연구 아이디어를 생성하고 필요한 (1)코드를 작성하고 (2)실험을 실행하는 것부터 (3)실험 결과를 요약하고 (4)시각화 하며 (5) 연구 결과를 토대로 과학 논문을 작성 하는 것까지 Research Lifecycle을 자동화 
3. (6)자동화 된 동료 검토 프로세스를 도입하여 생성한 논문을 평하고 피드백을 작성하며 결과를 개선한다. 
4. 자동화된 과학적 발견 과정이 반복되어 개방적인 방식으로 아이디어를 반복하면서 개발하고 증가하는 지식 아카이브에 추가하여 인간 과학 공동체를 모방
5. 첫 시연으로 기계 학습 연구 내에서 다양한 하위 분야에서 연구를 수행하여 확산 모델,Transformer,grokking과 같은 인기 분야에서 새로운 기여

15달러의 비용으로 전체 논문 작성 가능

## Overview of The AI Scientist 
<p align ="center">
<img src ="https://sakana.ai/assets/ai-scientist/schematic_2.png">
THe AI Scientist 개념
</p>

## 주요 프로세스
1. **아이디어 생성** : 시작 템플릿이 주어지면 AI Scientist는 다양한 연구방향으로 브레인스토밍을 진행 (Semantic Scholar에 검색해 독창성 확인)
   - 논문 작성을 위해 Style File와 Section Header가 포함된 LaTex폴더 포함
2. **실험 반복** : 먼저 제안된 실험을 실행한 다음 결과를 시각화할 플롯을 얻고 생성한다. 각 플롯에 무엇이 포함되어 있는 설명하는 노트를 작성하여 저장된 수치와 실험 노트를 통해 논문 작성에 필요한 정보 제공
3. **논문 쓰기** : LaTex에서 진행되는 기계학습 컨퍼런스 스타일의 진행 상황을 간결하고 유익하게 작성(Semantic Scholar을 통해 인용할 관련 논문을 자율적으로 검색)
4. **자동화 된 논문 검토** : 자동화된 LLM 기반 리뷰어를 개발한다.이는 지속적인 피드백 루프를 가능하게 하여 AI Scientist가 연구 결과를 반복적으로 개선할 수 있도록 한다.

------------------------
## 한계 및 과제
1. 비전 기능이 없기 때문에 논문으로 시각적 문제를 해결하거나 플롯을 읽을 수없다.
2. 아이디어를 잘못 구현하거나 기준선과 불공하게 비교하여 오해의 소지가 있는 결과 초래
3. 결과를 작성하고 평가할 떄 중대한 오류를 범한다.(숫자 비교)




[The AI Scientist Github](https://github.com/SakanaAI/AI-Scientist)  
[The AI Scientist Paper](https://arxiv.org/pdf/2408.06292)