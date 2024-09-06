# 데이터 크롤링(data crawling)
1.Chrome 설치

2.크롤링 프로그램 다운로드
- Terminal에서
>> git clone https://github.com/YoongiKim/AutoCrawler
>> cd AutoCrawler

3.크롤링에 필요한 패키지 설치
>> pip install -r requirements.txt

4.다운로드할 키워드 입력
AutoCrawler-master 폴더 안의 keywords.txt을 연다
검색하고하는 키워드를 한 줄에 한 개씩 쓴 후 저장

예시)
감자 /
토마토 /
고구마

5.크롤링 실행
>> python main.py

>> python main.py --limit 20
20로 재한
# yolo 가상환경 만들기
yolo는 3.8파이썬이 필요하지만 젯슨은 3.6까지 가능 그래서 가상환경 필요



       wget https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh
       sudo chmod 755 Archiconda3-0.2.3-Linux-aarch64.sh
       ls
wget 네트웨크 파일 다운 도구 / 
sudo chmod 755 파일이나 디렉토리의 권한을 설정하는 명령어



       ldh@ldh-desktop:~$  ./Archiconda3-0.2.3-Linux-aarch64.sh
Archiconda3 conda를 통해 파이썬 환경과 패키지를 관리



        dli@dli-desktop:~$ sudo chmod 755 Archiconda3-0.2.3-Linux-aarch64.sh
        [sudo] password for dli: 
        dli@dli-desktop:~$ ./Archiconda3-0.2.3-Linux-aarch64.sh 


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
        THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT. 
        (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
        OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


       Do you accept the license terms? [yes|no]
       [no] >>> 
       Please answer 'yes' or 'no':'
       >>> yes

      Archiconda3 will now be installed into this location:
      /home/dli/archiconda3

       - Press ENTER to confirm the location
       - Press CTRL-C to abort the installation
       - Or specify a different location below

      [/home/dli/archiconda3] >>> archiconda3
ERROR: File or directory already exists: 'archiconda3'
If you want to update an existing installation, use the -u option.
dli@dli-desktop:~$ 
