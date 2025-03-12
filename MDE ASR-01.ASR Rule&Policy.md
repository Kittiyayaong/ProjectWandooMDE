![image](https://github.com/user-attachments/assets/f0c3b35f-7f37-4d60-99a3-ef804ee8ed26)# MDE Attack Surface Reduction(ASR)

## 1. ASR Rule 설정하기

### Attack Surface Reduction Rule이란? 
공격 표면 감소 규칙(Attack Surface Reduction Rules)은 **외부 시점에서 보안 취약점을 식별하고 이를 강화하는데 목적**이 있습니다. 특정 장치에서 보안 취약점이 발견되면, ASR 규칙을 통해 다양한 보안 조치로 보안 취약점을 감소시켜 공격 표면을 줄이는 방법입니다. 
사전에 관리자가 설정하는 규칙으로 관리자는 조직의 보안 정책에 맞춰 이러한 규칙을 작성하고 적용할 수 있습니다. 예를 들어, Office 응용 프로그램이 자식 프로세스를 생성하지 못하도록 차단하거나, 악성 소프트웨어 제거 도구(MRT)가 실행되지 않도록 차단하는 등의 규칙을 설정할 수 있습니다
이러한 규칙들은 클라우드 인텔리전스를 기반으로 하여 공격 표면을 최소화합니다. 관리자가 설정한 규칙들은 조직의 보안 태세를 강화하고, 잠재적인 위협으로부터 시스템을 보호하는 데 중요한 역할을 합니다

---
Tips. Attack surface reduction (ASR) rules 예시 (참고)

![image](https://github.com/user-attachments/assets/1da41a98-35ed-4f33-bd7d-63908dfcebd7)

---

### MDE 보안 구성 관리 솔루션 아키텍쳐

![image](https://github.com/user-attachments/assets/2f6b9e5f-6c26-4a2f-a4a5-71351161f575)

**새로운 디바이스의 관점** 
1. 디바이스를 MDE에 온보딩:
디바이스가 Intune에 등록되면서, Intune에서 디바이스를 Microsoft Defender for Endpoint에 온보딩됩니다.
2. 정책 생성:
두 번째 단계는 Microsoft Intune에서 보안 정책을 생성하는 것입니다. 여기에는 ASR(Attack Surface Reduction) 규칙과 같은 보안 정책이 포함됩니다.
3. Synthetic registration:
세 번째 단계는 하이브리드 Azure AD 가입을 통해 디바이스를 Microsoft Entra ID에 등록하는 것입니다. 이를 통해 디바이스는 클라우드와 온프레미스 환경 모두에서 관리될 수 있습니다.
4. 정책 / 상태:
디바이스가 Intune을 통해 배포된 보안 정책을 수신하고, MDE에서 이를 적용하여 활성화 후 공격 표면을 줄이는 것입니다. 또한, MDE는 정책의 적용 상태와 디바이스의 보안 상태를 Intune에 보고합니다.

---
Tips. 왜 MDE 설정을 Endpoint.microsoft.com (Intune 포털)에서 진행해야할까?
MDE 포털과 Intune 포털은 각각의 주요 목적과 사용 사례가 다릅니다. MDE 포털은 주로 보안 상태 모니터링과 위협 탐지 및 대응에 중점을 두고, Intune 포털은 장치 및 보안 정책의 중앙 집중식 관리, 정책 생성 및 배포, 상태 모니터링에 중점을 둡니다. 이러한 이유로 MDE 설정을 Endpoint.microsoft.com (Intune 포털)에서 진행하는 것이 유용합니다.

![image](https://github.com/user-attachments/assets/d215bec9-89de-4a53-afb5-125afdb582ab)

---

### ASR Policy 설정하기
**1. Profile 생성하기**
Intune console > Endpoint Security > Attack Surface Reduction > + create policy 

![image](https://github.com/user-attachments/assets/b4b48f79-abe6-4b9f-8a6c-a8423e9831ce)

**2. Rule 생성하기**

![image](https://github.com/user-attachments/assets/77e48f3c-f5e9-42c4-8a6d-7bcb1ba278a6)

![image](https://github.com/user-attachments/assets/248f7687-9f25-4d7f-b644-11fd615ac95f)

시나리오: 회사에서 직원들이 주로 사용하는 Office 어플리케이션을 보호
설정예시: 
* Block Office applications from creating executable content 규칙을 Block으로 설정합니다. 이를 통해 Office 문서에서 실행 파일을 생성하는 것을 차단하여 악성 문서로 인한 보안 위협을 줄일 수 있습니다.
* Block Win32 API calls from Office macros 규칙을 Block으로 설정합니다. 이를 통해 악성 매크로가 시스템 API를 호출하여 악성 활동을 수행하는 것을 방지할 수 있습니다.
* Block all Office applications from creating child processes 규칙을 Block으로 설정합니다. 이를 통해 Office 어플리케이션이 Child processes를 생성하지 못하도록 하여 악성 활동을 방지할 수 있습니다.
  
![image](https://github.com/user-attachments/assets/07f3b624-65c4-4b44-bdd1-b6d3cae1f9ed)

* ASR Only Per Rule Exclusions
특정 ASR 규칙에 대해 예외설정하는 기능입니다. 즉, 특정 규칙에 대해서만 예외를 설정할 수 있으며, 다른 규칙에는 여전히 적용됩니다.

예를 들어, Block Office applications from creating executable content 규칙에 대해 C:\Program Files\MyApp\MyApp.exe를 예외로 설정하면, 이 파일은 해당 규칙에서만 제외되고, 다른 ASR 규칙에는 여전히 적용됩니다.

![image](https://github.com/user-attachments/assets/69bf3815-75de-4553-885f-6f815a89d027)
* Attack Surface Reduction Only Exclusions

특정 경로에 있는 파일이나 완전히 지정된 리소스에 대해 Attack Surface Reduction (ASR) 규칙이 적용되지 않도록 예외를 설정할 수 있습니다. 예를 들어, C:\Windows 경로를 추가하면 이 디렉터리에 있는 모든 파일이 ASR 규칙의 적용을 받지 않게 됩니다. 예외를 추가할 때는 경로 또는 완전히 지정된 리소스 이름을 문자열로 입력해야 합니다.

* Controlled Folder Access
이 설정은 Controlled Folder Access 기능을 활성화하거나 비활성화할 수 있는 옵션을 제공합니다. Controlled Folder Access는 랜섬웨어와 같은 악성 소프트웨어로부터 중요한 폴더를 보호하는 기능입니다. 보호된 폴더와 허용된 어플리케이션을 지정할 수 있습니다.
* Controlled Folder Access Protected Folders: 보호할 폴더를 지정할 수 있습니다.예시: C:\Users\Public\Documents 폴더를 보호 폴더로 추가
* Controlled Folder Access Allowed Applications: 보호된 폴더에 접근할 수 있는 허용된 어플리케이션을 지정할 수 있습니다. 예시: C:\ProgramFiles\MyApp\MyApp.exe 어플리케이션을 허용된 어플리케이션으로 추가


