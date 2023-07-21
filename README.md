# 4th-AIxBookathon
제 4회 SKKU AIxBOOKATHON 대회 최우수상을 수상한 팀 테이북 repository입니다.

## 목차
1. [대회 소개](#1-대회-소개)
2. [데이터 수집](#2-데이터-수집)
3. [데이터 전처리](#3-데이터-전처리)
4. [주제 선정](#4-주제-선정)
5. [모델 학습](#5-모델-학습)
6. [모델 인퍼런스](#6-모델-인퍼런스)
7. [수필](#7-수필)
---
## 1. 대회 소개
<img src="https://github.com/ryuseunghan/4th-AIxBookathon/assets/106146847/111d03d1-b5d7-4b9a-87c2-238b67789ca8.png"  width="600" height="800"/>   

* 성균관대학교에서 주최한 제 4회 AIxBookathon은 인공지능 모델을 활용하여, 주어진 키워드를 주제로 수필을 작성하는 대회입니다.
* 대회 당일날 주제가 공개되었으며 주제는 ```"담대한(Daring)"```이었습니다.
</br>

#### 🏆 2nd of 15 teams
저희 팀 테이북은 본선에 진출한 총 15개의 팀 중 2위를 하여 최우수상을 수상하였습니다.

## 2. 데이터 수집
>글틴
대표 에세이 문학회   
브런치   
동아신춘문예   
모두의 말뭉치 - 비출판물 데이터

학습을 위해 최대한 주제별로 많은 데이터를 수집해줬으며 데이터는 저작권에 위배되지 않는 데이터만 수집했습니다.  
</br>
이때 주제별로 많은 데이터를 수집한 이유는 대회 당일날 주제를 공개한다는 이유도 있었지만 결과적으로 저희가 수필을 생성할 때 단락마다 각각의 최적화된 모델을 학습하는데 큰 도움이 되었습니다.

## 3. 데이터 전처리
* KLUE : Korean Language Understanding Evaluation에서 사용한 전처리 기법 사용했습니다다

## 4. 주제 선정
### 담대한은 곧 모더니즘
<img src="https://github.com/ryuseunghan/4th-AIxBookathon/assets/106146847/512471f9-f011-436f-bc1c-9a34f644a18a.png"  width="800" height="400"/>

```
저희는 담대함의 터부시되는 경계를 깨부수는 속성을 통해 모더니즘의 기조를 연결지어 인상주의 화가 모네
그리고 보편적인 가치에서 벗어나 주체성을 되찾아가는 성장 수필을 구성하게 되었습니다.
```

## 5. 모델 학습
#### 사용모델 : SKT/kogpt2-base-v2
#### 모델 학습 전략 : 플롯을 구성하고 각 주제에 맞게 베이스모델을 파인튜닝 
마인즈랩에서 제공한 서버 환경에서 다양한 생성 모델들을 동일한 데이터로 학습 뒤에 생성 되는 텍스트를 비교하였고 SKT-KoGPT2를 선정하게 되었습니다.   
</br>
모델 선정 기준
1. 학습 속도
2. 학습 데이터 반영되는 정도
3. 문장의 자연스러움
</br>
40mb 가량의 데이터로 해당 모델을 한번 더 사전학습을 진행하여 베이스 모델을 생성하였습니다.
베이스 모델을 기반으로 각 에피소드에 해당하는 키워드를 선정하고 그 키워드에 해당하는 데이터를 통해 fine-tuning을 진행하였습니다.   
</br>
<img src="https://github.com/ryuseunghan/4th-AIxBookathon/assets/106146847/f81616ca-7ebe-4013-9536-fd8cfa1c1d10.png"  width="800" height="400"/>
<img src="https://github.com/ryuseunghan/4th-AIxBookathon/assets/106146847/6e0b39e3-7b85-4416-80d1-cb8965af5e8f.png"  width="800" height="400"/>

</p>
그 결과 10 종류의 모델을 생성하였으며 이렇게 10 종류의 모델들을 통해 수필 속 움직이는 시점과 다채롭게 변화하는 화자의 심리를 효과적으로 반영했습니다.

## 6. 모델 인퍼런스
* top-p sampling 방법을 이용하여 텍스트를 생성
* 짧은 텍스트를 생성하고 그 텍스트를 다시 prompt로 사용

top-p sampling은 디코딩 전략 5가지를 정성평가를 진행해 선정하게 되었습니다.   
[How to generate text: using different decoding methods for language generation with Transformers](https://huggingface.co/blog/how-to-generate?fbclid=IwAR19kbEiW_sF19TeSr4BE4jQZSIqz0GzOFD2013fIGEH32DReW9pAFq6vDM)를 참고하였습니다.

### 7. 수필
[수필 본문](과거에서 찾은 '나'.md)

