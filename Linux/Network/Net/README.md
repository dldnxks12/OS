#### Linux Network Programming 


	IP Addr

		인터넷에 연결된 호스트는 반드시 IP 주소와 Port 번호를 가지고 있다. 이를 통해 특정 호스트를 알 수 있다.

		해당 호스트에서는 특정 Port에서 어떤 신호가 오기를 기다리는 프로세스가 돌아가고 있다. 

			이렇게 접속을 기다리면서 어떤 작업을 해주는 프로세스를 "서버 프로세스" 라고 한다.

			반대로 서버에 접속해서 어떤 작업을 수행하는 프로세스를 "클라이언트 프로세스"라고 한다. 

<div align=center>
	
![image](https://user-images.githubusercontent.com/59076451/130128897-8869f6a2-9218-4f83-8a01-65a9337687e9.png)
	
</div>	

		

		그럼 어떤 서버 프로세스가 어떤 Port로 대기 중인지 알 수 있는 방법은 뭘까?

		이것은 사전에 공유되지 않는 한 알기 어렵지만, 유명한 서비스들은 정해진 Port를 사용한다. 

			ex) 메일 서버 (SMTP) : 25 port , 웹 서버 (HTTP) : 80 port, ... 

				/etc/services 에 나열되어있다. 

		
	TCP/UDP 


		IP 보다 상위 layer인 TCP/UDP Level에서는 btye 열인 stream을 전송한다.

		이를 잘라 패킷으로 만들어 IP layer에 내려보내 전송한다. 

		받는 쪽에서는 잘려긴 패킷을 보고 잘 맞춘 후 byte 열을 만들어 스트림으로 받아들인다.		



	Host name 

		네트워크 상의 호스트(PC)는 IP 주소로 식별된다. 하지만 IP주소는 숫자이므로 사람이 다루기 어렵다.

		따라서 이 IP주소 대신에 Host name을 이용한다. 

			ex) www.google.com 

		Host name과 IP 주소를 매칭시켜놓으면 사람은 외우기 쉽고 쓰기 쉬운 host name을 사용하고,

		PC는 이를 IP 주소에 해당하는 숫자로써 다루면 된다.

		
	DNS (Domain Name System)

		호스트에 대해서 IP 주소와 host name을 모두 매칭시켜 놓은 저장소라고 보면 된다. 

		DNS는 host name을 domain 이라고 하는 영역에 나눠서 관리하고, 이를 전 세계에 알린다.

		domain이라 함은 , com, org, kr 등의 이름을 가진 name을 관리하는 이름 영역이다.

		만일 com 이라는 이름을 가진 host name을 찾는다면, com domain을 관리하는 DNS 서버에 물어봐야하는 것이다. 
			

	주소 체계

		MAC Addr : 네트워크 카드나 라우터 같은 HW 들이 서로를 인식하기 위해 사용하는 주소

		IP Addr  : OS에서 네트워크 상의 다른 단말들을 구분하기 위해 사용하는 주소  

		Domain name(host name) : 사람이 서버나 단말을 구분하기 위해 사용하는 주소 

		Port Num : 클라이언트 입장에서 서버를 찾았을 때, 우리가 사용할 서비스를 지정해야 한다. 이 때 사용하는 번호


	Shutdown() 

		close() 함수를 사용하면 서버에서의 읽기/쓰기 소켓을 모두 닫는다.

		하지만 shutdown() 함수를 사용하면 둘 중 하나만 선택해서 닫을 수 있다. 

			int shutdown(int sockfd, int how)

				how? 

				1. SHUT_RD : 입력 스트림 종료 

				2. SHUT_WR : 출력 스트림 종료

				3. SHUT_RDWR : 입출력 스트림 종료  == close() 
