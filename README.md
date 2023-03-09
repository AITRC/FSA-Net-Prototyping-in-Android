# FSA-Net Prototyping in Android 

단일 FSA-Net 으로 머리 움직임 (Degree) 을 추정합니다.

```sh
1. 디바이스 카메라 세팅을 합니다. (OpenCV)
2. 얼굴 인식, 머리 움직임 추정 모델을 로드합니다. (Tensorflow)
3. While Loop:
    (3-1) 얼굴을 인식합니다. (OpenCV)
    (3-2) 인식된 얼굴의 각도를 측정합니다. (FSA-Net)
    (3-3) 움직임 라인 (X, Y, Z 축) 을 그립니다. (OpenCV)
```


## Update
- **```2022/01/21```** : 단일 FSA-Net 구현하였습니다. (./FSA-NET.py)
- **```2022/01/22```** : Tensorflow-1 에서 Tensorflow-2 로 리팩토링하였습니다. (./lib/* 와 ./FSA-NET.py)
- **```2022/01/23```** : Numpy, Keras 라이브러리를 Tensorflow-2 로 대체하였습니다. (./lib/* 와 ./FSA-NET.py)
- **```2022/02/14```** : TF Lite 파일을 읽어 모델을 로드할 수 있습니다. (FSA-NET-TFLITE.py)
- **```2022/02/15```** : Media Pipe 로 시선 추정이 가능합니다. (CL-NET-TFLITE.py)
- **```2022/02/15```** : Open CV 를 Media Pipe 로 통합하고 Numpy 를 제거하였습니다. (MITTY.py)


## Project
- 디렉토리 정보를 나타냅니다.

```
    ├── README.md           <- FSA-Net 앱 프로토타이핑 개요를 나타냅니다.
    │
    ├── lib                 <- Pre-Trained FSA-Net (가중치) 의 네트워크 구성 객체입니다. 
    │
    ├── pre-trained         <- Pre-Trained (가중치) 를 저장하는 공간입니다.
    │   ├── face_detector   <- OpenCV 에서 사용하는 Pre-Trained 얼굴 인식 모델입니다.
    │   ├── fsanet_capsule  <- 이미지의 헤드 포즈 각도 추정을 위한 Pre-Trained 가중치입니다.
    │   └── fsanet.tflite   <- 헤드 포즈 각도 객체와 가중치를 모두 포함한 파일입니다. (TFLite 로드 필요)
    │
    ├── demo.py    <- 앙상블 헤드 포즈 TF Lite 파일을 읽어 각도를 추정합니다. (TFLite 파일 필요)
    │                 : [1] Open CV 얼굴 인식 [2] TF Lite 파일로 헤드 포즈 추정 [3] Media Pipe 로 시선 체크
    ├── requirements.txt    <- 라이브러리 환경 구성을 위해 사용합니다.
```


## Dependency
실행을 위해 필요한 라이브러리 목록입니다. **[링크]**(https://c-lab.atlassian.net/wiki/spaces/MIT/pages/382829010/1)
- **Python 3.8**
- **Tensorflow 2.7.0**
- **Mediapipe 0.9.1.0**
- **OpenCV 4.7.0**

```sh
$ pip install -r requirements.txt 
```


## Demo
데모 실행 명령어입니다.
```sh
$ python3 demo.py
```
