# English_Accent_Classification
### 📢 Overview


- 총 6개국(Africa, Australia, Canada, England, Hongkong, US)에서 녹음 된 음성 파일로 English accent를 분류하는 코드입니다.
- 머신러닝, MLP, CNN 등 다양한 방법으로 국가별 악센트 분류를 시도하였습니다.


### 🛠️ Requirements

```
- Python : 3.7.10
- Scikit-learn : 0.24.2
- Tensorflow : 2.3.0
- Librosa : 0.8.1
- CUDA : 11.2
```

### 🎙️ Data


![data](https://user-images.githubusercontent.com/54276004/124896688-a068ed00-e018-11eb-9799-be83f696b1ca.png)


### 🖥️ Process


1. Voice_Classification_ML.ipynb
2. Voice_Classification_MLP.ipynb
3. Voice_Classification_CNN.ipynb


> Pre-processing

- 전처리 코드는 **Voice_Classification_CNN.ipynb**에 포함되어 있습니다.
- 데이터의 용량이 매우 크기 때문에 npy 형식으로 변환 후 저장하였습니다.
- 데이터의 길이가 일정하지 않아 모든 데이터를 최소 길이로 분할하였습니다.
- 음성 신호를 프레임별로 나누어 FFT를 적용해 Spectrum을 구하고,   
Spectrum에 Mel Filter Bank를 적용해 Mel Spectrogram을 구하였습니다.


> Modeling

- Voice_Classification_ML.ipynb  
  - 기본적인 머신러닝 분류 모델인 LogisticRegression, DecisionTreeClassifier,    
    RandomForestClassifier, AdaBoostClassifier을 적용하였습니다.


- Voice_Classification_MLP.ipynb  
   - Tensorflow를 사용하여 MLP 모델을 구현  
   - Mel Spectrogram을 1차원으로 Flatten한 후 input값으로 사용하였습니다.


- Voice_Classification_CNN.ipynb
    - Tensorflow를 사용하여 CNN 모델을 구현  
    - Mel Scpectrogram으로 나온 값이 이미지의 형상을 띄고 있기 때문에 CNN을 적용하였습니다.  
    - Time, Frequency = x, y / Amplitude = pixel value  

    ![mel_spctrogram](https://user-images.githubusercontent.com/54276004/124896625-93e49480-e018-11eb-8ac1-0985f0811e0a.png)  

    - Audio data는 Grayscale image와 비교되기 때문에 Depth를 1로 설정하였습니다.  
    - Overfitting을 방지하기 위해 StratifiedKFold를 사용하였습니다.
