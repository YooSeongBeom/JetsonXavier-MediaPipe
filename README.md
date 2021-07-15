# JetsonXavier-MediaPipe
>1. Jetson SDK manager 및 기본 사용자 설정이 완료된 상태를 가정.    
>2. Nano를 이용하여 Mediapipe를 설치.sh파일을 그대로 사용하여 사양에 맞춰 나머지 버전을 업그레이드 해줘야함    
>3. Tensor 2.4.0 Containner 21.05를 사용    
1. 다운로드 하기전 의존성 패키지와 사전에 필요한 패키지들을 install하고 .sh파일을 실행시켜 mediapipe 설치.
~~~
#Setup
pip install setup
wget https://bootstrap.pypa.io/get-pip.py
sudo python3 get-pip.py
rm get-pip.py


sudo pip3 install pip --upgrade
sudo pip3 install opencv_contrib_python

#mediapipe 
git clone https://github.com/PINTO0309/mediapipe-bin
cd mediapipe-bin

./v0.8.5/numpy119x/mediapipe-0.8.5_cuda102-cp36-cp36m-linux_aarch64_numpy119x_jetsonnano_L4T32.5.1_download.sh

sudo pip3 install \
numpy-1.19.4-cp36-none-manylinux2014_aarch64.whl \
mediapipe-0.8.5_cuda102-cp36-none-linux_aarch64.whl
~~~

2.no module name Tenosrflow error solution
> 텐서플로우를 설치해줘야 한다.  
## 설치 전 환경 설정

+ Install system packages required by TensorFlow
```bash
sudo apt-get update
sudo apt-get install libhdf5-serial-dev hdf5-tools libhdf5-dev zlib1g-dev zip libjpeg8-dev liblapack-dev libblas-dev gfortran
```

+ Install and upgrade pip3
```bash
sudo apt-get install python3-pip
sudo pip3 install -U pip testresources setuptools
```

+ Install the Python package dependencies
```
sudo pip3 install -U numpy==1.19.4 future==0.18.2 mock==3.0.5 h5py==2.10.0 keras_preprocessing==1.1.2 keras_applications==1.0.8 gast==0.2.2 futures protobuf pybind11
```

## Tensorflow install
+ tensorflow 설치
```bash
# version 입력
# 젯팩 4.5 / tensorflow 2.4.0 / nvidia container 21.05
export JP_VERSION=45
export TF_VERSION=2.4.0
export NV_VERSION=21.05

# install command
sudo pip3 install --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v$JP_VERSION tensorflow==$TF_VERSION+nv$NV_VERSION
```


* Version 정보
```bash
$JP_VERSION -> 젯팩 버전
$TF_VERSION -> 텐서플로우 버전
$NV_VERSION -> NVIDIA 컨테이너 버전

젯팩 4.5 version => v45
텐서플로우 2.4.0 => tensorflow==2.4.0
컨테이너 21.05 => nv21.05
```

* 설치 확인
```bash
python3
import tensorflow as tf
```

* 오류 관련
```bash
# tensorflow 버전 호환이 안되는 문제, 다운그레이드하면 해결
# Illegal instruction (core dumped)

# AttributeError: module 'tensorflow' has no attribute 'Session'
# instead of tf.Session()
tf.compat.v1.Session()

# AttributeError: module 'tensorflow' has no attribute 'gfile'
# instead of tf.gfile
tf.compat.v2.io.gfile.GFile()
tf.io.gfile.GFile

# AttributeError: module 'tensorflow' has no attribute 'GraphDef'
# instead of tf.GraphDef()
tf.compat.v1.GraphDef()

# AttributeError: module 'tensorflow' has no attribute 'get_default_graph'
# instead of tf.get_default_graph()
tf.compat.v1.get_default_graph()
```
