## 1. Anti-virus 설정하기 

### 고객사 니즈
1. 고객사 Needs: 네트워크 파일 및 이동식 드라이브 스캔
2. 목적: 네트워크 파일과 이동식 드라이브를 스캔하여 악성 소프트웨어를 탐지
3. Antivirus 설정값:
* Allow Scanning Network Files: Enabled
* Allow Full Scan Removable Drive Scanning: Enabled
* Allow Full Scan On Mapped Network Drives: Enabled

### AV 설정하기 
1. 설정 위치
Intune console > Endpoint Security > Antivirus > + create policy > Platform: windows, Profile: MD Antivirus

![image](https://github.com/user-attachments/assets/83fcadb2-cfb1-415b-89d6-19d0690def43)

Profile 유형 (참고)
* Defender Update controls: 이 프로필 유형은 Microsoft Defender의 업데이트 설정을 제어하는 데 사용됩니다. 여기에는 바이러스 정의 파일 및 보안 인텔리전스 업데이트의 빈도와 소스를 설정하는 옵션이 포함됩니다. 이를 통해 최신 보안 업데이트를 유지하고 새로운 위협에 대응할 수 있습니다.
* Microsoft Defender Antivirus exclusions:이 프로필 유형은 Microsoft Defender Antivirus에서 제외할 항목을 설정하는 데 사용됩니다. 특정 파일, 폴더, 파일 형식 또는 프로세스를 제외하여 스캔하지 않도록 설정할 수 있습니다. 이는 성능을 최적화하고 특정 파일이나 프로세스가 잘못 탐지되는 것을 방지하는 데 유용합니다.
* Microsoft Defender Antivirus:이 프로필 유형은 Microsoft Defender Antivirus의 다양한 설정을 구성하는 데 사용됩니다. 여기에는 실시간 보호, 클라우드 기반 보호, 이메일 스캔, 네트워크 파일 스캔, 스크립트 스캔 등의 옵션이 포함됩니다. 이를 통해 시스템을 다양한 형태의 악성 소프트웨어로부터 보호할 수 있습니다.
* Windows Security Experience:이 프로필 유형은 Windows 보안 환경을 사용자에게 제공하는 설정을 구성하는 데 사용됩니다. 여기에는 Windows 보안 센터의 사용자 인터페이스 설정, 알림 설정, 보안 기능의 가시성 등을 포함합니다. 이를 통해 사용자가 보안 상태를 쉽게 확인하고 필요한 조치를 취할 수 있도록 도와줍니다.

2. Policy Configuration setting
![image](https://github.com/user-attachments/assets/344e22c1-a507-408f-a948-cb05f1c0caf3)
* Allow Scanning Network Files: Enabled
* Allow Full Scan Removable Drive Scanning: Enabled
* Allow Full Scan On Mapped Network Drives: Enabled

3. 설정값 적용
![image](https://github.com/user-attachments/assets/1eac1f6c-034d-4a3c-b317-3ab7ebf31c71)

4. 설정 완료
![image](https://github.com/user-attachments/assets/613375a7-27eb-45da-b176-af1dbdb8efa7)

### 🔗 [다음 Lab으로 이동하기 »](https://github.com/Kittiyayaong/ProjectWandooMDE/blob/main/MDE%20Module03%20-%20NGP-02.Tamper%20Protection.md)
