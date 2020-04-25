# 1. Get into the Shell

## 1) Virtual Machine (VM)

### (1) VM?

- 가상의 컴퓨터를 만들어주는 프로그램
  - `host OS` : 실제 컴퓨터에 직접 설치되어 있는 OS 
  - `guest OS` : VM 상에 설치되어 있는 OS

- VM 의 필요성
  - 실제 컴퓨터로부터 프로젝트를 완전히 분리시킴으로써 기존의 컴퓨터 환경에 어떠한 변화 없이 프로젝트만을 위한 새로운 환경을 설정할 수 있음
  - 개발 환경과 배포 환경을 일치시킬 수 있음

- 준비사항
  - [VirtualBox](https://www.virtualbox.org/wiki/Downloads) :VM software
    - OS 에 맞는 *platform package* 설치
  - [Vagrant](https://www.vagrantup.com/downloads.html) : VM 사용 편리성을 높여주는 프로그램
    - OS 에 맞게끔 설치
    - `vagrant up` 명령어를 통해 `Vagrantfile` 상의 설정에 따라 VM 생성, guest OS 설치 및 환경 설정을 자동으로 수행
    - host OS 에서 VM 상의 파일을 수정하기 용이하게끔
  - [Vagrantfile](https://www.udacity.com/api/nodes/4713348570/supplemental_media/vagrantfile/download) : Udacity 강의에서 제공하는 설정 파일

- VM 실행

```bash
# Vagrantfile 이 위치한 디렉토리로 이동

vagrant up # Linux OS 다운로드, VM 실행
vagrant ssh
```

- shell commands

  - `vagrant up` : VM 실행
  - `vagrant ssh` : 로그인

  ![image-20200425151457220](/Users/eunjung/Documents/CS_learning/OS/udacity_linux_command_line_basics/images//image-20200425151457220.png)

  - `exit` or `ctrl + d` : 로그아웃

  ![image-20200425151519433](/Users/eunjung/Documents/CS_learning/OS/udacity_linux_command_line_basics/images//image-20200425151519433.png)

  - `ctrl + c` : 커맨드 종료

- **command name (command line arguments: optional)**

  - `ls` : 폴더/파일 목록 출력
  - `curl` : 웹에서 파일 다운로드
  - `date` : 현재 날짜, 시간 정보 출력
  - `host udacity.com` : 입력한 도메인의 IP 주소 및 기타 정보 출력
  - `echo you rock` : 입력한 command line arguments 를 그대로 출력
  - `history` : 지금까지 입력했던 명령어 히스토리 출력
  - `hostname` : 컴퓨터 이름 출력
  - `expr 2 + 2` : 계산 결과 출력 
  - `bash --version` : bash 정보 출력
  - `uname` : 실행 중인 OS 이름 출력
  - `rm [파일명]` : 파일 삭제 (`os.remove(파일명)`: 파이썬)

- **terminal VS shell**
  - 사용자로부터 텍스트 인풋을 받아 그에 따른 아웃풋을 표시해주는 프로그램
  - **shell 은 터미널이 받은 input을 해석, 그에 따른 작업을 수행하여 output을 터미널로 전달**
    - 다양한 shell 프로그램이 존재 (Bourne shell: sh, C shell: csh, Korn shell: ksh, Z shell: zsh, bash 등)
    - **shell scripting** : terminal 없이 shell command를 파일에 작성하고 shell 프로그램을 통해 실행