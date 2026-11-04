
---
title: "Atmega328p를 이용한 Self_Balancing_Rc_Car"
description: "Atmega328p를 이용하여 PID 제어로 균형을 잡는 자동차 만들기 프로젝트"
date: 2026-11-04
draft: false
categories:
    - Projects
tags:
    - Atmega328p
    - Embedded
    - Fusion360
---

## Project Overview

### 프로젝트 소개

본 프로젝트는 Atmega328p를 이용한 자동으로 균형을 잡는 RC 자동차입니다.

여태까지 배운 UART통신, I2C통신, PWM 이론을 바탕으로 스스로 균형을 잡는 자동차를 만들었습니다. 
PID 제어를 사용했으며, Atmega328p와 Atmel studio 7.0 툴을 이용했습니다.

### 프로젝트 정보

- **프로젝트명:** Atmega328p를 이용한 Self_Balancing_Rc_Car
- **개발 기간:** 2026.09.01 ~
- **진행 상태:** 진행중
- **주요 기술:** Atmega328p

### Development Purpose

여태까지 배운 임베디드 기초 이론을 이용해서 하나의 작품을 만들고 싶었습니다. 특히 관심이 많았던 **자동 균형 제어**를 한번 해보고 싶어서
**Self_Balancing_Rc_car** 프로젝트를 도전하게 되었습니다. 

### My Role

본 프로젝트는 개인 프로젝트로 진행하였으며, 제가 담당한 주요 개발 작업은 다음과 같습니다.

- 임베디드 시스템 구현: PWM, I2C, UART, GPIO 등 임베디드 시스템의 핵심 기술을 실제 하드웨어에 적용
- MCU 기반 제어 시스템 개발: ATmega328P를 활용하여 PID 제어 알고리즘을 구현하고, 차체의 균형 유지를 위한 모터 제어 시스템 개발
- 3D 모델링 및 기구 설계: Autodesk Fusion 360을 활용하여 자동차 프레임을 직접 설계하고 3D 모델링 수행


---

## Development

### System Architecture

본 시스템은 ATmega328P 마이크로컨트롤러를 기반으로 MPU6050 센서에서 자세 데이터를 수집하고, PID 제어 알고리즘을 통해 차체의 균형을 자동으로 유지하도록 설계한 2륜 RC 자동차입니다.

**1. Sensor Data Acquisition (MPU6050 & I2C)**

MPU6050 센서와 ATmega328P 간 I2C 통신을 통해 3축 가속도 및 각속도 데이터를 수집합니다. 수집된 데이터를 바탕으로 차체의 기울기를 추정하고, PID 제어 알고리즘의 입력값으로 활용합니다.

**2. PID Control Algorithm**

ATmega328P에서 목표 기울기와 현재 기울기 사이의 오차를 계산합니다. 비례(P), 적분(I), 미분(D) 제어 알고리즘을 활용하여 차체의 균형을 유지하는 데 필요한 모터 제어값을 계산합니다.

**3. Motor Control (PWM & GPIO)**

PID 제어 알고리즘에서 계산된 출력값을 바탕으로 PWM 신호를 생성하여 모터의 회전 속도를 조절합니다. GPIO를 통해 모터의 회전 방향을 제어하고, 차체의 기울기 변화에 대응하도록 구성합니다.

**4. UART Communication (Tera Term)**

ATmega328P와 PC 간 UART 시리얼 통신을 구성하고, Tera Term을 활용하여 센서 측정값 및 제어 데이터를 실시간으로 모니터링합니다. 이를 통해 센서 데이터의 변화와 PID 제어 동작을 확인하고, 시스템 디버깅 및 동작 분석에 활용합니다.

**5. Hardware Design & 3D Modeling**

Autodesk Fusion 360을 활용하여 자동차 프레임을 직접 설계하고 3D 모델링을 진행합니다. MCU, MPU6050 센서, 모터 등의 부품 배치와 차체의 무게중심을 고려하여 균형 제어에 적합한 하드웨어 구조를 설계합니다.

---





