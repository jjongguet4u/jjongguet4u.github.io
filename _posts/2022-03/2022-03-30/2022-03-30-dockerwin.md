---
layout: post
title:  "Wsl + Docker 환경설정"
categories: dev
tags: container
comments: true
---

# WSL

---

1. windows terminal 설치

2. terminal에서 실행
    
    `dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`
    
    `dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`
    
3. 재부팅 진행

4. wsl2로 업데이트(설치)
    
    [https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) 
    
5. Terminal에서 실행
    
    `wsl —set-default-version 2`
    
6. Microsoft store에서 Ubuntu 설치

- wsl 버전 확인하기 및 업데이트
    
    `wsl -l -v` 에서 version 1인경우에만 진행
    
    `wsl —set-version Ubuntu 2`
    

## 번외 : 항상 관리자권한으로 실행

---

1. 레지스트리 수정
    
    windows r → regedit →
    
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System 에서 EnableLUA 값을 1 에서 0 으로 수정함
    
2. 재부팅진행
    
    출처 : [https://sosohanbox.tistory.com/304](https://sosohanbox.tistory.com/304)
    

## Docker

---

> 해당방식은 Docker Desktop설치 이후, 해당 내용을 WSL2에 연결해서 사용하는 방식입니다.
백그라운드 램이슈가 있는것같으니 꼭 확인해야합니다.
> 
1. 도커 데스크탑 다운로드
    
    [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop) 
    
2. 추가세팅

Settings → Resources → WSL INTEGRATION

Enable Integraion with my default WSL distro (체크하기)

Ubuntu-18.04 (체크하기)
3. terminal로 wsl2로 ubuntu 들어가서
    
    `docker version` ( 제대로 나오는지 확인)
    
    `kubectl version` ( 클라이언트 버전만 나오는지 확인. 아직 커넥션 안되어있음)
    
