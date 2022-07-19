# 클라우드
> 클라우드 관련 키워드 
> - 고가용성 : 필요할 때 필요한 자원 사용
> - 확장성 : 시스템 확장
> - 민첩성 : 요청에 대한 빠른 반응
> - 탄력성 : 서버가 늘어났다가 줄어들어야 함
> - 글로벌 분산 : 전 세계에 분산 가능
> - 보안성 : 보안성이 뛰어남
> - 재해복구 : 시스템 복구 기능
> - 결함에 따른 복구성 : 소프트웨어에 의한 버그도 알아서 보완이 됨

<br/>

## 클라우드 특징

**규모의 경제**


- IT 인프라 운영 시 작은 규모의 운영보다 큰 규모의 운영이 더 저렴하고 효율적임
- MS, Amazon, Google과 같은 규모가 큰 클라우드 제공업체는 규모의 경제의 이점을 이용해 효율적인 서비스를 제공한다. 


<br/>

**소비기반 모델**
- 선결제 비용 없음
- 고가의 인프라를 구매하고 관리할 필요가 없음
- 필요에 따라 리소스를 추가 지불하고 사용 가능
- 더 이상 필요하지 않은 리소스 중지할 수 있음

<br/>


## 클라우드 서비스 모델
1. 공용 클라우드
2. 사설 클라우드 : 회사 내부에서 구축하여 사용, 특정 사용자에게만 제공
3. 하이브리드 클라우드 : 공용 + 사설, vpn으로 공용 - 사설 연결

