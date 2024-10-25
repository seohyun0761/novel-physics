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

#### yolo 가상환경 만들기

#### 잿슨나노의 기본세팅이 되어있다는 전제하에 진행하도록 하겠습니다.
기본세팅의 자세한 사항은 https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write 에서 확인해주세요.

""참고 링크 https://github.com/jetsonmom/yolov8_jetson4GB?tab=readme-ov-file   ,    https://cyb.tw/docs/Tech/2020/9/18_Install-anaconda-on-Jetson-Nano.html#install-archiconda ""
```
sudo apt update
sudo apt upgarde
```
가장 먼저 업데이트 업그레이드를 한다.

아나콘다를 다운하고 실행파일에 권한을 준다.
```
uycgb
uname -a
wget https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh
sudo chmod 755 Archiconda3-0.2.3-Linux-aarch64.sh
```
해당 파일을 실행한다
```
 ./Archiconda3-0.2.3-Linux-aarch64.sh
```
실행후 Enter 키를 눌러 다음으로 넘어가고 YES를 입력하라는 메세지가 나오면 YES를 입력한다 그에 따른 결과값이 다음과 같다.
```
###### result 
ldh@ldh-desktop:~$  ./Archiconda3-0.2.3-Linux-aarch64.sh

Welcome to Archiconda3 0.2.3

In order to continue the installation process, please review the license
agreement.
Please, press ENTER to continue
>>> q
Copyright (c) 2016-2017 Jonathan J. Helmus
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

    * Redistributions of source code must retain the above copyright
       notice, this list of conditions and the following disclaimer.

    * Redistributions in binary form must reproduce the above
       copyright notice, this list of conditions and the following
       disclaimer in the documentation and/or other materials provided
       with the distribution.

    * Neither the name of the developers nor the names of any
       contributors may be used to endorse or promote products derived
       from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
"AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


Do you accept the license terms? [yes|no]
[no] >>> 
Please answer 'yes' or 'no':'
>>> yes

Archiconda3 will now be installed into this location:
/home/ldh/archiconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below

[/home/ldh/archiconda3] >>> 
PREFIX=/home/ldh/archiconda3
installing: python-3.7.1-h39be038_1002 ...
Python 3.7.1
installing: ca-certificates-2018.03.07-0 ...
installing: conda-env-2.6.0-1 ...
installing: libgcc-ng-7.3.0-h5c90dd9_0 ...
installing: libstdcxx-ng-7.3.0-h5c90dd9_0 ...
installing: bzip2-1.0.6-h7b6447c_6 ...
installing: libffi-3.2.1-h71b71f5_5 ...
installing: ncurses-6.1-h71b71f5_0 ...
installing: openssl-1.1.1a-h14c3975_1000 ...
installing: xz-5.2.4-h7ce4240_4 ...
installing: yaml-0.1.7-h7ce4240_3 ...
installing: zlib-1.2.11-h7b6447c_2 ...
installing: readline-7.0-h7ce4240_5 ...
installing: tk-8.6.9-h84994c4_1000 ...
installing: sqlite-3.26.0-h1a3e907_1000 ...
installing: asn1crypto-0.24.0-py37_0 ...
installing: certifi-2018.10.15-py37_0 ...
installing: chardet-3.0.4-py37_1 ...
installing: idna-2.7-py37_0 ...
installing: pycosat-0.6.3-py37h7b6447c_0 ...
installing: pycparser-2.19-py37_0 ...
installing: pysocks-1.6.8-py37_0 ...
installing: ruamel_yaml-0.15.64-py37h7b6447c_0 ...
installing: six-1.11.0-py37_1 ...
installing: cffi-1.11.5-py37hc365091_1 ...
installing: setuptools-40.4.3-py37_0 ...
installing: cryptography-2.5-py37h9d9f1b6_1 ...
installing: wheel-0.32.1-py37_0 ...
installing: pip-10.0.1-py37_0 ...
installing: pyopenssl-18.0.0-py37_0 ...
installing: urllib3-1.23-py37_0 ...
installing: requests-2.19.1-py37_0 ...
installing: conda-4.5.12-py37_0 ...
installation finished.
Do you wish the installer to initialize Archiconda3
in your /home/ldh/.bashrc ? [yes|no]
[no] >>> yes

Initializing Archiconda3 in /home/ldh/.bashrc
A backup will be made to: /home/ldh/.bashrc-archiconda3.bak


For this change to become active, you have to open a new terminal.

Thank you for installing Archiconda3!
```

결과가 잘나왔으면 다음 명령어를 입력한다.

```
conda env list
conda activate base
jetson_release 
```

이후 python3.8. 가상환경을 만들고 욜로 가상환경을 만들어 들어간다.

```
conda create -n yolo python=3.8 -y
conda env list
```
```
conda activate yolo
```

욜로 가상환경에 들어오면  (yolo)dli@dliL~$ 과 같이 나타날 것이다.

```
 pip install -U pip wheel gdown

 gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM

 gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV
```
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
트리를 실행하면 다음과 같은 결과가 나와야한다.

![image](https://github.com/moon-joy/Jetson-nano/assets/171406702/7c4b161b-5c27-40d6-a1b8-8eb1ec1ac9b3)

이후 https://github.com/ultralytics/ultralytics?tab=readme-ov-file 이 링크에서 yolov8n.py를 다운로드 해준다. 경로는 (yolo) dli@jetson:~/Jetson-Nano2/V8 이다.

![image](https://github.com/moon-joy/Jetson-nano/assets/171406702/86595bc6-3a20-4390-b2aa-42371a5c4c87)

이제 파일을 실행시켜 주기만하면 된다. 

```
python detectY8.py
```
이떄 경로는 (yolo) dli@jetson:~/Jetson-Nano2/V8 로 디렉토리 안에 들어가서 명령어를 쳐야 실행된다.

만약 오류가 발생한다면  detectY8.py 파일의 코드를 수정해야한다. 


![image](https://github.com/moon-joy/Jetson-nano/assets/171406702/89a2570f-bc42-4539-af35-9cbc9b143529)

detectY8.py에 들어가서 사진과 같은 코드를 찾아 수정하고 다시 실행하면 된다.

작동 결과는 유튜브에서 확인 가능하다. https://youtu.be/HxUnThdKvtA?si=D56TcjKOtVIDa_Bg 
