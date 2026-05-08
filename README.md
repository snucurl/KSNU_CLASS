# KSNU_CLASS
# ROS2
## Installation on Windows11 with WSL2 and Ubuntu 22.04
Windows 11에서 WSL2(Windows Subsystem for Linux)를 설치하고 Ubuntu 22.04를 WSL2 상에서 운영

### 1. PowerShell을 실행
   
   - [**검색**]에서 **Windows PowerShell**을 입력하고 **관리자 권한으로 실행**을 누름

   - 만약 PowerShell의 버전이 낮다면 최신 버전 7.4.1을 아래 링크를 이용하여 설치(반드시 해야하는 과정은 아님)
  
   - [PowerShell 7.4.1 설치 링크}(https://learn.microsoft.com/ko-kr/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4#msi)

### 2. PowerShell에서의 commands
   
   - wsl --list --online
   
   - wsl --install -d Ubuntu-22.04
   
   - 본인 PC를 재부팅 하고 아래 명령어를 입력
   
   - wsl --status
   
   - wsl --update
  

### 3. Ubuntu 실행

   - [찾기]에서 "터미널"이라고 입력하고 터미널이 나오면 메뉴에서 + 표시 옆의 아래쪽 화살표를 눌러 Ubuntu 22.04.5 LTS를 선택 또는 Ctrl+Shift+5로 우분투 터미널을 생성
   
### 4. ROS2-Humble 설치

   - Ubuntu 22.04 terminal에서 아래 ROS2 Documentation 페이지의 installation 메뉴를 참고하여 설치하면 됨
   - https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html
   - 만약 Humble을 설치하는 도중에 Setup Sources 과정에서 Curl 명령의 에러(Time spent만 있으면 다운로드가 0인 상태)가 지속되면 아래와 같은 과정으로 해결해 볼 것
   - curl -I -4 --connect-timeout 5 --max-time 20 https://github.com
   - curl -I -6 --connect-timeout 5 --max-time 20 https://github.com
   - getent hosts github.com
   - 상기 명령에서 -4는 통과 -6은 실패일 경우에는 아래 명령을 실행
   - sudo sed -i 's/^[#[:space:]]*\(precedence[[:space:]]\+::ffff:0:0\/96[[:space:]]\+100\)/\1/' /etc/gai.conf
   - grep -n "precedence ::ffff:0:0/96" /etc/gai.conf
   - 이후에 다시 Setup Sources 과정을 처음부터 수행
     
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
   - 먼저 파이참 실행 후 File-Settings-Tools-Web Browsers and Preview에서chrome을 체크 해제한 다음 아래의 Apply 버튼을 눌러서 firefox 웹브라우저가 작동하는지 확인하고 작동하지 않을 경우 아래 절차대로 따른다
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

### 10. PyCharm에서 ROS2 패키지 빌드

   - 파이참 실행 후 File-Settings-Tools-External Tools를 선택
   - "+" 기호를 눌러 새로운 External Tools 적용
   - ![image](https://github.com/snucurl/KSNU_CLASS/assets/144347449/f7318d80-8c15-4a21-9757-7687f17470b3)
   - 이후 프로젝트 명에서 우클릭하여 External Tools-Colcon Build를 선택하여 빌드함
   - 빌드 이후에는 Ubuntu 22.04 터미널에서 작업
   - source ~/robot_ws/install/local_setup.bash #빌드되어 설치된 패키지를 등록, 이 작업은 ~/.bashrc에 저장해 놓으면 생략가능
   - ros2 run my_first_ros_rclpy_pkg helloworld_subscriber  #subscriber 실행
   - 새로운 터미널을 연 다음 
   - ros2 run my_first_ros_rclpy_pkg helloworld_publisher # publisher 실행

### 11. TurtleBot3 설치

   - 로보티즈의 아래 동영상을 보고 따라하면 됨

   - [TurtleBot3 설치]([https://www.youtube.com/watch?v=F3n0SMAFheM](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/)

### 12. WSL 안의 Ubuntu 사용자 비밀번호를 잊은 경우

   - WSL Ubuntu를 재설치하지 않고 기존 파일과 개발 환경을 유지한 상태로 sudo 비밀번호만 재설정하는 방법
   - Windows 쪽에서 WSL을 root 사용자로 실행한 뒤 Ubuntu 사용자 비밀번호를 재설정
   - PowerShell 에서 설치된 배포판 확인 : wsl -l -v
   - PowerShell에서 Ubuntu 22.04를 root 사용자로 실행 : wsl -d Ubuntu-22.04 -u root
   - root 쉘에서 사용자(home) 이름 확인 : ls /home
   - 또는 root 쉘에서 현재 등록된 일반 사용자 후보를 보려면 : awk -F: '$3 >= 1000 && $3 < 65534 {print $1}' /etc/passwd
   - root 쉘에서 해당 사용자의 비밀번호 재설정 : passwd kim
   - root 쉘에서 종료 : exit
   - PowerShell에서 다시 Ubuntu를 실행 : wsl -d Ubuntu-22.04
   - Ubuntu 안에서 테스트 : sudo apt update
   - 만약 root로만 접속이 된다면 PowerShell에서 Ubuntu의 기본 사용자를 변경해야 함 : ubuntu2204 config --default-user <사용자이름>

### 13. VS Code 설치
#### 1) Windows용 VS Code 설치
   - VS Code는 Ubuntu 내부가 아니라 Windows에 설치해야 함
   - 설치 중 다음 옵션을 체크. 이 옵션이 있어야 Ubuntu 터미널에서 code . 명령으로 VS Code를 열 수 있음
     --> Add to PATH
    
#### 2) VS Code 확장 설치
  - VS Code 실행 → Extensions에서 다음 확장 설치:
    --> WSL
  - 확장 ID: ms-vscode-remote.remote-wsl 또는 Remote Development extension pack을 설치. 이 확장팩에는 WSL 확장이 포함됨

#### 3) Ubuntu home 디렉토리를 VS Code에서 열기
  - 권장 방식: Ubuntu 터미널에서 열기:
  - cd ~
  - code .
  - Ubuntu 터미널에서 열고 싶은 폴더로 이동한 뒤 code .를 실행. 처음 실행 시 VS Code가 WSL 내부에 필요한 서버 구성요소를 설치.
  - mkdir -p ~/workspace
  - cd ~/workspace  --> 권장 작업폴더 위치
  - code .

#### 4) PowerShell에서 바로 열기
  - code --remote wsl+Ubuntu /home/<Ubuntu사용자명>/workspace

