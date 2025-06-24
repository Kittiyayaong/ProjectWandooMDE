# MDE Basic Setting

## 3. Device Group 

### Device group이란? 
보안 운영 팀의 책임을 논리적으로 분리하기 위해 사용됩니다. 장치 그룹을 생성하면 특정 기준(예: 이름, 태그, 도메인 등)에 따라 장치를 그룹화하고, 해당 그룹에 대한 역할 접근 권한을 부여할 수 있습니다. 이를 통해 특정 장치 그룹에 대한 보안 정책을 적용하고, 다양한 설정(예: 웹 콘텐츠 필터링, 억제 규칙, 정책 기준선 등)을 적용할 수 있습니다
![image](https://github.com/user-attachments/assets/df279b5e-cbb6-426e-a9e7-1e0d76e3c46b)

---
예시: MS 직원 장소영은 사내 PC로는 인트라넷에 접근할 수 있지만, BYOD를 사용시에는 접근 불가하다.
* RBAC: 장소영이 MS 직원으로서 사내 PC를 사용할 때 인트라넷에 접근할 수 있는 권한을 부여받았습니다. (RBAC를 통해 특정 역할에 대한 접근 권한을 설정)
* Device group: BYOD(Bring Your Own Device)를 사용할 때는 인트라넷에 접근할 수 없도록 설정되었습니다.  (Device group을 통해 특정 장치 그룹에 대한 접근 권한을 제한)
---

## ✅ Device Group 설정하기 
**1. Device Group 생성하기: MDE Console > Setting > Endpoints > Device Groups > + add device group**
![image](https://github.com/user-attachments/assets/ddc53f61-b404-4154-83cd-dd67e4b6d6d6)

**2. Remediation level 설정하기 : IT 환경에서 감지된 보안 위협을 처리하는 자동화 및 개입의 정도를 의미합니다.** 
* No automated response (자동 응답 없음)
* Semi - require approval for all folders (모든 폴더에 대해 승인 필요)
* Semi - require approval for non-temp folders (임시 폴더가 아닌 폴더에 대해 승인 필요)
* Semi - require approval for core folders (핵심 폴더에 대해 승인 필요)
* Full - remediate threats automatically (완전 자동으로 위협 해결)

---
> ⭐️ Tip.
> 
> "Full Remediate Threats Automatically"를 설정하면 시스템이 감지된 위협을 자동으로 해결하므로, 해당 설정값을 추천 (수동 승인이나 개입 없이 자동)
---

**3. Device group 조건 설정**
장치 그룹은 여러 조건을 기반으로 동적으로 장치를 추가할 수 있습니다. 
![image](https://github.com/user-attachments/assets/4cc4f2b1-7f1e-4a46-aa38-39ed5643e2f0)

조건 조합 (AND/ OR)
* AND: 각 조건 중 일부 조건을 비워두면 해당 조건은 무시됩니다. 
“이름이 "Desktop-"으로 시작하고 도메인이 "Contoso"로 시작하는 경우”
두 조건이 모두 참이어야 장치가 그룹에 추가됩니다.
* OR: 각 조건의 오른쪽에 있는 "+" 버튼을 클릭하여 새로운 조건을 추가
“이름이 "Desktop-"으로 시작하거나, 이름이 "demo"로 끝나거나, 도메인이 "Contoso"로 시작하는 경우”

**4. 시나리오 1: 특정 부서(예: 마케팅 부서)의 장치들을 그룹화하여 해당 부서에 맞는 보안 정책을 적용합니다.**
![image](https://github.com/user-attachments/assets/dbeaf994-0bca-485d-bc9e-e19aa69a83ce)

예시 조건: 
  * 장치 이름이 "Marketing-"으로 시작하고,
  * 도메인이 "Contoso"로 시작
  * 장치 태그에 "Marketing"이 포함
  * 운영 체제가 Windows 10인 경우

**5. 시나리오 2: Sales 부서에서 Project Y를 위해 사용되는 장치들을 그룹화합니다. 이 장치들은 Windows 10 또는 Windows 11을 실행 중이며, 뉴욕 사무실에 위치해 있습니다.**

![image](https://github.com/user-attachments/assets/7dc7d116-c3c2-4339-bf72-1585a2cdf48b)

예시 조건: 
* 장치 이름이 "Sales-"로 시작하고
* 도메인이 "ProjectY"로 시작하며
* 장치 태그에 "NewYork"이 포함되고
* 운영 체제가 Windows 10 또는 Windows 11인 경우
* 추가 조건으로 장치 이름이 "-NY" 또는 "-HQ"로 끝나거나
* 도메인이 "Sales" 또는 "Marketing"을 포함하는 경우

**6. 사용자 접근 권한 설정 (Optional)**
![image](https://github.com/user-attachments/assets/13f0281d-7cf3-4f47-b8cd-d0d6800460d0)

이 단계는 선택 사항으로, 특정 장치 그룹에 접근할 수 있는 사용자와 Entra ID 그룹을 선택할 수 있습니다. 이를 통해 다음과 같은 기능을 제공합니다:
* 특정 사용자 및 그룹에 접근 권한 부여: 특정 사용자나 Entra ID 그룹을 선택하면, 선택된 사용자와 그룹만 해당 장치 그룹에 접근할 수 있습니다. 선택되지 않은 사용자는 해당 장치 그룹에 접근할 수 없습니다
* 티어링 모델 유지: 이 기능은 티어링 모델을 유지하는 데 매우 유용합니다. 예를 들어, 도메인 컨트롤러만 포함된 장치 그룹을 생성하고, T0 관리자만 이 장치들에 접근할 수 있도록 설정할 수 있습니다.

**7. 설정 완료**
![image](https://github.com/user-attachments/assets/eb3f1a55-5a1b-4a91-ba51-1ab172ee1207)
