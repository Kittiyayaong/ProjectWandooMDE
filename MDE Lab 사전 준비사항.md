## Lab 사전 준비사항 

## Endpoint.microosft.com 에서 ASR 설정하기 위한 준비과정
* Azure에서 Intune activation
* Defender에서 Intune connection
* Endpoint.Microsoft.com에서 MDE Connection
* 본 랩은 "Security Administrator" 권한을 기반으로 제공됩니다. (최소 security admin 권한으로 참석 요망) 


1. Azure에서 Intune activation
이 설정은 모바일 디바이스 관리(MDM) 및 Windows 정보 보호(WIP) 정책을 구성하는 것으로, Intune을 통해 디바이스와 데이터를 중앙에서 관리하고 보호할 수 있게 해줍니다

![image](https://github.com/user-attachments/assets/6f4cda41-660c-41de-b654-8c37d0cf6ee2)

2. Defender에서 Intune connection 설정

![image](https://github.com/user-attachments/assets/999524fc-8cac-4701-b2e5-907fc2df2554)

3. Intune에서 MDE 연결

![image](https://github.com/user-attachments/assets/1eee9003-f7aa-480e-8144-8489221bbd2c)


> ✅ Tips. Microsoft 365 Defender 역할 종류 (Azure AD 기준)

| 역할 이름                          | 주요 권한                                | 주 사용 목적                |
| ------------------------------ | ------------------------------------ | ---------------------- |
| **Global Administrator**       | 모든 설정 가능 (보안 포함 전체 권한)               | 계정/테넌트 전체 관리용 |
| **Security Administrator**     | 대부분 보안 정책 구성, 디바이스 그룹 및 규칙 설정 가능     | 🔺**실습에 가장 적합**        |
| **Security Reader**            | 경고 보기, Advanced Hunting 보기, 설정 변경 불가 | 모니터링 전용 사용자            |
| **Security Operator**          | 경고 상태 업데이트, 조사 태스크 실행                | 경보 triage 담당자          |
| **Compliance Administrator**   | 데이터 손실 방지, 감사 로그 등 구성                | Purview 관련 실습 시        |
| **Endpoint Security Manager**  | Intune 내 엔드포인트 보안 프로필 구성 권한          | Intune 정책 배포 시 필요      |
| **Intune Administrator**       | 디바이스 등록, 보안 정책 및 앱 배포                | Intune 기반 관리 시 필요      |
| **Cloud Device Administrator** | 디바이스 등록 및 관리                         | Hybrid Join 구성 시 사용    |
