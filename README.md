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
