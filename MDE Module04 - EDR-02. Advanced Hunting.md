### Advanced Hunting이란? 
쿼리 기반 위협 검색도구로, 네트워크에서 발생하는 이벤트를 탐색하고 위협 지표와 엔티티를 식별할 수 있습니다. 최대 30일 동안의 원시 데이터를 탐색할 수 있습니다. 실시간으로 동작하는 기능이 아니기 떄문에 사용자가 필요할 때 쿼리를 작성하여 추가적인 정보를 탐색하고 분석에 사용됩니다. 

1. Advanced Hunting의 주요 기능
* 데이터 탐색: 최대 30일 동안의 원시 데이터를 탐색하여 위협 지표와 엔티티를 식별합니다.
* 유연한 데이터 접근: 다양한 이벤트와 시스템 상태를 탐색할 수 있으며, Kusto Query Language (KQL)를 사용하여 쿼리를 작성할 수 있습니다.
* 탐지 규칙 생성: Advanced Hunting 쿼리를 사용하여 탐지 규칙을 생성하고, 이를 통해 의심스러운 활동을 모니터링하고 대응 조치를 취할 수 있습니다

2. Advanced Hunting 활용 
예시: MDE를 사용하는 고객이 EDR, EDR in Block Mode, Advanced Hunting을 함께 사용하는 경우에 바이러스가 침투

* 바이러스 침투: 악성 파일이 시스템에 침투하여 실행됩니다.
* EDR 탐지: EDR이 악성 파일의 실행을 탐지하고, 이를 보고합니다.
* Advanced Hunting 분석: 보안 팀은 Advanced Hunting을 사용하여 추가적인 분석을 수행합니다. 예를 들어, 바이러스가 어떻게 시스템에 침투했는지, 유사한 위협이 다른 시스템에 존재하는지 확인합니다

3. Advanced Hunting 쿼리 작성 방법
Advanced Hunting은 Kusto Query Language (KQL)를 기반으로 하며, 이를 통해 네트워크 이벤트를 탐색하고 위협 지표와 엔티티를 식별할 수 있습니다. 

4. 쿼리 작성의 기본 단계
* 테이블 선택: 쿼리는 일반적으로 테이블 이름으로 시작합니다. 예를 들어, DeviceProcessEvents 테이블을 선택할 수 있습니다.
* 시간 범위 설정: 쿼리의 첫 번째 요소는 시간 필터입니다. 예를 들어, 지난 7일 동안의 데이터를 탐색하려면 | where Timestamp > ago(7d)를 사용할 수 있습니다.
* 조건 추가: 특정 조건을 추가하여 데이터를 필터링합니다. 예를 들어, PowerShell 실행 이벤트를 찾으려면 | where FileName in~ ("powershell.exe", "powershell_ise.exe")를 사용할 수 있습니다.
* 결과 정렬 및 표시: 결과를 정렬하고 표시할 열을 선택합니다. 예를 들어, | project Timestamp, DeviceName, FileName, ProcessCommandLine를 사용할 수 있습니다.

### 시나리오
* 고객사 Needs: 최근 30일 동안 안티바이러스 감지가 2회 이상 발생한 장치들을 확인 
* 설정 방향: Advanced hunting을 통해 추가적인 내용을 쿼리를 통해 수동 검색한다.

### ✅ Advanced Hunting Query test
1. 위치: MDE console > Hunting > Advanced Hunting 

