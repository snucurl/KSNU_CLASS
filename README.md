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

   - Ubuntu 22.04 terminal에서 아래 동영상을 보고 따라하면 됨

   - [ROS2 Humble 설치 유튜브 동영상](https://www.youtube.com/watch?v=F3n0SMAFheM)
