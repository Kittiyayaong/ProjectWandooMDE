## 3. Live Resonse 설정하기 

### Live Resonse란? 
Live Response는 보안 운영 팀이 원격 셸 연결을 사용하여 장치에 즉시 액세스할 수 있도록 하는 기능입니다. 이를 통해 심층적인 조사 작업을 수행하고 실시간으로 식별된 위협을 신속하게 차단할 수 있습니다

### 시나리오
사용자A의 PC에서 의심스러운 파일이 run되어서, medium-severity level의 alert이 생성되었습니다. MDE에서 해당 파일을 block처리하였지만, 운영진입장에서는 모든 것이 정상화되었는지 원격으로 확인하고 싶어요.
* 고객사 Needs: 발생한 incident에 대해서 원격으로 정상화되었는지 확인
* 설정 방향:  해당 incident에서 live respons를 활성화하여 shell을 통해 확인.

### ✅ 설정하기 
1. Live Response 활성화하기
* 설정위치: MDE console > setting > endpoints > advanced setting > Live response 

![image](https://github.com/user-attachments/assets/89564b76-29a2-448a-a5f7-0c86b1991682)

2. 설정값 설명
* Live Response: 적절한 RBAC 권한을 가진 사용자가 원격 셸 연결을 사용하여 권한이 부여된 장치를 조사할 수 있도록 합니다.
* Live Response for Servers: Live Response 권한을 가진 사용자가 권한이 부여된 서버(Windows Server 또는 Linux 장치)에 원격으로 연결할 수 있도록 합니다.
* Live Response unsigned script execution: Live Response에서 서명되지 않은 PowerShell 스크립트를 사용할 수 있도록 합니다.

3. 설정 완료 
