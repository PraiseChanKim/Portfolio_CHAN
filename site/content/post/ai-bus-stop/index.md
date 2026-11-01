
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


---


## Implementation Process

### 1. YOLO-based White Cane Detection

**데이터셋 준비 및 모델 학습**

시각장애인의 흰지팡이를 탐지하기 위해 YOLO 기반 객체 인식 모델을 학습하였습니다.

Roboflow의 White Cane 데이터셋을 활용하였으며, YOLO11n 모델을 선택하여 객체 탐지 모델을 구성하였습니다.

주요 학습 설정은 다음과 같습니다.

- **Model:** YOLO11n
- **Dataset:** White Cane Dataset (Roboflow)
- **Epochs:** 50
- **Image Size:** 640 × 640
- **Batch Size:** 16
- **Detection Class:** white_cane

**모델 변환 및 Raspberry Pi 적용**

학습된 YOLO 모델을 Raspberry Pi 환경에서 실행하기 위해 ONNX 형식으로 변환하였습니다.

변환한 모델은 OpenCV DNN 모듈을 이용하여 실행하도록 구성하였습니다.

이를 통해 Raspberry Pi Camera로 입력된 영상에서 흰지팡이를 실시간으로 탐지하도록 구현하였습니다.

**탐지 안정성 개선**

카메라 영상에서 흰지팡이가 일시적으로 탐지되는 경우에도 시스템이 바로 활성화되지 않도록 하였습니다.

흰지팡이가 약 2초 동안 지속적으로 탐지되면 안내 시스템을 활성화하도록 상태 전환 로직을 구현하여 오작동을 줄이고자 하였습니다.

### 2. Bluetooth Communication

**Raspberry Pi와 Arduino 간 무선 통신**

Raspberry Pi와 Arduino 사이의 데이터 전달을 위해 HC-05 Bluetooth 모듈을 활용하였습니다.

Raspberry Pi는 객체 인식과 버스 정보 처리를 담당하고, Arduino는 사용자 입력 및 점자 출력 장치의 서보모터 제어를 담당하도록 기능을 분리하였습니다.

주요 통신 명령은 다음과 같습니다.

- **READY:** 안내 시스템 준비 상태 전달
- **BUS:** 버스 번호 및 남은 도착 시간 전달
- **DEST:** Arduino에서 선택한 목적지 정보 전달
- **STOP:** 사용자 안내 종료 요청

**통신 안정성 개선**

Bluetooth 연결이 끊어지는 상황에 대응하기 위해 자동 재연결 기능을 구현하였습니다.

재연결 이후에도 버스 도착 시간과 사용자 상태를 유지하도록 구성하였으며, 필요한 안내 정보를 다시 전송하여 시스템이 정상적으로 동작하도록 개선하였습니다.

### 3. Braille Output Device

**6개의 서보모터를 활용한 점자 출력 장치**

시각장애인에게 촉각적으로 정보를 전달하기 위해 Arduino와 6개의 서보모터를 활용한 점자 출력 장치를 구현하였습니다.

각 서보모터는 점자의 6개 돌기 중 하나를 제어하며, 출력할 정보에 따라 돌기의 상태가 달라지도록 구성하였습니다.

**하드웨어 제어 및 시스템 연동**

Arduino에서 Bluetooth로 수신한 명령을 처리하고, 점자 출력 장치와 연동하도록 구현하였습니다.

이를 통해 Raspberry Pi의 영상 인식과 버스 정보 처리 기능을 실제 하드웨어 출력 장치와 연결하였습니다.
