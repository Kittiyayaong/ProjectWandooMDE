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
