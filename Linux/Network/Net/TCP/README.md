#### TCP 


- TCP

    TCP는 연결 기반의 신뢰성이 있는 통신 방식이다.

    주로 서버와 클라이언트 간 통신 방식으로 사용되는데, UDP 방식보다는 조금 더 복잡한 방식으로 Code가 작성된다.

---
  
- TCP Server

    TCP 서버는 소켓을 생성한 후 bind() 하는 과정은 UDP 서버와 동일하다.
    
    서버는 클라이언트와의 통신을 위해 소켓을 생성하고, 이를 bind()함수를 이용해서 운영체제( 커널 )에 서비스를 연결(등록)한다.
    
    이렇게 되면 이제 서버로 접속하는 클라이언트의 데이터를 받을 수 있도록 준비가 된다.
   
   
   
    하지만 UDP와는 다르게 TCP는 클라이언트가 3 way handshaking( connect() )을 통해 서버에 접속하기 때문에 
    
    클라이언트의 대기를 처리하기 위한 Queue가 필요하다!       
    
    이를 위해 listen() 함수를 통해 Queue를 생성하고, accept() 함수를 통해 클라이언트의 접속을 기다릴 수 있다.
    
        listen() 함수는 연결 요청을 할 수 있는 소켓의 최대 수를 명시하고, 이를 넘어서는 클라이언트의 연결 시도는 거부된다.
    


    서버에서 클라이언트의 연결에 대한 큐를 확보한 후에는 클라이언트의 연결을 대기해야한다 - accept()
    
    accept() 함수를 통해 서버에 클라이언트가 연결되면, 이제 클라이언트와 통신할 수 있는 소켓에 대한 fd가 반환된다. 
    
        즉, 임시 fd를 생성해서 서버와 클라이언트가 통신할 수 있게 해주는 것 !
    
   
---

- TCP Client

    TCP 클라이언트는 먼저 소켓을 생성하고 서버에 접속해야 한다. 이 때 connect() 함수를 사용한다.
    
    서버에 접속된 후에는 read(), write() 함수를 통해 통신을 진행해도 되고, recv(), send() 함수를 사용해도 된다.
    
        소켓은 file descriptor로 취급받기 때문에 read(), write() 같은 file descriptor 기반의 파일 입출력 함수를 사용할 수 있는 것이다.
    
    UDP와 달리 이미 서버에 접속해 있으므로 데이터를 보낼 때 서버의 정보를 사용할 필요가 없다. 


**TCP도 UDP와 동일하게 통신 작업이 완료되면 close() 함수로 소켓을 닫아주자!**