![image](https://github.com/user-attachments/assets/ed915a13-de31-465f-8278-803b882bf850)

2. 시나리오 1. PowerShell 다운로드 이벤트 탐지

```powershell
DeviceProcessEvents 
| where Timestamp > ago(7d)
| where FileName in~ ("powershell.exe", "powershell_ise.exe") 
| where ProcessCommandLine has_any("WebClient", "DownloadFile", "DownloadData", "DownloadString", "WebRequest", "Shellcode", "http", "https") 
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType 
| top 100 by Timestamp
![image](https://github.com/user-attachments/assets/b87a7bed-d82f-4892-a4f6-5a71fcb36d57)
```

* DvcipCrProcessEvents: 이 쿼리는 DvcipCrProcessEvents 테이블에서 데이터를 가져옵니다.
* where Timestamp > ago(7d): 지난 7일 동안의 데이터를 필터링합니다.
* where FileName in~('powershell.exe', 'powershell_ise.exe'): powershell.exe 또는 powershell_ise.exe 파일이 실행된 이벤트를 필터링합니다.
* where ProcessCommandLine has_any ~ : 프로세스 명령줄에 "WebClient", "DownloadFile", "DownloadData", "DownloadString", "WebRequest", "Shellcode", "http", "https" 중 하나라도 포함된 이벤트를 필터링합니다.
* project Timestamp~: 결과에서 Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, FileName, ProcessCommandLine, RemoteIp, RemoteUrl, RemotePort, RemoteIPType 열을 선택합니다.
* top 100 by Timestamp: Timestamp 기준으로 상위 100개의 결과를 반환합니다.

3. 시나리오 2. 최근 30일 동안 안티바이러스 감지가 2회 이상 발생한 장치들을 확인

```powershell
DeviceEvents 
| where Timestamp > ago(30d) 
| where ActionType == "AntivirusDetection“
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId, DeviceName 
| where count_ > 2
![image](https://github.com/user-attachments/assets/3887d19c-c39d-46d3-94e7-907de116cf43)
```
* DeviceEvents 테이블에서 Timestamp가 최근 30일 이내인 이벤트를 필터링합니다.
* ActionType이 "AntivirusDetection"인 이벤트를 필터링합니다.
* DeviceId와 DeviceName별로 이벤트를 그룹화하고, 각 그룹에서 가장 최근의 Timestamp와 ReportId를 선택하고, 이벤트 수를 계산합니다.
* 이벤트 수가 2개를 초과하는 그룹만 선택합니다.

### ✅ Advanced hunting detection rule 
1. Detection rule이란?
Detection rule은 보안 시스템에서 특정 이벤트나 활동을 감지하고 경고를 생성하기 위해 설정하는 규칙입니다. 이러한 규칙은 보안 위협을 조기에 발견하고 대응할 수 있도록 도와줍니다.

![image](https://github.com/user-attachments/assets/bf1dff3c-34e7-4753-a8bd-d8c68a687d25)

![image](https://github.com/user-attachments/assets/43b744e5-fb59-4e56-a22e-603000a2608e)

2. Category
Detection Rules의 특정 유형의 보안 이벤트

![image](https://github.com/user-attachments/assets/2fea3c68-c5b2-4a50-83d9-7ed533b65867)

3. Threat analytics report (Optional)

![image](https://github.com/user-attachments/assets/0d71d266-19ad-4e61-890d-b5ea89a6bd34)

4. Impacted entities
   
감지된 이벤트가 영향을 미치는 장치를 식별하기 위해 사용됩니다. 이 설정은 감지된 이벤트가 어떤 장치와 관련이 있는지를 명확히 하기 위해 필요합니다. Device name 열을 선택하면 해당 장치 이름을 기준으로 이벤트를 추적하고 분석할 수 있습니다. 

![image](https://github.com/user-attachments/assets/cfe3ef00-01b1-4e50-85ad-576e38376118)

5.  Actions: 
쿼리에서 발견된 엔터티에 대해 적용할 수 있는 조치를 선택합니다. 이 설정은 감지된 위협에 대해 자동으로 취할 조치를 정의합니다.
* Collect investigation package: 조사 패키지를 수집합니다. 장치에서 추가적인 데이터를 수집하여 심층 분석을 수행하는 데 사용됩니다.
* Run antivirus scan: 안티바이러스 검사를 실행합니다. 감염된 장치에서 악성 소프트웨어를 탐지하고 제거하기 위해 사용됩니다.
* Isolate device: 장치를 격리합니다. 감염된 장치가 네트워크에서 다른 장치로 위협을 전파하지 않도록 하기 위해 사용됩니다.
* Initiate investigation: 조사를 시작합니다. 감지된 위협에 대해 심층 조사를 수행하는 데 사용됩니다.
* Restrict app execution: 애플리케이션 실행을 제한합니다. 감염된 장치에서 특정 애플리케이션의 실행을 제한하여 추가적인 위협을 방지합니다.

![image](https://github.com/user-attachments/assets/2dcadf1a-a0e8-46c5-80da-4657cd83b909)

6. Scope: demo group 선택
경고를 적용할 대상을 설정합니다. 이 설정은 감지 규칙이 적용될 장치나 장치 그룹을 정의합니다.
* All devices: 모든 장치에 경고를 적용합니다.
* Specific device groups: 특정 장치 그룹에만 경고를 적용합니다

![image](https://github.com/user-attachments/assets/d398b9de-1e42-4a2e-a9f6-dbd6d5e5a39b)

7. 설정 완료
MDE console > Hunting > Custom detection rules에서 생성된 rule 확인

![image](https://github.com/user-attachments/assets/d37b7452-3423-4971-b531-f8d461ddb357)


### 🔗 [다음 Lab으로 이동하기 »](https://github.com/Kittiyayaong/ProjectWandooMDE/blob/main/MDE%20Module04%20-%20EDR-03.%20Live%20Resonse.md)
