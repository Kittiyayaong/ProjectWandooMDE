
## 2. MDE Roles-based Access Control

### RBAC 란? (Role-based Access Control, 역할 기반 엑세스 제어)

특정 작업을 수행할 수 있는 사용자 제어: 사용자 정의 역할을 생성하고 세부적으로 Defender for Endpoint 기능에 대한 액세스를 제어합니다.
특정 장치 그룹 또는 그룹에 대한 정보 보기 제어: 이름, 태그, 도메인 등 특정 기준에 따라 장치 그룹을 생성하고, 특정 Entra ID(Azure AD) 사용자 그룹을 사용하여 역할 액세스를 부여합니다

#### RBAC 설정하기 

1. 설정위치: MDE console > Permissions > Defender XRD Roles > + create customer role 
![image](https://github.com/user-attachments/assets/15671c55-6f3b-4000-8d86-10d19c50d718)

Endpoints roles & groups" 대신 "Microsoft Defender XDR"에 설정해야 하는 이유
 * 통합된 권한 관리: Endpoint roles & groups에서는 장치에 대한 RBAC만 설정 - Microsoft Defender XDR 포털은 모든 워크로드에 대한 단일 권한 관리 경험을 제공합니다. 이를 통해 다양한 보안 경고와 사건을 한 곳에서 관리할 수 있으며, 이는 공격의 전체적인 맥락을 파악하는 데 도움이 됩니다
 * 미래 데이터 소스 자동 포함: Defender XDR에서 "Include future data sources automatically" 옵션을 선택하면, 앞으로 추가될 새로운 데이터 소스도 자동으로 포함됩니다. 이를 통해 새로운 데이터 소스가 추가될 때마다 별도로 설정을 변경할 필요 없이 자동으로 접근 권한이 부여됩니다

Endpoint roles&groups에서 설정할 경우 지원/미지원
 * 지원: Defender for Endpoint RBAC는 사용자가 볼 수 있는 장치, 접근할 수 있는 장치, 수행할 수 있는 디바이스 작업에 대해 세분화된 제어를 제공합니다.  또한, 특정 장치 그룹에 대한 정보 접근을 제어하고, 특정 작업을 수행할 수 있는 권한을 부여할 수 있습니다
 * 미지원: Defender XDR에서 제공하는 ＂Include future data sources automatically＂ 옵션과 같은 기능은 Endpoint roles&groups에서는 지원되지 않습니다. 이 기능은 새로운 데이터 소스가 추가될 때마다 자동으로 접근 권한이 부여되는 기능으로, Defender XDR에서만 사용할 수 있습니다
---
Tip. 기존 MDE RBAC 패널 비활성화: "Endpoints & Vulnerability Management" 스위치를 활성화하면, 기존의 MDE RBAC 패널(설정 > 엔드포인트 > 권한 - 역할)에서 역할을 추가할 수 있는 기능이 완전히 제거됩니다. 즉, 더 이상 기존 패널을 통해 역할을 추가하거나 수정할 수 없습니다.

---

2. Permission 설정하기
   ![image](https://github.com/user-attachments/assets/af06ef4e-0477-47e8-99c0-3742fbef6af9)

Permission 설정값 
* Security operations (운영): 일상적인 보안 운영을 관리하고 사건 및 경고에 대응합니다. 주로 보안 이벤트와 관련된 작업을 수행.
* Security posture (상태관리): 조직의 보안 상태를 관리하고, Defender 평가를 수행하는 등의 작업을 담당합니다. 보안 정책의 준수 여부를 평가하고 개선.
* Authorization and settings (설정관리): 보안 및 시스템 설정을 관리하며, 정책을 생성하고 관리합니다. 시스템의 전반적인 보안 설정.

![image](https://github.com/user-attachments/assets/fa201785-9fe9-490c-8dfe-80fc41a668b7)

3. Assignment 설정하기
![image](https://github.com/user-attachments/assets/8e85ae02-f2b7-42a3-a2b5-4caf8188d1cd)
![image](https://github.com/user-attachments/assets/f42d5522-8953-4f7a-9da1-7807fa4b3f8e)
![image](https://github.com/user-attachments/assets/3a1cc877-9edd-45de-967f-8110a4acece2)
---
Tip. Microsoft Defender for Endpoint(MDE)에서 역할을 할당할 때, 데이터 소스 항목에서 모든 항목이 켜져 있는지 확인하고 "Include future data sources automatically" 옵션을 선택하는 것은 매우 중요!! 
* 모든 데이터 소스 활성화: 데이터 소스 항목에서 모든 항목이 켜져 있는지 확인함으로써, 현재 사용 중인 모든 데이터 소스에 대한 접근 권한을 부여합니다. 이를 통해 보안 분석가나 관리자들이 필요한 모든 데이터에 접근할 수 있게 됩니다.
* 미래 데이터 소스 자동 포함: "Include future data sources automatically" 옵션을 선택하면, 앞으로 추가될 새로운 데이터 소스도 자동으로 포함됩니다. 이를 통해 새로운 데이터 소스가 추가될 때마다 별도로 설정을 변경할 필요 없이 자동으로 접근 권한이 부여됩니다.
---
![image](https://github.com/user-attachments/assets/93ea30a1-d129-4c1b-8a1d-30be02e4ead1)
![image](https://github.com/user-attachments/assets/23018313-6e8a-41e5-88bc-743d4132518f)
