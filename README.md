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
2.
