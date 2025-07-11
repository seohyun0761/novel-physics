## 📘 2학년 프로젝트
# 젯슨나노

![화면 캡처 2024-09-06 152822](https://github.com/user-attachments/assets/99dc679c-98e3-477e-9ae4-8ffc1b121021)

Getting Started with AI on Jetson Nano 

**1. Jetson Nano Setting 준비물**
  
    - jetson nano 4gb

    - c type power adapter
  
    - 와이파이 동글
  
    - 웹캠(USB Camera), 또는 CSI Camera (라즈베리파이 V2)
  
    - 64기가 이상 마이크로sd카드

    - 그외 쿨링펜, lcd, 또는 모니터. hdmi
    
    
**2. jetson nano에 대하여**

welcome 부터 따라하기 https://learn.nvidia.com/courses/course?course_id=course-v1:DLI+S-RX-02+V2&unit=block-v1:DLI+S-RX-02+V2+type@vertical+block@aba5104413ae454c8c63a6f301925337


**3. jetpack downloads**

https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write


**4. 이미지 굽기 위해 필요한 것들**
~~~ bash
   4-1. sd card formatter  download
   4-2. balenaetcher download --->  이미지 굽기
   4-3. 제슨나노에 sd넣고 우분투 설치
~~~
   ![화면 캡처 2024-09-06 155525](https://github.com/user-attachments/assets/bcdcb8d9-fb5f-41c5-9e2e-9795195f973e)
![화면 캡처 2024-09-06 155559](https://github.com/user-attachments/assets/fbbbe0aa-65b6-4a21-9226-9f866e05de58)

**5. 제슨 알아보고 설치하기**

https://developer.nvidia.com/embedded/learn/jetson-nano-2gb-devkit-user-guide#id-.JetsonNano2GBDeveloperKitUserGuidevbatuu_v1.0-DeveloperKitSetup

5. image classification - Thumbs Project using ResNet

https://learn.nvidia.com/courses/course?course_id=course-v1:DLI+S-RX-02+V2&unit=block-v1:DLI+S-RX-02+V2+type@vertical+block@aabe204272214ba69309581d388b0734

5. image regression - Face XY Project

https://learn.nvidia.com/courses/course?course_id=course-v1:DLI+S-RX-02+V2&unit=block-v1:DLI+S-RX-02+V2+type@vertical+block@76a2873eb69946b4928c4f8432e04314

**6. 우분투 설치**
![화면 캡처 2024-09-06 155949](https://github.com/user-attachments/assets/cb433d38-ba60-4c78-a176-b7599c58a733)
![화면 캡처 2024-09-06 160039](https://github.com/user-attachments/assets/094353d3-69bf-4f8c-b62a-2bdfb6b8f9a7)
![화면 캡처 2024-09-06 160119](https://github.com/user-attachments/assets/d177b14f-35a4-4e24-8d16-b48dddf138aa)

**7.쿨링팬 설치와 jtop**
>jtop : system monitoring tool

terminal 열기
~~~ bash
dli@dli-desktop:~$ sudo apt install python3-pip
 --컴퓨터가 물어본다   do you want to continue ? Y
dli@dli-desktop:~$  sudo -H pip3 install -U jetson-stats

sudo apt-get upgrade
sudo apt-get update
sudo apt install python3-pip

do you want to continue? Y
sudo-Hpip3install-Ujetson-stats
~~~



# 데이터 크롤링(data crawling)
1.Chrome 설치

2.크롤링 프로그램 다운로드
Terminal에서
~~~ blsh
>> git clone https://github.com/YoongiKim/AutoCrawler
>> cd AutoCrawler
~~~

3.크롤링에 필요한 패키지 설치
~~~ bash
pip install -r requirements.txt
~~~


4.다운로드할 키워드 입력
AutoCrawler-master 폴더 안의 keywords.txt을 연다.     
검색하고하는 키워드를 한 줄에 한 개씩 쓴 후 저장. 
안되면 메모장에

예시)
감자 /
토마토 /
고구마

5.크롤링 실행
~~~ bash
python main.py
~~~
사진 개수를 20개로 제한
~~~ bash
 python main.py --limit 20
~~~


# yolo 가상환경 만들기
yolo는 3.8파이썬이 필요하지만 젯슨은 3.6까지 가능 그래서 가상환경 필요


    uname -a
    wget https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh
    sudo chmod 755 Archiconda3-0.2.3-Linux-aarch64.sh
    ls
 - .sh 명령어는 쉘 스크립트를 실행하는 명령어로, 주로 자동화된 작업을 처리할 때 사용된다.
 - wget 명령어는 터미널에서 파일을 웹에서 다운로드할 때 사용하는 명령어이다.
##### 결과

  Archiconda3-0.2.3-Linux-aarch64.sh Pictures Desktop Public Documents Templates Downloads Videos examples.desktop yolov8_4gb Music

     ./Archiconda3-0.2.3-Linux-aarch64.sh
실행 중 선택이라 뜨면
yes---> enter ---> yes in your /home/ldh/.bashrc ? [yes|no] [no] >>> yes
이렇게 한다.

    conda env list
    conda activate base
    jetson_release 

    
### python 3.8 가상환경 만들기
***
base가 아닌 native에서 실행

    conda deactivate
 - 가상환경에서 빠져 나오는 명령어임
   
 ```
conda create -n yolo python=3.8 -y
conda env list
conda activate yolo
 ```

 - "conda activate yolo"를 실행하여 yolo 가상환경으로 진입해서 pytorch, torchvosion을 설치하는 과정
 - 결과 가상에서 설치 torch, torvosion 다운로드
 - torch은 과학 계산과 머신러닝 알고리즘을 지원하는 프레임워크이며, 주로 PyTorch로 알려진 딥러닝 라이브러리에서 사용
 - Torchvosion은 PyTorch에서 컴퓨터 비전 작업을 쉽게 하기 위한 라이브러리로, 이미지 처리용 데이터셋, 모델, 전처리 도구를 제공

(yolo) dli@dli:~$
```
pip install -U pip wheel gdown
```
```
gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM
```
![IMG_0543](https://github.com/user-attachments/assets/70cda6f3-3c8c-49f8-a4c7-60ea7a86996e)

```
gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV
```
![IMG_0544](https://github.com/user-attachments/assets/ea45073d-dd77-4150-a563-50f0bb8db702)

 
아래 두 라인을 실행(library 설치) 후 torch, torchvision은 확인이 가능하였다.

```
sudo apt-get install libopenblas-base libopenmpi-dev
sudo apt-get install libomp-dev
pip install torch-1.11.0a0+gitbc2c6ed-cp38-cp38-linux_aarch64.whl
pip install torchvision-0.12.0a0+9b5a3fe-cp38-cp38-linux_aarch64.whl
python -c "import torch; print(torch.__version__)"
```

만약 오류가 발생 한다면 numpy 설치가 제대로 되지않은것이므로 수동으로 설치해준다.

```
conda install numpy
```

```

(yolo) dli@dli:~$ python

>>> import torch
>>> import torchvision
>>> print(torch.__version__)
>>> print(torchvision.__version__)
>>> print("cuda used", torch.cuda.is_available())
cuda used True
>>>
```
```
git clone https://github.com/Tory-Hwang/Jetson-Nano2
```

```
cd Jetson-Nano2/
```
```
cd V8
```
```
pip install ultralytics
```
```
pip install -r requirements.txt
```
```
pip install ffmpeg-python
```
```
sudo apt install tree
```
```
tree -L 2
```
![image](https://github.com/user-attachments/assets/46b318d6-3213-416e-8762-06edb70e23ec)


결과



 - 다 했으면 https://github.com/ultralytics/ultralytics?tab=readme-ov-file 이 링크에서
YOLOv8n을 다운 받는다. 그리고 그 파일의 경로만 알아두면 된다.
1. 내 컴퓨터
2. Jetson-nano2
3. V8
4. detectY8.py
5. brtsp = True 라고 되어있는 것을 brtsp = False로 바꾼다.

이제 v8 파일로 가서
```
python3 detectY8.py
```
이렇게 하면 카메라가 화면에 뜬다



https://github.com/user-attachments/assets/0857dfb9-84d8-4756-97f6-cdb7c37c7005

## 📗 3학년 프로젝트



