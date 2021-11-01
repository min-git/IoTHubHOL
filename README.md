# IoTHubHOL
Azure IoT Hub hands-on lap을 실습합니다.
Azure Portal상에 IoT Hub를 생성하여 디바이스 생성 및 연동 합니다.
VSCode를 활용하여 디바이스 샘플 소스코드를 통해 텔레메트리 데이터를 생성하여 IoT Hub에 등록된 디바이스와 연동 합니다.

이번 과정에서는 아래의 내용을 실습 합니다.
1. IoT Hub 생성
2. IoT Hub에 디바이스 등록
3. Visual Studio Code를 통해 샘플 디바이스 코드로 텔레메트리 데이터 IoT Hub로 전송
4. Azure IoT Explorer를 통해 IoT Hub로 전송되는 텔레메트리 데이터 실시간 모니터링

# 사전 준비사항
- Git 설치
- Visual Studio Code 설치
- Visual Studio Code Extension 설치 (C#)
- .NET Core 설치
- Azure IoT Explorer 설치

# Lab 1 - IoT Hub 리소스 생성

***리소스 그룹 생성***
실습에 필요한 리소스들을 그룹핑하여 관리할 수 있는 리소스 그룹을 생성합니다.

Azure 포털에서 리소스 만들기를 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139613676-977b31cc-4932-4a25-864b-b219e9230fb0.png)

검색창에 Resource Group을 입력하여 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139613692-a3daece0-0ed6-42aa-a476-3634ce5b7b16.png)


