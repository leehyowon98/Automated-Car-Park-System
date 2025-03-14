# Automated-Car-Park-System
[팀프로젝트코드.pdf](https://github.com/user-attachments/files/18783613/default.pdf)
# 프로젝트 개요
이 프로젝트는 NFC, 초음파 센서, 블루투스, 모터 등을 활용한 주차 관리 시스템입니다. NFC 태그를 통해 관리자 모드를 활성화할 수 있으며, 블루투스를 통해 원격으로 시스템을 제어할 수 있습니다. 또한, 초음파 센서를 사용하여 주차 공간의 유무를 감지하고, 이를 기반으로 LED 색상 변경 및 모터를 이용한 게이트 개폐를 수행합니다.

# 주요 기능
1. **NFC 카드 인증**
   - NFC 태그를 인식하여 관리자 시스템을 활성화할 수 있음.
   - 관리자 인증 후, 블루투스 및 버튼을 통한 시스템 제어 가능.

2. **블루투스를 통한 원격 제어**
   - 블루투스 모듈을 통해 시스템 상태(켜짐/꺼짐)를 변경할 수 있음.
   - 블루투스 데이터 수신 후 시스템 상태 반영.

3. **버튼을 이용한 수동 제어**
   - 버튼 1: 시스템 온/오프 토글
   - 버튼 2: 환풍기 온/오프 토글

4. **초음파 센서를 활용한 주차 공간 감지**
   - 차량이 감지되면 경고 메시지 출력 및 게이트 닫힘.
   - 차량이 감지되지 않으면 주차 가능 메시지 출력 및 게이트 개방.

5. **LCD 디스플레이**
   - 현재 시스템 상태, 주차 공간 여부 등을 표시.

6. **RGB LED 및 부저 활용**
   - 시스템 상태에 따라 LED 색상이 변경됨 (녹색, 노란색, 빨간색).
   - 경고 상황 발생 시 부저 작동.

# 코드 구성
### 1. 초기화
- 버튼, 블루투스(UART), PWM, LCD, RGB LED, 부저, 초음파, NFC 모듈 초기화.
- NFC 통신 설정 및 상태 확인.
- 표준 출력(stdout) 설정.

### 2. 메인 루프
- NFC 태그 확인 → 관리자 모드 활성화
- 블루투스 데이터 수신 및 시스템 상태 업데이트
- 버튼 입력 감지 → 시스템 및 환풍기 상태 토글
- 초음파 센서를 이용한 차량 감지 및 주차 공간 상태 업데이트
- LED, LCD, 모터 제어 수행

# 하드웨어 구성
- 마이크로컨트롤러 (예: AVR 128a)
- NFC 모듈 (MFRC522)
- 초음파 센서 (HC-SR04)
- 블루투스 모듈 (HC-06)
- 버튼 2개
- PWM 서보모터
- RGB LED
- 부저
- LCD 디스플레이 (I2C 또는 병렬 인터페이스 지원)

# 사용 라이브러리
- UART(시리얼 통신)
- PWM (모터 및 LED 제어)
- SPI (NFC 모듈 통신)
- GPIO (버튼, 부저, LED 제어)

# 실행 방법
1. NFC 태그를 스캔하여 시스템을 활성화합니다.
2. 블루투스 또는 버튼을 통해 시스템을 제어합니다.
3. 초음파 센서가 주차 공간 상태를 감지하고 LCD 및 LED에 표시합니다.
4. 차량이 감지되면 경고 표시 및 게이트를 닫습니다.
5. 차량이 없으면 환영 메시지와 함께 게이트를 엽니다.

# 추가 개발 가능 사항
- NFC 관리자 인증 시스템 강화 (여러 관리자 추가 가능하도록 확장)
- 스마트폰 앱과 연동하여 실시간 주차 공간 모니터링 제공
- 클라우드 서버 연동하여 데이터 저장 및 분석 기능 추가

