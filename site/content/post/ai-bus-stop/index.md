
---
title: "AI 기반 시각장애인 버스 정류장 안내 시스템"
description: "컴퓨터 비전과 임베디드 시스템을 활용한 버스 안내 프로젝트"
date: 2026-11-01
draft: false
categories:
    - Projects
tags:
    - Raspberry Pi
    - Arduino
    - YOLO
    - OpenCV
---


## Project Overview

### 프로젝트 소개

본 프로젝트는 시각장애인의 대중교통 이용 편의성을 높이기 위해 개발한 AI 기반 버스 정류장 안내 시스템입니다.

Raspberry Pi의 카메라와 YOLO 객체 인식 모델을 활용하여 흰지팡이를 탐지하고, Arduino 기반 점자 출력 장치와 연동해 버스 도착 정보를 전달하도록 구현하였습니다.

### 프로젝트 정보

- **프로젝트명:** AI 기반 시각장애인 버스 정류장 안내 시스템
- **개발 기간:** 2026.09.01 ~ 2026.10.11
- **진행 상태:** 완료
- **주요 기술:** Python, OpenCV, YOLO, Raspberry Pi, Arduino, Bluetooth

### Development Purpose

시각장애인은 버스 정류장에서 버스 번호와 도착 정보를 시각적으로 확인하기 어려울 수 있습니다.

이러한 문제를 해결하기 위해 컴퓨터 비전 기술로 사용자의 흰지팡이를 인식하고, 점자 출력 장치를 통해 필요한 버스 정보를 전달하는 시스템을 개발하였습니다.

### My Role

- Raspberry Pi 기반 카메라 영상 처리 및 객체 인식 시스템 구현
- YOLO 모델 학습 및 흰지팡이 탐지 기능 개발
- Raspberry Pi와 Arduino 간 Bluetooth 통신 구현
- 서보모터를 활용한 점자 출력 장치 연동
- 시스템 동작 검증 및 통신 안정성 개선

---

## Development

### System Architecture

본 시스템은 Raspberry Pi와 Arduino를 중심으로 구성된 AI 기반 임베디드 안내 시스템입니다.

**1. Camera & Object Detection**

Raspberry Pi Camera로 입력된 영상을 YOLO 객체 인식 모델과 OpenCV를 활용하여 분석합니다. 흰지팡이가 일정 시간 이상 탐지되면 안내 시스템을 활성화합니다.

**2. Bus Information Processing**

Raspberry Pi에서 목적지에 따른 버스 경로를 탐색하고, 버스 번호와 남은 도착 시간을 관리합니다. 최적의 버스 경로를 탐색하기 위해 BFS 알고리즘을 활용하였습니다.

**3. Bluetooth Communication**

Raspberry Pi와 Arduino는 HC-05 Bluetooth 모듈을 통해 데이터를 주고받습니다. Raspberry Pi는 버스 정보를 전송하고 Arduino로부터 목적지 선택 및 안내 종료 명령을 수신합니다.

**4. Braille Output Device**

Arduino에 연결된 6개의 서보모터를 이용하여 점자 돌기를 제어합니다. 이를 통해 사용자에게 버스 안내 정보를 촉각적으로 제공합니다.

**5. LED Matrix**

MAX7219 기반 8×8 LED Matrix를 활용하여 시스템 시작 및 활성화 상태를 표시합니다.
