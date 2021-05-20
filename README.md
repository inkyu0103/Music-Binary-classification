# CNN Based Music Classification

## 1. 프로젝트 목표

사용자의 감정에따라 곡을 추천하기 위한 CNN 기반의 음악 분류기 (Ternary Classification)
<br>


일반적으로, 음악을 장르 및 분위기를 분류하기 위해서는 사용된 악기 종류, 음의 높낮이 ,소리의 크기 ,빠르기 및 다양한 특징들을 직접 골라내어 분류한다. 이렇게 각 음악마다 특징을 하나하나 뽑아낸다는 것은 쉬운 일이 아니며, 특징을 뽑아내는 과정에서 주관적으로 평가하게 되는 문제도 존재한다. 이러한 문제들을 해결하고자, 직접 음악적 특징을 추출하는 것이 아닌 음악이 가지고 있는 고유한 진동수를 시각화하고, CNN을 이용하는 학습시키는 방법을 통해 여러가지 곡들을 분류하고자 한다.


<br>

## 2. 진행 순서

- [오디오 추출 및 전처리 & 이미지 처리](#3-학습-데이터)
  - WAV 음원 추출
  - STFT를 통한 Spectrogram (image) 생성
  - Spectrogram의 mel scale 변환 (MelSpectrogram)
  - 128 * 128 크기로 Resize
  - R,G,B 채널 정규화

- [신경망 구축하기](#5-신경망-구축)

- [라이브 테스트](#6-라이브-테스트)



<br>

## 3. 학습 데이터

### (1) 기존에 음악-감정 분류에 사용한 데이터셋 사용 (CAL 500) : **사용하지 않음**
  
  CAL 500 데이터를 그대로 사용하려다, 다음과 같은 이유로 사용하지 않게 되었습니다.

  - 몇몇 나라의 논문을 살펴본 결과 자국의 곡을 분석하는 경우가 존재

    (참고 논문)
    - Neural Network architectures to classify emotions in Indian Classical Music 
    - Music emotion recognition using convolutional long short term memory deep neural network

  - 데이터의 형식이 생각했던 방식과 달라서, 처리하는데 시간이 많이 걸릴 것이라 예상


### (2) 데이터를 직접 만들기
- Youtube 에 올라와있는 한국인이 좋아하는 노래 TOP 100곡
- 각 음원을 5초 단위로 잘라내어 사용 (약 500개의 샘플)
- 음원의 중간 부분부터 5개의 샘플 골라냄
- 각 샘플은 다음 중 하나로 라벨링 되어있음
  
  | 항목 | 라벨링 |
  |---|---|
  |차분한 음악 | 0 |
  |신나는 음악 | 1 |
  |슬픈 음악   | 2 |

  (수정 2021.05.18)
    
    3가지 분류를 다음과 같은 이유로 2가지 분류로 수정하였습니다.
  
    - 라벨링 과정에서 슬픈 음악과 차분한 음악의 애매모호함 
    <br>
      (Ex. [다린 - 가을](https://www.youtube.com/watch?v=1IApYpeWe8A&ab_channel=%EB%82%98%EC%9D%98%EC%9E%91%EA%B3%A0%EC%95%A0%ED%8B%8B%ED%95%9C%EC%A0%95%EC%9B%90%EB%82%98%EC%9D%98%EC%9E%91%EA%B3%A0%EC%95%A0%ED%8B%8B%ED%95%9C%EC%A0%95%EC%9B%90)은 슬픈 노래인가? 차분한 노래인가?)

    - 세분화를 하면 할 수록 더 많은 데이터가 요구됨. 같은 규모의 데이터를 그대로 사용하면, 예측과정에서 정답률이 많이 낮아지는 결과가 발생

  <br>

    | 항목 | 라벨링 |
    |---|---|
    |차분한 음악 | 0 |
    |신나는 음악 | 1 |
    


## 4. 오디오 추출 및 전처리 & 이미지 처리

### (1) 오디오 추출

  - python librosa 패키지 사용
  - sampling rate는 기존의 22050 사용

### (2) Spectrogram vs MelSpectrogram vs MFCC

1. Spectrogram의 정의 
 
    A spectrogram is a visual representation of the spectrum of frequencies of a signal as it varies with time
    

2. 왜 사용하는가?
  
    음악의 


3. Mel-Spectrogram


4. MFCC 




## 5. 신경망 구축



## 6. 라이브 테스트