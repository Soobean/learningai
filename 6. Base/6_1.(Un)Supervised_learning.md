# LLM 1차 목표

![image-1](https://github.com/user-attachments/assets/e94400c5-d2f2-4d6c-bc85-f5c61e22bc71)
[출처 :Attention is All you need](https://arxiv.org/pdf/1706.03762, "논문 링크")

## LLM(Large Learning Model)의 베이스가 되는 신경망 아키텍처(BERT,GPT)

### BERT(Bidirectional Encoder Representations from **Transformers**)

- 윗 논문의 Encoder부분을 활용해 만든 모델

### GPT(Generatice Pretrained **Transformer**)

- Decoder부분을 활용해 만든 모델

---

# 인공지능 기초 #1

![image-2](https://github.com/user-attachments/assets/abda05b6-11d2-49da-8d55-357ab4cfb4b8)

## 지도 학습 / 비지도 학습 / 강화 학습

### 지도 학습

- 분류 : 주어진 데이터를 정해진 라벨에 따라 분류하는 문제
  - (Ex . 개/고양이 분류)
- 회귀 : 어떤 데이터들의 Feature를 기준으로, 연속된 값(그래프)를 예측하는 문제
  - (Ex , 부동산 예측)

### 비지도 학습

- 라벨이 없는 데이터들 비슷한 Feature로 군집화하여 새로운 데이터에 대한 결과를 예측하는 방법

![image-3](https://github.com/user-attachments/assets/e2636bf2-d6cb-43f8-adbe-221f3d4423a7)

### 강화 학습

- 에이전트(Agent)가 주어진 환경에서 최적의 행동(Action)을 학습하여 보상(Reward)를 최대화하는 방법
  - 에이전트 : 학습 수행하는 주체
  - 환경 : 에이전트 행동에 따라 상태와 보상을 제공
  - 행동 : 에이전트가 환경에서 취할 행동
  - 상태 : 현재 환경의 상황을 나타내는 정보
  - 보상 : 에이전트가 행동에 따른 보상

상호작용 -> 업데이트 -> 최적화 순으로 이루어진다.
