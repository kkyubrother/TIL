# Jetson Nano 기본 프로그램 설치
```console
sudo apt update
sudo apt upgrade -y
```
## Jetson stats
```console
sudo apt install python3 python3-pip
sudo -H pip install -U jetson-stats
sudo reboot
```
[출처](https://github.com/rbonghi/jetson_stats)
## OpenCV 설치(compiled CUDA)
### SWAP 설정(Ubuntu Swap 설정)
1. 스왑 파일 생성
```console
sudo fallocate -l 8G /swapfile
```
2. 스왑 파일 권한 변경
```console
sudo chmod 600 /swapfile
```
3. 스왑 동작 설정
```console
sudo mkswap /swapfile
```
4. 스왑 활성화
```console
sudo swapon /swapfile
```
5. 재부팅 이후에도 적용하기 위해서는 /etc/fstab 파일 수정
```console
sudo nano /etc/fstab
```
6. 파일 하단에 추가
```console
/swapfile swap swap defaults 0 0
```
7. 재부팅
```console
sudo reboot
```

[출처](https://psychoria.tistory.com/717)

### 컴파일 및 설치

```console
wget https://github.com/Qengineering/Install-OpenCV-Jetson-Nano/raw/main/OpenCV-4-5-4.sh
sudo chmod 755 ./OpenCV-4-5-4.sh
./OpenCV-4-5-4.sh
```
[출처](https://qengineering.eu/install-opencv-4.5-on-jetson-nano.html)

### 설치 확인
1. Jetson stats 에서 확인 가능
2. `python3 -c import cv2;print(cv2.__version__)`

## PyTorch, torchvision
```console
sudo apt-get install libopenblas-base libopenmpi-dev libomp-dev python3-pip
pip3 install Cython
pip3 install numpy torch-1.6.0-cp36-cp36m-linux_aarch64.whl
```
[출처](https://elinux.org/Jetson_Zoo)

## TensorFlow
[확인](https://elinux.org/Jetson_Zoo#TensorFlow)

# 간편하게 사용하기(with Docker)
1. 다운로드
```console
sudo docker pull nvcr.io/nvidia/l4t-ml:r34.1.0-py3
```
2. 실행
```console
sudo docker run -it --rm --runtime nvidia --network host nvcr.io/nvidia/l4t-ml:r34.1.0-py3
```
3. 접속 (http://{jetson ip}:8888), 기본 비밀번호는 `nvidia`
4. 호스트 장치와 디렉터리 연결하기
```console
# /path/in/host : 호스트 경로
# /path/in/container : 컨데이너 경로
sudo docker run -it --rm --runtime nvidia --network host -v /path/in/host:/path/in/container nvcr.io/nvidia/l4t-ml:r34.1.0-py3
```