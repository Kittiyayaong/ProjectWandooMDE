
## 2. MDE Roles-based Access Control

### RBAC 란? (Role-based Access Control, 역할 기반 엑세스 제어)

특정 작업을 수행할 수 있는 사용자 제어: 사용자 정의 역할을 생성하고 세부적으로 Defender for Endpoint 기능에 대한 액세스를 제어합니다.
특정 장치 그룹 또는 그룹에 대한 정보 보기 제어: 이름, 태그, 도메인 등 특정 기준에 따라 장치 그룹을 생성하고, 특정 Entra ID(Azure AD) 사용자 그룹을 사용하여 역할 액세스를 부여합니다

## ✅ Exercise 1. RBAC 설정하기 

Task 1. 설정위치: MDE console > Permissions > Defender XRD Roles > + create customer role > **Wandoo-mde-rbac** role 생성 

   <img width="1156" alt="image" src="https://github.com/user-attachments/assets/fa900fc4-73dd-40a0-80bc-9bd2c2e6b459" />

> ⭐️ Tips. Endpoints roles & groups" 대신 "Microsoft Defender XDR"에 설정해야 하는 이유
> 1. Microsoft Defender for Endpoint(MDE)는 XDR 플랫폼의 일부: MDE는 현재 Microsoft Defender XDR 플랫폼 아래 통합되어 관리됩니다. XDR(Extended Detection and Response) 포털은 Defender for Endpoint, Defender for Identity, Defender for Office 365, Defender for Cloud Apps 등 여러 보안 제품의 통합 관리 허브입니다. 따라서 역할 기반 액세스(RBAC), 경고 관리, 인시던트 할당 등 공통 보안 운영 기능은 XDR 포털에서 중앙 설정됩니다.
> 2. RBAC 범위가 MDE 단독이 아닌 XDR 전체에 적용: XDR의 RBAC는 인시던트, 경고, 디바이스 권한 등에 걸쳐있기 때문에, Defender XDR RBAC 설정 시, 해당 권한은 MDE에도 함께 적용됩니다.

---

Task 2. Permission 설정하기
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

> ⭐️ Tips. Microsoft Defender for Endpoint(MDE)에서 역할을 할당할 때, 데이터 소스 항목에서 모든 항목이 켜져 있는지 확인하고 "Include future data sources automatically" 옵션을 선택하는 것은 매우 중요!! 
> * 모든 데이터 소스 활성화: 데이터 소스 항목에서 모든 항목이 켜져 있는지 확인함으로써, 현재 사용 중인 모든 데이터 소스에 대한 접근 권한을 부여합니다. 이를 통해 보안 분석가나 관리자들이 필요한 모든 데이터에 접근할 수 있게 됩니다.
> * 미래 데이터 소스 자동 포함: "Include future data sources automatically" 옵션을 선택하면, 앞으로 추가될 새로운 데이터 소스도 자동으로 포함됩니다. 이를 통해 새로운 데이터 소스가 추가될 때마다 별도로 설정을 변경할 필요 없이 자동으로 접근 권한이 부여됩니다.

---

![image](https://github.com/user-attachments/assets/93ea30a1-d129-4c1b-8a1d-30be02e4ead1)
![image](https://github.com/user-attachments/assets/23018313-6e8a-41e5-88bc-743d4132518f)
