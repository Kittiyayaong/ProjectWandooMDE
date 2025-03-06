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
