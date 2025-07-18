# ChatGPT

- GPT(Generative Pre-trained Transformer) : 사전 훈련된 생성 트랜스포머 AI 모델
- Transformer와 Attention 메커니즘
  
# API

## Interface

서로 다른 두 개의 시스템(기기, 소프트웨어 등)이 정보를 교환할 때, 그 사이에 존재하는 것

ex) 키보드, 마우스, 모니터 / TV 리모컨 / 자동차 운전대, 페달 / 스마트폰 터치 스크린 등

 ## Client-Server

- Client : 서비스를 요청하는 대상
- Server : 요청을 받아서 처리하고, 결과를 응답해주는 대상

![client-server](image.png)

## API Key
API에게 요청을 보내는 애플리케이션을 구별하기 위한 고유한 식별 문자열   
목적 : 보안 강화, 데이터 관리

# Vibe Coding

- VSCode와 Copilot을 이용하여 프롬프트 엔지니어링을 이용한 미니 챗봇 만들기 :   
https://married-spot-253.notion.site/5fef18bbcd4b467fb8c7ed819250e1e8?v=d7d02b0f89684f7e8e5650572eb693e2


# Prompt Engineering

- 사전 준비 : https://colab.research.google.com/drive/1IQ2D12h2JnAEd_w8cWk02ozIXjK6LFYO
  
- GPT가 이전 대화를 기억할 수 있는 원리? context window
  
- 토큰(Token) : 문장에서 '단어'와 유사, 텍스트 데이터를 처리하고 이해하는 기본 단위
  
- OpenAI 주요 parameter
  1. 필수 파라미터
     1. model
     2. messages
  2. 옵션 파라미터
     1. temperature : 다음 토큰의 다양성을 조정(응답의 창의성과 다양성 조정)   
    **temperature가 높아질수록**, 확률분포가 평탄해져 **더 다양한 단어가 선택**될 가능성 증가
     2. top_p : 선택할 토큰의 확률 범위를 제한   
    **top_p가 낮아질수록**,특정 질문에 대한 **특정한 단어만 후보로 남게 됨**

  ex1) 낮은 temperature + 높은 top_p :
높은 확률 단어에 집중하고 선택 후보가 다양함
->  기술문서 작성, 고객 지원

  ex2) 높은 temperature + 낮은 top_p :
다양한 단어에 집중하고 선택 후보가 제한적
->  아이디어 도출, 소설 생성
