# Network
## Azure Virtual network
> 사전 지식
> - IPv4는 총 32비트의 숫자 구성(4,294,967,296개)
> - 가용 가능한 IP는 3,706,452,992개로 충분하지 않음
> - Private network로 해결해야 함


- Azure 데이터 센터에 가상의 네트워크를 만들어 네트워크 기반 통신
- Azure 지역에 종속되며 가상의 네트워크이기 때문에 생성에 제한이 없음
- 다른 계정의 가상 네트워크와는 독립됨


### CIDR(Classless inter-domain routing)
![image](https://user-images.githubusercontent.com/86597163/177228060-7007a0a9-d227-4b27-a1ad-377de94def67.png)
- IP를 표현할 때 사용하는 표현법(subnet mask(A,B,C클래스로 쪼갬)와 비슷한 기능, 더 잘게 쪼갬)
- 클라우드에서는 CIDR로 비트를 쪼갬

![image](https://user-images.githubusercontent.com/86597163/177228209-237efa66-51ca-4e55-b4bf-66aadd86e675.png)
![image](https://user-images.githubusercontent.com/86597163/177228282-c5406130-21f4-4f3a-8770-11750f30eb27.png)

> 게이트웨이를 통해야만 개인 컴퓨터에 접속할 수 있음

![image](https://user-images.githubusercontent.com/86597163/177228420-031d0d47-2963-4046-a3b8-e58cb2a72c2b.png)
> /28 : 28비트를 마스크로 막으면 마지막 4비트가 남음 -> 16대까지 사용 가능


#### 네트워크 구성
![image](https://user-images.githubusercontent.com/86597163/177228490-516b1d2f-54b2-4984-91fe-a87241dbdbc4.png)

> 네트워크가 0.0인 자리부터 사용할 수 있다.
> 
> 서브넷 3에는 192.168.3.0/24 -> 3번을 할당 받음
> 
> 서브넷 2는 2번을 할당
> 
> 이런식으로 네트워크를 쪼개면 방해받지 않고 네트워크 사용 가능
 

<br/>


### SUBNET
- 실제 Azure VM이 배치되는 네트워크 단위
- 가상 네트워크 안에 종속됨
- 가상 네트워크와 서브넷은 크기 조절 가능(CIDR)
- 성능, 속도 향상
- 보안 향상



### 가상 네트워크 만들기
1) 리소스 그룹(VNETTest) 만들기
2) 생성한 리소스 그룹에서 Virtual network 리소스 만들기
![image](https://user-images.githubusercontent.com/86597163/177229922-0765198d-daf5-49a7-9239-483e4daf29e6.png)

> BastionHost
> - vm 접근방법 중 하나
> - 접속하지 않고 서버를 관리할 수 있게 함
> 
> DDoS Protection
> - 디도스 접속을 방지하는 서비스
> 
> 방화벽


![image](https://user-images.githubusercontent.com/86597163/177231918-b47cc729-581d-4777-a0d7-3c290c82593e.png)


<br/>


### Azure Virtual Machine

### 가상 머신 만들기
1) ubuntu server 18.04 만들기
![image](https://user-images.githubusercontent.com/86597163/177238040-08d6e64b-30d8-422b-9783-89e720b23080.png)

http://bit.ly/KWJ_Azure_HOL2 




인바운드 포트 규칙
포트넘버 80(in80)
any
대상포트범위 80
우선순위 310
이름 in80

아웃바운드 포트 규칙
포트80


<br/>



### Azure Storage Account
1) **Blob storage**
   - 브라우저에 이미지나 문서 직접 제공
 - 설치 등 분산 액세스용으로 파일 저장 
 - 비디오 및 오디오 스트리밍 가능

  > 리소스 그룹에서 스토리지 계정 만들기
  >
  > blob -> 컨테이너 만들기 -> 컨테이너 추가(공용 액세스 수준 : blob(주소 알면 접근 가능))
  > 
  > 이미지 다운 -> 컨테이너(data)에서 이미지 업로드
  > * 액세스 계층 : 핫, 쿨, 아카이브(파일 신청 -> 파일 불러옴)
  >
  > 업로드한 이미지의 주소 : https://labuser14storage.blob.core.windows.net/data/omg.jpg
  >
  >스토리지에 파일 올리고 스토리지에서 파일을 가져옴


  > azure storage explorer에서도 스토리지를 만들 수 있음
  >
  > azure storage explorer에 접속 -> 구독 계정 접속
  >
  > azure에서 생성한 storage에 접근할 수 있다.

2) **파일 서비스**
> 파일 서비스 -> 파일 공유 -> 파일 스토리지 생성
> 
> 연결 -> 스토리지 계정 키(코드 복사, 파워 shell에서 실행)
> 
> 파워shell(관리자모드)실행 -> 복사한 코드 입력
> 
> 탐색기에서 network location에 빈 네트워크 드라이브가 생성됨


3) **파이썬사용**
>[파이썬으로 파일 사용하기](https://docs.microsoft.com/ko-kr/azure/storage/files/storage-python-how-to-use-file-storage?tabs=python)




