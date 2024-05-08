---
title: wsl 2에서 Kali-Linux 설치 시 주의점
date: 2024-05-08 16:39:42 +09:00
categories: [
    Computer_Science,
    Network,
    Information_Security,
    Operation_System,
]
tags: [
    CS,
    정보보안,
    OS,
    Kali-Linux,
]
---

### WSL에서 Kali Linux 사용 시 발생하는 사소하지만 짜증나던 문제점


WSL(Windows Subsystem for Linux)에서 Kali Linux를 사용하면서 겪었던 문제와 그 해결 방법에 대해 이야기하려고 합니다.

WSL에서 Kali Linux를 설치하고 여러 가지 작업을 시도하다 보면 패키지 업데이트와 업그레이드를 진행할 때 문제가 발생하는 경우가 있습니다.

다음과 같이 범용적인 Linux 패키지 업데이트 & 업그레이드 명령어를 사용할텐데

```bash
sudo apt update && sudo apt upgrade -y
```

가끔, 이 명령어를 실행하면 설치 과정 중에 WSL이 갑자기 멈추는 문제가 발생하기도 합니다. 

개인적인 생각으론 WSL에서 systemd를 제대로 사용하지 못하는 경우가 있는 것 같습니다. 그래서 WSL에서 systemd를 사용하도록 설정해주기 위해,

```bash
sudo vi /etc/wsl.conf
```

`wsl.conf` 파일을 생성하거나 열어서

```bash
[boot]
systemd=true
```

systemd를 사용하게 적어주면 됩니다.

에디터 취향에 따라서 code나 notepad를 사용하셔도 무방합니다.

이 설정을 저장하고 WSL을 재시작하면, 이제 패키지 업데이트와 업그레이드를 정상적으로 진행할 수 있게 됩니다.