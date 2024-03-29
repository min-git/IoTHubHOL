# IoTHubHOL
Azure IoT Hub을 활용한 아키텍처 구성을 위한 hands-on lap을 실습합니다. [Azure IoT 아키텍처 참조](https://docs.microsoft.com/ko-kr/azure/architecture/reference-architectures/iot)

Azure Portal상에 IoT Hub를 생성하여 디바이스 생성 및 연동 합니다.
VSCode를 활용하여 디바이스 샘플 소스코드를 통해 텔레메트리 데이터를 생성하여 IoT Hub에 등록된 디바이스와 연동 합니다.

이번 과정에서는 아래의 내용을 실습 합니다.
1. IoT Hub 생성
2. IoT Hub에 디바이스 등록
3. Visual Studio Code를 통해 샘플 디바이스 코드로 텔레메트리 데이터 IoT Hub로 전송
4. Azure IoT Explorer를 통해 IoT Hub로 전송되는 텔레메트리 데이터 실시간 모니터링


# 사전 준비사항
- [Git 설치](https://git-scm.com/downloads)
- [Visual Studio Code 설치](https://code.visualstudio.com/)
- [Node.js ver. 12+ 설치](https://dotnet.microsoft.com/download/dotnet)
- [Azure IoT Explorer 설치](https://github.com/Azure/azure-iot-explorer/releases)


# 참조 기술문서
- [IoT Hub 설명서](https://docs.microsoft.com/ko-kr/azure/iot-hub/)
- [MS Learn 교육사이트](https://docs.microsoft.com/ko-kr/learn/browse/?expanded=azure%2Cwindows&products=azure-iot%2Cazure-iot-hub)


# Lab 1 - IoT Hub 리소스 생성 및 디바이스 

## Lab 1-1 리소스 그룹 생성 ##

실습에 필요한 리소스들을 그룹핑하여 관리할 수 있는 리소스 그룹을 생성합니다.

Azure 포털에서 리소스 만들기를 선택합니다.

![image](img/iothub_hol001.png)

검색창에 Resource Group을 입력하여 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139613692-a3daece0-0ed6-42aa-a476-3634ce5b7b16.png)

## Lab 1-2 IoT Hub 생성 ##

Home(홈)을 선택하여 기본화면에서 리소스 만들기를 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139613823-fb9bd706-bf94-43d1-b349-68a4ea4e5fd7.png)

사물 인터넷(IoT) 카테고리 및 IoT Hub 만들기를 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139613862-065893ff-98ad-4388-a247-adc435a464c9.png)

이전 실습에서 생성한 리소스 그룹을 선택하고 IoT Hub 이름과 지역을 입력합니다.

IoT Hub 이름은 다른 사용자들과 중복되지 않는 값을 입력하여야 합니다.

“검토+만들기”를 선택한 후 유효성 검사를 통과하면 “만들기”를 선택하여 IoT Hub 리소스를 생성합니다.

![image](https://user-images.githubusercontent.com/14192817/139613911-c74c87a9-3072-451a-844f-5fb8f7d9030b.png)

배포가 완료되면 홈을 선택하여 생성된 IoT Hub로 이동합니다.

IoT Hub 리소스가 생성되더라도 정상화에 약간의 지연이 있을 수 있습니다.

![image](https://user-images.githubusercontent.com/14192817/139613939-f7664cc2-f483-43ba-b4b3-2af8db50289b.png)

## Lab 1-3 IoT Hub에 디바이스 등록 ##

IoT Hub 화면에서 Devices 항목을 선택한 후 “+ 디바이스 추가”를 선택하여 디바이스 등록을 진행합니다.

![image](https://user-images.githubusercontent.com/14192817/139613978-a9dcc5d2-91ee-4b91-9d85-c2a756cef04c.png)

디바이스 만들기 화면에서 등록될 디바이스를 식별할 디바이스 ID를 선택합니다.

본 실습의 과정에서 인증 형식은 대칭 키를 선택하여 저장합니다.

![image](https://user-images.githubusercontent.com/14192817/139613990-466a918a-25db-4c5a-84d6-25f95f9bc661.png)

생성된 장치 ID를 확인 후 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139614003-7edbeb20-3ca1-4dd5-a98e-dc7f630d3905.png)

등록된 디바이스 정보에서 “기본 연결 문자열”을 복사하여 메모장 등에 저장합니다.

“기본 연결 문자열”(Connection String)은 실제 디바이스 프로그래밍 코드에서 IoT Hub 연결 정보로 사용 됩니다.

![image](https://user-images.githubusercontent.com/14192817/139614020-c2b58dfe-d43d-481a-a606-831398aec220.png)


## Lab 1-4 Visual Studio Code를 활용하여 디바이스 샘플 프로그램 구동 ##

본 실습에서는 Node.js를 이용하여 디바이스 샘플 프로그램을 구동 합니다.

C/C#/NodeJS/Python/Java 언어 샘플 실습은 [기술 문서](https://docs.microsoft.com/ko-kr/azure/iot-develop/quickstart-send-telemetry-iot-hub?toc=%2Fazure%2Fiot-hub%2Ftoc.json&bc=%2Fazure%2Fiot-hub%2Fbreadcrumb%2Ftoc.json&pivots=programming-language-nodejs) 참조하시기 바랍니다.

Git에 등록된 샘플 프로그램을 로컬PC에 다운로드 및 실행하여 IoT Hub에 텔레메리트 데이터를 전송합니다.

로컬 PC에서 프로그램 코드를 저장할 디렉토리를 생성합니다.

![image](https://user-images.githubusercontent.com/14192817/139614150-3319f039-2940-4868-a2cf-f0395070c76f.png)

CMD 창에서 생성된 디렉토리로 이동합니다.

명령어를 통해서 Git에 저장된 샘플 코드를 로컬 디렉토리로 다운로드 합니다.

```bash
git clone https://github.com/Azure/azure-iot-sdk-node
 ```

![image](img/iothub_hol01.png)

다운로드하여 생성된 azure-iot-sdk-node 디렉토리로 이동합니다.

Windows

```bash
cd azure-iot-sdk-node
 ```

Linux 

```bash
cd azure-iot-sdk-node
 ```

Visual Studio Code를 실행합니다.

![image](img/iothub_hol02.png)

![image](img/iothub_hol03.png)

본 실습에서는 azure-iot-sdk-node/device/samples/javascript 디렉토리 하위의 샘플 소스코드를 이용하여 실습합니다.

![image](img/iothub_hol04.png)

Terminal 메뉴에서 New Terminal을 선택하여 터미널 창을 실행합니다.

![image](https://user-images.githubusercontent.com/14192817/139614205-e5aa14fb-90ce-483d-aa98-65394e694770.png)

하단의 Terminal 창에서 실습을 진행할 샘플 코드가 위치한 “azure-iot-sdk-node/device/samples/javascript” 디렉토리로 이동합니다.

![image](img/iothub_hol05.png)

Node.js 를 설치합니다.

```bash
npm install
 ```

![image](img/iothub_hol06.png)

아래 명령어를 참조하여 샘플 프로그램을 실행합니다.

샘플 프로그램에서는 텔레메트리 데이터를 임의로 생성하여 IoT Hub로 전송합니다.

Window CMD
```bash
set IOTHUB_DEVICE_CONNECTION_STRING="메모장에 저장된 IoT Hub 연결 문자열 정보 입력"
set IOTHUB_DEVICE_SECURITY_TYPE=connectionString
 ```
 
Power Shell
```bash
$env:IOTHUB_DEVICE_CONNECTION_STRING='메모장에 저장된 IoT Hub 연결 문자열 정보 입력'
$env:IOTHUB_DEVICE_SECURITY_TYPE='connectionString'
 ```
 
Bash
```bash
export IOTHUB_DEVICE_CONNECTION_STRING="메모장에 저장된 IoT Hub 연결 문자열 정보 입력"
export IOTHUB_DEVICE_SECURITY_TYPE="connectionString"
 ```

예시) 
![image](img/iothub_hol07.png)

## Lab 1-5 Azure IoT Explorer를 IoT Hub 텔레메트리 실시간 모니터링 ##

Azure IoT Explorer를 통해 디바이스에서 IoT Hub로 전송되는 실시간 텔레메트리 데이터를 모니터링 합니다.

Azure 포털에서 IoT Hub의 “공유 엑세스 정책” 메뉴를 선택하고 iothubowner 항목을 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139614402-d70f3fdf-bc88-45fe-8979-df5240a2b148.png)

IoT Hub의 기본 연결 문자열을 복사하여 메모장 등에 저장합니다.

![image](https://user-images.githubusercontent.com/14192817/139614414-19f514f8-5270-4b76-b26e-f83cec660d97.png)

Azure IoT Explorer 를 실행하여 “+ Add connection”을 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139614424-e46d03eb-0942-43bc-aa96-cb958e65e69a.png)

저장해 두었던 IoT Hub 기본 연결 문자열을 입력창에 복사하여 붙여넣기 합니다.

자동으로 나머지 정보들이 입력되면 저장 버튼을 선택하여 정보를 저장합니다.

![image](https://user-images.githubusercontent.com/14192817/139614438-cbd04199-21da-4095-a16f-e29a60e1fe5e.png)

등록된 디바이스 정보가 출력되는 화면에서 등록된 device id를 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139614468-d4f1dc2d-b6c8-488e-a358-6c95722a4a0f.png)

Telemetry 메뉴를 선택한 후 Start 버튼을 선택합니다.

![image](https://user-images.githubusercontent.com/14192817/139614475-fccf1b6e-46ce-4995-ba30-70e06a535a0f.png)

실시간으로 디바이스에서 전송하는 텔레메트리 데이터를 모니터링할 수 있습니다.

![image](https://user-images.githubusercontent.com/14192817/139614518-1812c286-32e7-4ac0-8ab0-80d41f9ea16d.png)





