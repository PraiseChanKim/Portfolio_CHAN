# Kim Yechan | Portfolio

Hugo와 Hugo Theme Stack을 활용하여 제작한 개인 포트폴리오 웹사이트입니다.

컴퓨터공학, 인공지능 및 임베디드 시스템 분야에 대한 관심과 학습 경험, 직접 수행한 프로젝트를 소개합니다.

## Website

- **Portfolio:** https://praisechankim.github.io/Portfolio_CHAN/
- **GitHub Repository:** https://github.com/PraiseChanKim/Portfolio_CHAN

## Tech Stack

- **Static Site Generator:** Hugo Extended v0.169.0
- **Theme:** Hugo Theme Stack
- **Languages:** Markdown, HTML, CSS
- **Version Control:** Git & GitHub
- **Deployment:** GitHub Actions & GitHub Pages
- **Development Environment:** Windows, Visual Studio Code

## Getting Started

### 1. Requirements

사이트를 로컬 환경에서 실행하기 위해 다음 도구가 필요합니다.

- Git
- Hugo Extended v0.169.0
- Visual Studio Code (권장)

Hugo 설치 및 버전별 다운로드는 [Hugo 공식 사이트](https://gohugo.io/installation/)에서 확인할 수 있습니다.

### 2. Clone Repository

터미널에서 저장소를 복제합니다.

`git clone https://github.com/PraiseChanKim/Portfolio_CHAN.git`

복제된 저장소 폴더로 이동합니다.

`cd Portfolio_CHAN`

### 3. Run Local Server

Hugo 사이트 폴더로 이동합니다.

`cd site`

개발 서버를 실행합니다.

`hugo server -D`

브라우저에서 다음 주소로 접속하여 사이트를 확인합니다.

http://localhost:1313/

서버를 종료하려면 터미널에서 `Ctrl + C`를 누릅니다.

### 4. Build Site

`site` 폴더에서 다음 명령어로 정적 사이트를 빌드할 수 있습니다.

`hugo --minify`

빌드된 결과물은 기본적으로 `site/public/` 폴더에 생성됩니다.

## Project Structure

주요 파일과 디렉터리는 다음과 같습니다.

| Path | Description |
|---|---|
| `site/config/_default/` | Hugo 사이트 설정 |
| `site/content/page/about/` | 자기소개 페이지 |
| `site/content/page/links/` | GitHub 및 프로젝트 링크 |
| `site/content/post/ai-bus-stop/` | AI 버스 정류장 프로젝트 게시글 및 미디어 파일 |
| `site/content/post/Self-balancing-RC-car/` | Self-Balancing RC Car 프로젝트 게시글 및 미디어 파일 |
| `site/assets/img/` | 프로필 이미지 등 사이트 자산 |
| `README.md` | 프로젝트 소개 및 실행 안내 |

## Featured Projects

### AI 기반 시각장애인 버스 정류장 안내 시스템

Raspberry Pi, YOLO 객체 인식 모델, Arduino 및 Bluetooth 통신을 활용한 시각장애인 버스 안내 시스템입니다.

카메라로 흰지팡이를 탐지한 후 목적지에 따른 버스 정보를 처리하고, 점자 출력 장치를 통해 정보를 전달하도록 구현하였습니다.

**주요 기술:** Python, Raspberry Pi, Arduino, YOLO11n, OpenCV, Bluetooth, Fusion

**프로젝트 소스코드:** https://github.com/PraiseChanKim/AI-Bus-Stop-System

### ATmega328P 기반 Self-Balancing RC Car

ATmega328P 마이크로컨트롤러와 MPU6050 센서를 활용하여
차체의 균형을 자동으로 유지하는 것을 목표로 개발 중인
2륜 RC 자동차 프로젝트입니다.

I2C 통신으로 가속도 및 각속도 데이터를 수집하고,
PD 제어 알고리즘을 통해 모터의 회전 방향과
PWM 출력을 조절하도록 구현하였습니다.

또한 Autodesk Fusion 360을 활용하여 자동차 프레임을
직접 설계하고 3D 모델링을 진행하였습니다.

현재 기울기 변화에 따른 모터 제어를 구현하였으며,
안정적인 균형 유지를 위한 PD 제어 계수 최적화를
진행하고 있습니다.

**주요 기술:** C, ATmega328P, MPU6050, I2C,
UART, Timer1 PWM, PD Control, Fusion 360

**프로젝트 소스코드 및 3D 모델링:**
[Self_Balancing_Rc_Car](https://github.com/PraiseChanKim/Self_Balancing_Rc_Car)

## Updating and Deploying

웹사이트 콘텐츠 또는 설정을 수정한 후 아래 절차로 변경사항을 반영합니다.

### 1. Edit Files

VS Code에서 필요한 Markdown 파일 또는 Hugo 설정 파일을 수정합니다.

### 2. Test Locally

`site` 폴더에서 `hugo server -D`를 실행하고 변경사항이 정상적으로 표시되는지 확인합니다.

### 3. Commit Changes

저장소 최상위 폴더에서 변경된 파일을 확인합니다.

`git status`

수정된 파일을 Git에 추가합니다.

`git add <수정한 파일 경로>`

변경 내용을 설명하는 메시지로 Commit합니다.

`git commit -m "docs: update portfolio content"`

### 4. Push to GitHub

`git push origin main`

### 5. Verify Deployment

`main` 브랜치에 Push하면 GitHub Actions 워크플로를 통해 사이트가 자동으로 빌드 및 배포됩니다.

아래 페이지에서 워크플로 실행 상태를 확인할 수 있습니다.

https://github.com/PraiseChanKim/Portfolio_CHAN/actions

배포가 성공하면 공개 사이트에서 변경사항이 반영되었는지 확인합니다.

https://praisechankim.github.io/Portfolio_CHAN/

## Theme & License

본 사이트는 [Hugo Theme Stack](https://github.com/CaiJimmy/hugo-theme-stack)을 기반으로 제작하였습니다.

Theme Stack designed by [Jimmy](https://github.com/CaiJimmy).

원본 Hugo Theme Stack은 **GNU General Public License v3.0**으로 배포됩니다. 원본 테마의 저작권 및 라이선스 고지를 유지합니다.

- **Theme Repository:** https://github.com/CaiJimmy/hugo-theme-stack
- **Theme Documentation:** https://stack.jimmycai.com/