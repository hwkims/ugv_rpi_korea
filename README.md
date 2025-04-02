![GitHub top language](https://img.shields.io/github/languages/top/effectsmachine/ugv_rpi) ![GitHub language count](https://img.shields.io/github/languages/count/effectsmachine/ugv_rpi)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/effectsmachine/ugv_rpi)
![GitHub repo size](https://img.shields.io/github/repo-size/effectsmachine/ugv_rpi) ![GitHub](https://img.shields.io/github/license/effectsmachine/ugv_rpi) ![GitHub last commit](https://img.shields.io/github/last-commit/effectsmachine/ugv_rpi)

# Waveshare UGV 로봇
이것은 [Waveshare](https://www.waveshare.com/) UGV 로봇을 위한 Raspberry Pi 예제입니다: **WAVE ROVER**, **UGV Rover**, **UGV Beast**, **RaspRover**, **UGV01**, **UGV02**.

![](./media/UGV-Rover-details-23.jpg)

## 기본 설명
Waveshare UGV 로봇은 상위 컴퓨터와 하위 컴퓨터를 모두 활용합니다. 이 저장소에는 일반적으로 이 설정에서 Raspberry Pi인 상위 컴퓨터에서 실행되는 프로그램이 포함되어 있습니다.

하위 컴퓨터에서 실행되는 프로그램은 사용되는 로봇 드라이버 유형에 따라 [ugv_base_ros](https://github.com/effectsmachine/ugv_base_ros.git) 또는 [ugv_base_general](https://github.com/effectsmachine/ugv_base_general.git)이라는 이름으로 지정됩니다.

상위 컴퓨터는 GPIO UART를 통해 JSON 명령을 전송하여 하위 컴퓨터(ESP32 기반 로봇 드라이버)와 통신합니다. Raspberry Pi를 사용하는 호스트 컨트롤러는 AI 비전 및 전략 계획을 처리하고, ESP32를 사용하는 서브 컨트롤러는 모션 제어 및 센서 데이터 처리를 관리합니다. 이 설정은 효율적인 협업과 향상된 성능을 보장합니다.

## 특징
- WebRTC 기반 실시간 비디오
- JupyterLab 기반 대화형 튜토리얼
- 팬틸트 카메라 제어
- 로봇 팔 제어
- Flask 기반 크로스 플랫폼 웹 애플리케이션
- 자동 타겟팅 (OpenCV)
- 객체 인식 (OpenCV)
- 제스처 인식 (MediaPipe)
- 얼굴 감지 (OpenCV & MediaPipe)
- 움직임 감지 (OpenCV)
- 비전 기반 라인 추적 (OpenCV)
- 색상 인식 (OpenCV)
- 다중 스레드 CV 처리
- 오디오 상호 작용
- 단축키 제어
- 사진 촬영
- 비디오 녹화

## 빠른 설치
**WAVE ROVER**, **UGV01** 또는 **UGV02**를 사용하는 경우 로봇에 Raspberry Pi를 설치해야 합니다.

이 앱은 **UGV Rover**, **UGV Beast** 및 **RaspRover**의 SD 카드에 이미 설치되어 있습니다.

이 튜토리얼을 사용하여 로봇의 상위 컴퓨터 프로그램을 업그레이드할 수 있습니다.

이 튜토리얼을 사용하여 순수 Raspberry Pi OS에 이 프로그램을 설치할 수 있습니다.

### GitHub에서 저장소 다운로드

Waveshare의 GitHub에서 이 저장소를 로컬 시스템으로 복제할 수 있습니다.

    git clone https://github.com/waveshareteam/ugv_rpi.git

### 설치 스크립트에 실행 권한 부여
    cd ugv_rpi/
    sudo chmod +x setup.sh
    sudo chmod +x autorun.sh
### 앱 설치 (완료까지 시간이 걸립니다)
    sudo ./setup.sh
### 자동 실행 설정
    ./autorun.sh
### AccessPopup 설치
    cd AccessPopup
    sudo chmod +x installconfig.sh
    sudo ./installconfig.sh
    * 입력 1: AccessPopup 설치
    * 아무 키나 눌러 종료
    * 입력 9: installconfig.sh 종료
### 장치 재부팅
    sudo reboot

로봇 전원을 켠 후, Raspberry Pi는 자동으로 핫스팟을 설정하고 LED 화면에 일련의 시스템 초기화 메시지가 표시됩니다:

![](./media/RaspRover-LED-screen.png)
- 첫 번째 줄 `E`는 이더넷 포트의 IP 주소를 표시하며, 이를 통해 Raspberry Pi에 원격으로 액세스할 수 있습니다. `No Ethernet`이라고 표시되면 Raspberry Pi가 이더넷 케이블에 연결되지 않았음을 나타냅니다.
- 두 번째 줄 `W`는 로봇의 무선 모드를 나타냅니다. 액세스 포인트(AP) 모드에서는 로봇이 자동으로 기본 IP 주소 `192.168.50.5`로 핫스팟을 설정합니다. 스테이션(STA) 모드에서는 Raspberry Pi가 알려진 WiFi 네트워크에 연결하고 원격 액세스를 위한 IP 주소를 표시합니다.
- 세 번째 줄 `F/J`는 이더넷 포트 번호를 지정합니다. 포트 `5000`은 로봇 제어 웹 UI에 대한 액세스를 제공하고, 포트 `8888`은 JupyterLab 인터페이스에 대한 액세스를 제공합니다.
- 네 번째 줄 `STA`는 WiFi가 스테이션(STA) 모드임을 나타냅니다. 시간 값은 로봇 사용 시간을 나타냅니다. dBm 값은 STA 모드에서의 신호 강도 RSSI를 나타냅니다.

휴대폰이나 PC를 사용하여 로봇 웹 앱에 액세스할 수 있습니다. 브라우저를 열고 URL 표시줄에 `[IP]:5000`(예: `192.168.10.50:5000`)을 입력하여 로봇을 제어합니다.

JupyterLab에 액세스하려면 `[IP]:8888`(예: `192.168.10.50:8888`)을 사용합니다.

로봇이 알려진 WiFi 네트워크에 연결되지 않은 경우, 자동으로 "`AccessPopup`"이라는 이름의 핫스팟을 암호 `1234567890`으로 설정합니다. 그런 다음 휴대폰이나 PC를 사용하여 이 핫스팟에 연결할 수 있습니다. 연결되면 브라우저를 열고 URL 표시줄에 `192.168.50.5:5000`을 입력하여 로봇을 제어합니다.

Raspberry Pi에서 실행되는 다양한 유형의 로봇과의 호환성을 보장하기 위해, 사용 중인 특정 로봇을 지정하는 `config.yaml` 파일을 사용합니다. 다음 명령을 입력하여 로봇을 구성할 수 있습니다:

    s 22

이 명령에서 `s` 지시어는 로봇 유형 설정을 나타냅니다. 첫 번째 숫자 `2`는 로봇이 `UGV Rover`임을 의미하며, `1`은 `RaspRover`를, `3`은 `UGV Beast`를 나타냅니다. 두 번째 숫자 역시 `2`이며, 모듈이 `Camera PT`임을 지정합니다. 여기서 `0`은 `Nothing`을, `1`은 `RoArm-M2`를 의미합니다.

### 장치 재부팅
프로그램 실행에 실패하고 런타임 중에 `v4l2.py`와 관련된 오류가 발생하는 경우, Python 가상 환경과 사용자 환경 모두에서 `v4l2.py`를 삭제해야 합니다. 이렇게 하면 프로그램이 자동으로 시스템 전체의 `v4l2.py`를 사용하게 됩니다.

    cd ugv_rpi/
    sudo rm ugv-env/lib/python3.11/site-packages/v4l2.py
    sudo rm /home/[your_user_name]/.local/lib/python3.11/site-packages/v4l2.py

이제 메인 프로그램 `app.py`를 다시 시작할 수 있습니다.

# 라이선스
ugv_rpi for the Raspberry Pi: an open source robotics platform for the Raspberry Pi.
Copyright (C) 2024 [Waveshare](https://www.waveshare.com/)

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/gpl-3.0.txt>.
