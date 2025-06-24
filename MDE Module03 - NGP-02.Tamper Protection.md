## 2. Tamper Protection

### 1. Tamper Protection (조작 보호)
바이러스 및 위협 보호 설정이 비활성화되거나 변경되는 것을 방지합니다. 이 기능은 사이버 공격 중에 악의적인 행위자가 보안 기능을 비활성화하려는 시도를 막아줍니다. Tamper Protection이 켜져 있을 때는 설정 변경이 불가능하며, 변경 시도는 차단됩니다

### 2. Tamper Protection 설정하기 

1. 설정 위치
Tamper Protection 설정하기 > Intune console > Endpoint Security > Antivirus > + create policy > Platform: windows, Profile: Windows security experience

> ⭐️ Tip.
>
> 'Windows Security Experience' 프로필: Microsoft Defender for Endpoint의 보안 설정을 통합적으로 관리할 수 있는 기능을 제공합니다. 이를 통해 Windows, macOS, Linux 등 다양한 플랫폼에서 일관된 보안 설정을 관리할 수 있습니다

2. Policy 이름
![image](https://github.com/user-attachments/assets/0c210bf5-2f96-4ce1-a527-7b506d8ad8f3)

3. Tamper Protection enable: On으로 변경 
![image](https://github.com/user-attachments/assets/0582eaa0-5275-4bf3-b9f1-b8a6c196f424)

4. 설정 완료
![image](https://github.com/user-attachments/assets/ff99cada-8cda-405d-b118-5e8b2402c2b0)

### 3. Tamper Protection 디바이스에 설정 적용 
Tamper Protection 정책은 Intune을 통해 설정된 후, 디바이스가 다음번 동기화 주기에 도달하면 자동으로 적용됩니다. 일반적으로 Intune 정책은 디바이스가 8시간마다 동기화되도록 설정되어 있습니다

* 수동적용하기: 대상 디바이스 > 설정 > 계정 > 회사 또는 학교 엑세스 > 정보 > 장치 동기화 상태 > 동기화 

![image](https://github.com/user-attachments/assets/6511c98a-d619-46da-86b1-5803c78a4840)

Device console에서 확인 가능 

![image](https://github.com/user-attachments/assets/fa38c42c-31c4-4c95-b49c-cd12f0d1e6fb)


### 🔗 [다음 Lab으로 이동하기 »](https://github.com/Kittiyayaong/ProjectWandooMDE/blob/main/MDE%20Module04%20-%20EDR-01.EDR(Endpoint%20detection%20%26%20response).md)
