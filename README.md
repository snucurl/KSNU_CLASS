# KSNU_CLASS
# ROS2
## Installation on Windows11 with WSL2 and Ubuntu 22.04
Windows 11에서 WSL2(Windows Subsystem for Linux)를 설치하고 Ubuntu 22.04를 WSL2 상에서 운영

### 1. PowerShell을 실행
   
   - [**검색**]에서 **Windows PowerShell**을 입력하고 **관리자 권한으로 실행**을 누름

   - 만약 PowerShell의 버전이 낮다면 최신 버전 7.4.1을 아래 링크를 이용하여 설치
  
   - [PowerShell 7.4.1 설치 링크}(https://learn.microsoft.com/ko-kr/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4#msi)

### 2. PowerShell에서의 commands
   
   - wsl --install
   
   - wsl --list --online
   
   - wsl --install -d Ubuntu-22.04
   
   - 재부팅
   
   - wsl --status
   
   - wsl --update
  

### 3. Ubuntu 실행

   - [검색]에서 WSL을 찾아 실행시키거나 **윈도우키**를 눌러 [맞춤]에서 **Ubuntu 22.04.3 LTS**를 우클릭한 다음 **관리자 권한으로 실행**을 선택

   - 사용할 계정과 패스워드를 입력

### 4. ROS2-Humble 설치

   - Ubuntu 22.04 terminal에서 아래 ROS2 Documentation 페이지의 installation 메뉴를 참고하여 설치하면 됨
   - https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html
     
### 5. PyCharm 설치

   - Ubuntu 22.04 terminal에서 아래 Jetbrains 홈페이지에서 리눅스 버전의 PyCharm을 다운로드
   - 홈디렉토리에서 아래 명령어들을 입력
   - wget https://download-cdn.jetbrains.com/python/pycharm-professional-2024.1.1.tar.gz #다운로드
   - tar xvf pycharm-professional-2024.1.1.tar.gz
   - cd pycharm-2024.1.1/bin
   - sh pycharm.sh #파이참 실행
   - 학교 이메일(@kunsan.ac.kr)로 만든 JetBrains Account를 이용해서 activate 실행
   - 웹브라우저가 작동하지 않을 경우에는 trial 버전으로 먼저 실행 후 나중에 activate 실행

### 6. PyCharm에서 ROS2 환경의 Python 설정 방법
   
   - PyCharm 실행 후 File-Settings-Project:ProjectName-Python Interpreter를 선택
   - Python Interpreter의 오른쪽에 있는 Add Interpreter를 선택하여 Add Local Interpreter를 선택
   - 왼쪽 메뉴에서 System Interpreter를 선택하고 Interpreter에서 /usr/bin/python3를 선택
   - 터미널에서 home directory로 이동 cd ~

### 7. PyCharm에서 JetBrains 계정 활성화 방법

   - Ubuntu 22.04 terminal에서 아래 명령어들을 순서대로 입력
   (1) 웹브라우저인 firefox 설치
   - sudo apt update
   - sudo apt upgrade
   - sudo apt install firefox
   - firefox &

   (2) 웹브라우저 firefox 실행 확인 후 PyCharm에서의 설정
   - 파이참 실행 후 File-Settings-Tools-Web Browsers and Preview에서 firefox의 Path를 /usr/bin/firefox로 수정
   - 파이참 실행 후 File-Settings-Settings Sync 메뉴에서 Login with JetBrains Account를 실행하여 license activation
   - 로그인을 위한 대화창이 뜨면 버튼을 클릭하여 JetBrains 로그인 페이지로 이동
   - 학교계정 이메일과 JetBrains에 가입할 때 사용한 비밀번호를 입력하면 Professional version activation 완료
     
### 8. GitHub 계정 생성

   - https://github.com/ 으로 이동
   - 본인의 계정을 새로 생성
   - public repository를 생성해서 작성한 코드를 commit

### 9. Source codes 다운로드

   - Ubuntu 22.04 terminal에서 아래의 명령어를 수행
   - sudo apt update
   - sudo apt install git
   - git --version
   - git config --global user.name "본인 계정"
   - git config --global user.email "본인 이메일 주소"
   - sudo git config --global color.ui "auto"
   - git config --list
   - git clone https://github.com/robotpilot/ros2-seminar-examples.git
   - 다운로드 완료 후 아래 명령어로 필요한 package만 복사
   - cp -r ~/ros2-seminar-examples/my_first_ros_rclpy_pkg ~/robot_ws/src/my_first_ros_rclpy_pkg
   - cd ~/robot_ws/src/my_first_ros_rclpy_pkg
   - ll