## 클라우드 서비스 유형
![image](https://velog.velcdn.com/images%2Fcourage331%2Fpost%2F643a1f95-58a2-4918-bfa4-04a6fc6115c1%2Fimage.png)
- On-premise : 사용자가 모두 관리
- IaaS : 셀프 서비스 포털을 통해 프로비저닝과 관리할 수 있는 컴퓨팅 인프라 제공, 운영 체제(OS)부터 사용자가 관리
- PaaS :platform as a service
- SaaS : 데이터만 사용자가 관리, software as a service, 넷플릭스와 같은 구독형 서비스
  > IaaS가 가장 유연하지만 잘 사용되지 않음

<br/>
<br/>



# Azure 
![image](https://user-images.githubusercontent.com/86597163/177067171-eb98bf6b-f4ab-48d5-8235-d405e3e015a0.png)

### Azure의 가용성
- VM SLA(99.9%) : 단일 VM
- VM SLA(99.95%) : 가용성 집합, 데이터 센터 내 가용성
- VM SLA(99.99%) : 가용성 영역, 데이터 센터 간 가용성
- 다중 지역 재해 복구 : 지역 쌍(central, south), 지역 간 가용성

### Azure 데이터 센터
- 독립적인 전원, 냉각 장치, 네트워크를 갖춘 별도의 시설
- MS에서 직접 구축

### 용어 정리
> - 리소스 : 가상 머신, 데이터 베이스, 가상 네트워크 등 단일 리소스를 나타내는 단위
> - 리소스 그룹 : 리소스를 묶을 수 있는 단위
> - 리소스 공급자 : 원하는 리소스를 제공하는 서비스, 가상 머신의 경우 공급자는 MS
> - 리소스 제공자 : 리소스를 제공하는 주체(MS, Cisco, NetApp 등)

### Azure 사용하기
- **리소스 그룹 만들기** 
![image](https://user-images.githubusercontent.com/86597163/177070725-2cf76f5a-e184-4440-9789-30d5a599353b.png
)
![image](https://user-images.githubusercontent.com/86597163/177070881-8bb27911-ac29-45d9-94bf-892312128956.png)
- **리소스 만들기**
  >공용 ip 주소 생성
  
  ![image](https://user-images.githubusercontent.com/86597163/177071581-5ba55ea2-3740-479b-bf2a-7805b95982eb.png)
  ![image](https://user-images.githubusercontent.com/86597163/177071814-b8387b39-20bf-4470-87fa-2f9fc93f6b25.png)

<br/>

**Azure 포탈 살펴보기**
![image](https://user-images.githubusercontent.com/86597163/177072016-11aa5350-653d-4e44-baf1-08b01ff6b340.png)

<br/>

Cloud Shell
  
![image](https://user-images.githubusercontent.com/86597163/177072692-a0145bf2-b86b-41d0-bb9d-3981a7937b2d.png)
- Azure PowerShell
- Azure CLI

<br/>


**Azure Shell 명령어**
- az account list : account 정보 출력(구독 정보, 이름 등), json 형식

- 명령어로 리소스 그룹 생성
    > az group create --location westus --name MyRG
    
    미국 서부, MyRG라는 리소스 생성

- 명령어로 가상 머신 생성
  > az vm create -n myVM -g MyRG --image UbuntuLTS --generate-ssh-keys

- 리소스 그룹 삭제
  > az group delete -n MyRG

<br/>>

**Azure CLI**
- 설치하기
  > google에 azure cli 검색 후 다운로드

- 설치 확인 
  > 명령프롬프트에 az 입력

- 로그인
  > az login -> 클라우드 계정과 연동됨

- 버전 확인
  > az version

- account 확인
  > az account list 

<br/>


**대시보드**

가상 머신들이 잘 작동하는지 확인하는 역할을 수행한다. 


<br/>

**리소스와 태그**
- 논리적으로 분류 체계를 구성하는 방법
- 최대 50개까지 부여 가능


<br/>


**리소스 이동**
- 구독 간 이동은 양쪽 구독이 동일한 Azure Active Directory에 연결된 경우만 가능
- 리소스와 종속성이 있는 리소스가 있으면 함께 이동(가상머신, 가상 네트워크 등)
- 다른 구독으로 이동하려는 경우 종속성 있는 리소스가 각기 다른 리소스 그룹에 흩어져 있는 경우 먼저 하나의 리소스 그룹으로 모은 다음 이동 가능

<br/>


**리소스 잠금**
![image](https://user-images.githubusercontent.com/86597163/177093810-513d3b60-d217-4b8d-99c0-d4d6ffffcdeb.png)
- 삭제 잠금 추가하기
- 리소스가 잠겨있으면 리소스 그룹도 삭제 불가

<br/>


# Azure Cloud
## 인증과 권한

**인증(Authentication)**
- user, 또는 service 계정 식별
- 정상적인 요청으로 액세스 자격 증명 획득

<br/>


**권한(Authorization)**
- 인증된 user 또는 service의 액세스 수준 정의
- 액세스 할 수 있는 리소스와 함께 수행할 수 있는 작업을 정의




### 테넌트
**테넌트 만들기**
> azure active directory -> 테넌트 관리
  
  ![image](https://user-images.githubusercontent.com/86597163/177096283-a7553a00-b187-41fc-82f8-9bc4ce7af088.png)
![image](https://user-images.githubusercontent.com/86597163/177098634-e9c786e8-6b8e-46b1-895a-8c46bdb79b2c.png)

- 테넌트를 사용하기 위해서는 구독이 필요함


## Azure AD
: azure active directory
- 다중 테넌트 클라우드 기반 디렉터리 및 ID 관리
- 클라우드 애플리케이션 및 리소스용 single sign-on(로그인) 액세스 기능 제공
- 전역 범위에서 원활하게 앱 개발 
- 전체 ID 관리 기능 제공
  - 셀프 서비스 암호 및 그룹 관리
  - 역할 기반 액세스 제어
  - 권한 있는 계정 관리
  - 앱 사용량 모니터링
  - 디바이스 등록
  - 경고 
  - MFA(별도의 인증 체계, 오버워치 로그인 후 핸드폰 인증)
  
![image](https://user-images.githubusercontent.com/86597163/177105773-89dc2f5d-85a9-4c09-aa5e-4fbb846053b2.png)