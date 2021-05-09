# CNN Based Music Classification

## 1. 프로젝트 목표

사용자의 감정에따라 곡을 추천하기 위한 CNN 기반의 음악 분류기 (Ternary Classification) 


<br>

## 2. 진행 순서

- 오디오 파일 전처리 
  - WAV 음원 추출
  - STFT를 통한 Spectrogram (image) 생성
  - Spectrogram의 mel scale 변환 (MelSpectrogram)
  
- 이미지 전처리
  - 128 * 128 크기로 Resize
  - R,G,B 채널 정규화

- 커스텀 데이터 셋 만들기 ( with pytorch )

- 신경망 구축하기



<br>

## 3. 학습 데이터
- Youtube 에 올라와있는 한국인이 좋아하는 노래 TOP 100곡
- 각 음원을 5초 단위로 잘라내어 사용 (약 500개의 샘플)
- 각 샘플은 다음 중 하나로 라벨링 되어있음
  
  | 항목 | 라벨링 |
  |---|---|
  |차분한 음악 | 0 |
  |신나는 음악 | 1 |
  |슬픈 음악   | 2 |

    

