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

![image](https://github.com/user-attachments/assets/46b318d6-3213-416e-8762-06edb70e23ec)

dli@dli-desktop:~$ cd Jetson-Nano2/
dli@dli-desktop:~/Jetson-Nano2$ cd V8
dli@dli-desktop:~/Jetson-Nano2/V8$ pip install ultralytics
Collecting ultralytics
  Downloading https://files.pythonhosted.org/packages/9e/a9/96ec571cbcc52655bd463f9ca269ba4c689a41ac32cbc0bd48bf5827ab07/ultralytics-8.0.151-py3-none-any.whl (616kB)
    100% |████████████████████████████████| 624kB 1.7MB/s 
Collecting torch>=1.7.0 (from ultralytics)
  Could not find a version that satisfies the requirement torch>=1.7.0 (from ultralytics) (from versions: )
No matching distribution found for torch>=1.7.0 (from ultralytics)
Cache entry deserialization failed, entry ignored
You are using pip version 10.0.1, however version 24.0 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
dli@dli-desktop:~/Jetson-Nano2/V8$ pip install -r requirements.txt
Collecting matplotlib>=3.2.2 (from -r requirements.txt (line 5))
  Downloading https://files.pythonhosted.org/packages/02/81/e8276ec6ca005b3b2bfaaad0ea47dbb3a0e389ec8ab87d08e3ccbe4b2742/matplotlib-3.5.3.tar.gz (35.2MB)
    100% |████████████████████████████████| 35.2MB 633kB/s 
    Complete output from command python setup.py egg_info:
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/tmp/pip-install-n7yu10oy/matplotlib/setup.py", line 349, in <module>
        "sdist": Sdist,
      File "/home/dli/archiconda3/lib/python3.7/site-packages/setuptools/__init__.py", line 139, in setup
        _install_setup_requires(attrs)
      File "/home/dli/archiconda3/lib/python3.7/site-packages/setuptools/__init__.py", line 134, in _install_setup_requires
        dist.fetch_build_eggs(dist.setup_requires)
      File "/home/dli/archiconda3/lib/python3.7/site-packages/setuptools/dist.py", line 514, in fetch_build_eggs
        replace_conflicting=True,
      File "/home/dli/archiconda3/lib/python3.7/site-packages/pkg_resources/__init__.py", line 777, in resolve
        replace_conflicting=replace_conflicting
      File "/home/dli/archiconda3/lib/python3.7/site-packages/pkg_resources/__init__.py", line 1060, in best_match
        return self.obtain(req, installer)
      File "/home/dli/archiconda3/lib/python3.7/site-packages/pkg_resources/__init__.py", line 1072, in obtain
        return installer(requirement)
      File "/home/dli/archiconda3/lib/python3.7/site-packages/setuptools/dist.py", line 581, in fetch_build_egg
        return cmd.easy_install(req)
      File "/home/dli/archiconda3/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 676, in easy_install
        return self.install_item(spec, dist.location, tmpdir, deps)
      File "/home/dli/archiconda3/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 702, in install_item
        dists = self.install_eggs(spec, download, tmpdir)
      File "/home/dli/archiconda3/lib/python3.7/site-packages/setuptools/command/easy_install.py", line 873, in install_eggs
        os.path.abspath(dist_filename)
    distutils.errors.DistutilsError: Couldn't find a setup script in /tmp/easy_install-u5xpaer4/numpy-2.1.2.tar.gz
    
    Edit mplsetup.cfg to change the build options; suppress output with --quiet.
    
    BUILDING MATPLOTLIB
          python: yes [3.7.1 | packaged by conda-forge | (default, Feb 26 2019,
                      04:21:53)  [GCC 7.3.0]]
        platform: yes [linux]
           tests: no  [skipping due to configuration]
          macosx: no  [Mac OS-X only]
    
    
    ----------------------------------------
Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-install-n7yu10oy/matplotlib/
You are using pip version 10.0.1, however version 24.0 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
dli@dli-desktop:~/Jetson-Nano2/V8$ pip install ffmpeg-python
Collecting ffmpeg-python
  Downloading https://files.pythonhosted.org/packages/d7/0c/56be52741f75bad4dc6555991fabd2e07b432d333da82c11ad701123888a/ffmpeg_python-0.2.0-py3-none-any.whl
Collecting future (from ffmpeg-python)
  Downloading https://files.pythonhosted.org/packages/da/71/ae30dadffc90b9006d77af76b393cb9dfbfc9629f339fc1574a1c52e6806/future-1.0.0-py3-none-any.whl (491kB)
    100% |████████████████████████████████| 491kB 1.3MB/s 
Installing collected packages: future, ffmpeg-python
Successfully installed ffmpeg-python-0.2.0 future-1.0.0
You are using pip version 10.0.1, however version 24.0 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
dli@dli-desktop:~/Jetson-Nano2/V8$ sudo apt install tree
[sudo] password for dli: 
Sorry, try again.
[sudo] password for dli: 
Sorry, try again.
[sudo] password for dli: 
sudo: 3 incorrect password attempts
dli@dli-desktop:~/Jetson-Nano2/V8$ tree -L 2
.
├── CITATION.cff
├── coco128_kor.yaml
├── coco128.yaml
├── coco_names_kor.txt
├── CONTRIBUTING.md
├── detectY8.py
├── docker
│   ├── Dockerfile
│   ├── Dockerfile-arm64
│   └── Dockerfile-cpu
├── docs
│   ├── app.md
│   ├── assets
│   ├── callbacks.md
│   ├── cfg.md
│   ├── cli.md
│   ├── CNAME
│   ├── engine.md
│   ├── hub.md
│   ├── index.md
│   ├── predict.md
│   ├── python.md
│   ├── quickstart.md
│   ├── README.md
│   ├── reference
│   ├── SECURITY.md
│   ├── stylesheets
│   └── tasks
├── examples
│   ├── README.md
│   ├── tutorial.ipynb
│   ├── YOLOv8-CPP-Inference
│   └── YOLOv8-OpenCV-ONNX-Python
├── LICENSE
├── MANIFEST.in
├── mkdocs.yml
├── output_video.mp4
├── predict - 복사본.py
├── README.md
├── README.zh-CN.md
├── RealSteam.py
├── requirements.txt
├── sample.jpg
├── sample.mp4
├── setup.cfg
├── setup.py
├── test2.py
├── test3.py
├── test.py
├── tests
│   ├── test_cli.py
│   ├── test_engine.py
│   └── test_python.py
├── ultralytics
│   ├── assets
│   ├── hub
│   ├── __init__.py
│   ├── models
│   ├── nn
│   ├── __pycache__
│   ├── tracker
│   └── yolo
└── yolov8n.pt

18 directories, 45 files

