# MDE Basic Setting

## 1. MDE Device Onboarding 

### MDE Device Onboarding 방법 (3가지) 
|방법|설명|장점|
|------|---|---|
|Intune|Intune을 사용하여 장치를 온보딩합니다.|중앙 집중식 관리, 자동화된 정책 배포|
|Configuration Manager|Configuration Manager를 사용하여 On-prem 엔드포인트를 보호합니다.|기존 인프라 활용 가능|
|로컬 스크립트|로컬스크립트를 사용하여 파일럿을 실행하거나 소수의 디바이스만 온보딩합니다.|간단한 설정, 빠른 테스트 가능|

Tip. 500개의 디바이스 온보딩을 위한 최적의 방법?
Intune을 사용하는 것이 가장 빠르고 효율적인 방법일 수 있습니다. 
Intune을 사용하면 중앙 집중식으로 장치를 관리하고, 자동화된 정책 배포를 통해 온보딩을 간편하게 진행할 수 있습니다.

### Onboarding Process 
![image](https://github.com/user-attachments/assets/0faa565d-5f1a-439c-b922-793e387a88b8)
장치 유형에 따라 온보딩 경로가 다르게 설정되어 있습니다. 주요 경로는 Non-Azure Windows Server, Azure Windows Server, Windows 10/11로 나뉩니다. 각 경로는 ConfigMgr 클라이언트의 유무와 Intune/MDM 통합 여부에 따라 세부적으로 나뉩니다.

### Intune에서 디바이스 Onboarding (사전확인) 
* MDE Console에서 Intune 활성화 확인: MDE console > Setting > Endpoints > Advanced feature > Intune connection
![image](https://github.com/user-attachments/assets/8ddfd76d-ee66-4c94-8a42-ffba9edcf18f)

* Intune Console에서 MDE 활성화 확인: Intune console > endpoint security > Defender for Endpoint > Connection Status 확인 / Connect Window device ‘ON’ 확인
![image](https://github.com/user-attachments/assets/53d1cf9b-d0de-4242-9eca-e1a8ab8ecc1e)

* Intune에서 Device Configuration 설정:
Intune console > Device > Windows > Configuration > +create > + new policy > Platform : Windows / Profile : template > Microsoft defender for endpoint
![image](https://github.com/user-attachments/assets/9068d85f-ac3a-440a-83e8-a8aa0af3188f)

### Sample sharing for all files
이 설정은 Microsoft Defender for Endpoint가 모든 파일의 샘플을 Microsoft로 공유할지 여부를 결정합니다. 이를 통해 Microsoft는 잠재적인 위협을 분석하고 보안 기능을 개선할 수 있습니다.
* Block: 이 옵션을 선택하면 모든 파일의 샘플 공유가 차단됩니다. 즉, 디바이스에서 Microsoft로 파일 샘플을 보내지 않습니다. 이 설정은 데이터 프라이버시를 강화할 수 있지만, 잠재적인 위협 분석에 제한이 있을 수 있습니다.
* Not configured: 이 옵션을 선택하면 기본 설정이 적용됩니다. 기본적으로 샘플 공유가 활성화될 수 있으며, 이는 Microsoft가 잠재적인 위협을 분석하는 데 도움이 됩니다.

### telemetry reporting frequency: 
Microsoft Defender for Endpoint가 텔레메트리 데이터를 Microsoft로 보고하는 빈도를 조정합니다. 텔레메트리 데이터는 디바이스의 보안 상태와 관련된 정보를 포함합니다.
* Enable: 이 옵션을 선택하면 텔레메트리 보고 빈도가 증가합니다. 즉, 디바이스가 risky한 상황일 경우에 더 자주 데이터를 Microsoft로 전송하여 보안 상태를 모니터링합니다. 이는 보안 위협을 더 빠르게 감지하고 대응하는 데 도움이 됩니다.
* Not configured: 이 옵션을 선택하면 기본 설정이 적용됩니다. 기본적으로 텔레메트리 보고 빈도가 표준 수준으로 유지될 수 있습니다.

### 설정완료
![image](https://github.com/user-attachments/assets/ada0c902-27fa-4b47-8f91-7cdf7747df96)
