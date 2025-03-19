## 1. Endpoint detection & response(EDR) 설정하기 

### EDR이란? 
EDR(Endpoint Detection and Response)은 엔드포인트에서 발생하는 사이버 위협을 탐지하고 대응하는 보안 솔루션입니다. EDR은 주로 PC, 랩탑, 서버와 같은 엔드포인트 장치에서 의심스러운 활동을 실시간으로 모니터링하고 분석하여, 악성코드나 랜섬웨어와 같은 위협을 신속하게 탐지하고 대응할 수 있도록 도와줍니다

1. EDR의 주요 기능
* 실시간 모니터링: 엔드포인트에서 발생하는 모든 활동을 실시간으로 모니터링하여 의심스러운 행동을 탐지합니다.
* 행동 기반 분석: 악성코드나 비정상적인 활동을 탐지하기 위해 행동 기반 분석을 수행합니다.
* 위협 대응: 탐지된 위협에 대해 신속하게 대응하여 악성코드를 격리하거나 제거합니다.
* 포렌식 조사: 보안 사고 발생 시, 사고의 원인과 영향을 조사하여 대응 방안을 마련합니다.

### Lab 시나리오 
1. 고객사 Needs:
* 행위 기반 차단 및 봉쇄: AI 및 머신러닝 기반의 행위 분석을 통해 악성 행위를 탐지하고 차단합니다. 이를 통해 새로운 형태의 악성 소프트웨어나 알려지지 않은 위협을 빠르게 차단할 수 있습니다.
* 멀웨어 탐지 및 차단: 처음 발견된 멀웨어를 탐지하고, 다른 엔드포인트에서도 몇 분 내에 차단할 수 있습니다. 
* 지속적인 위협 탐지: 클라우드 기반의 EDR 기능을 통해 비정상적인 행위를 탐지하고, 자동으로 대응합니다
2. 설정방향 : 샘플 공유를 활성화하여 Microsoft Defender for Endpoint가 악성 샘플을 Microsoft로 전송하도록 설정합니다.

### EDR 설정하기 
1. Intune console(portal)에서 EDR policy 설정
Intune console > Endpoint security > Endpoint Detection and Response > + Create policy 

![image](https://github.com/user-attachments/assets/9cad826e-c257-4b53-91a2-85e87d41932d)

![image](https://github.com/user-attachments/assets/ab95caf1-6965-4932-ab97-9529c27a26cd)

2. EDR Policy Configuration setting 설정

![image](https://github.com/user-attachments/assets/d940b69f-5f41-46f8-80b7-ec79205a0cb6)

* Microsoft Defender for Endpoint client configuration package type
Microsoft Defender for Endpoint 클라이언트 구성 패키지 유형을 지정합니다. 이 패키지는 Microsoft Defender for Endpoint를 설정하고 구성하는 데 필요한 모든 파일과 설정을 포함합니다. 기본적으로 설정되지 않음으로 표시되며, 필요에 따라 적절한 패키지를 선택하여 구성할 수 있습니다

* Sample Sharing
샘플 공유 설정은 Microsoft Defender for Endpoint가 악성 샘플을 Microsoft로 전송하도록 허용하는지 여부를 결정합니다. 이 설정을 활성화하면, Microsoft는 전송된 샘플을 분석하여 새로운 위협을 식별하고, 보안 제품을 개선하는 데 사용할 수 있습니다. 기본적으로 설정되지 않음으로 표시되며, 필요에 따라 활성화할 수 있습니다. 
* Not Configured (기본 설정 상태): Intune에서 해당 설정을 변경하지 않으며, 장치에 적용된 기본값이 유지됩니다. 즉, 조직의 정책에 따라 샘플 공유가 활성화되거나 비활성화될 수 있습니다
* None (샘플 공유를 명시적으로 비활성화): Microsoft Defender for Endpoint가 악성 샘플을 Microsoft로 전송하지 않도록 명확하게 지정됩니다
* [Deprecated] Telemetry Reporting Frequency
원격 측정 보고 빈도 설정은 Microsoft Defender for Endpoint가 원격 측정 데이터를 Microsoft로 전송하는 빈도를 지정합니다. 이 설정은 현재 사용되지 않으며, 기본적으로 설정되지 않음으로 표시됩니다. 원격 측정 데이터는 제품 성능, 사용 현황 및 잠재적인 문제를 분석하는 데 사용됩니다.

3. Intune console(portal)에서 EDR policy 설정
* 샘플 공유를 활성화하여 Microsoft Defender for Endpoint가 악성 샘플을 Microsoft로 전송하도록 설정합니다.

![image](https://github.com/user-attachments/assets/c75c9dd9-26e6-4593-86f8-8a7a12b3d608)

* Scope tags/ Assignment 설정

![image](https://github.com/user-attachments/assets/b2004fb0-3ae2-4546-acaf-bd0a1550c046)

* 생성 완료
  
![image](https://github.com/user-attachments/assets/d425b8e6-064f-444b-95a8-6609b54c3d88)

### EDR in Block mode 
EDR in Block Mode를 활성화하지 않은 경우, EDR은 탐지된 위협에 대해 경고를 제공하고, 관리자가 수동으로 대응할 수 있도록 합니다. 그러나 EDR in Block Mode를 활성화하면, 탐지된 악성 아티팩트를 자동으로 차단하고 대응할 수 있는 추가적인 보호 기능을 제공합니다
* EDR(Endpoint Detection and Response) 기능은 주로 악성 활동을 탐지하고 보안 팀에 알리며 사건 세부 사항을 기록하는 데 중점
* EDR in Block Mode는 탐지된 악성 아티팩트를 자동으로 차단하고 대응할 수 있는 추가적인 보호 기능을 제공

![image](https://github.com/user-attachments/assets/9b203479-daac-4ac2-a1b7-8f5a33938a8e)

1. MDE console(portal)에서 EDR in block mode 활성화
* 설정위치: Setting > Endpoints > Advanced Features > Enable EDR in Block mode

![image](https://github.com/user-attachments/assets/7333ed10-d6fa-40c2-9d41-99fcf7c86de7)

