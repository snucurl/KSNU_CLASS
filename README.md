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
   - 홈디렉토리에서 download 폴더를 생성
   - cd download
   - wget https://download-cdn.jetbrains.com/python/pycharm-professional-2024.1.1.tar.gz #다운로드
   - tar xvf pycharm-professional-2024.1.1.tar.gz
   - cd pycharm-2024.1.1/bin
   - sh pycharm.sh
   - 학교 이메일(@kunsan.ac.kr)로 만든 JetBrains Account를 이용해서 activate 실행
   - 
