# NetWhat
## IP주소란?
*  IP주소란 인터넷 상에서 통신하기 위해 각각의 컴퓨터 및 통신장비에 부여하는 고유한 주소를 의미한다. 인터넷 통신을 하기 위해서는 IP주소가 필수적으로 필요하다.
*  IP주소는 IPv4, IPv6 2가지 종류가 있으며, 일반적으로 IP주소라 하면 IPv4주소를 말한다.
* https://m.blog.naver.com/PostView.naver?blogId=hostinggodo&logNo=220589113088&proxyReferer=https:%2F%2Fwww.google.com%2F
### IPv4
* 12자리, 10진수 숫자 배열로 표현.
* 0.0.0.0 ~ 255.255.255.255까지의 숫자 조합으로 사용. 32비트.
* 최대 약 43억개의 서로 다른 주소를 부여할 수 있지만, 인터넷 사용자가 급증하면서 고갈 문제에 처함.

### IPv6
* IPv4의 고갈문제를 해결하기 위해 제시된 대안.
* 128비트.


# 예비문제

# Q. What are the different layers of the OSI model?
A. Application - Presentation - Session - Transport - Network - Data Link - Physical
* OSI7계층 정리: https://velog.io/@dyllis/OSI-7%EA%B3%84%EC%B8%B5-%EC%A0%95%EB%A6%AC
* 국제표준화기구(ISO)에서 만든 네트워크 통신의 7단계 과정.
* (최상위)응용 -> 표현 -> 세션 -> 전송 -> 네트워크 -> 데이터링크 -> 물리(최하위)
![image](https://user-images.githubusercontent.com/52701529/119629052-a039d700-be48-11eb-9a7b-41a39ceee593.png)

# Q. What is the network address of a host with an IP address of 116.45.224.50/8?
A. 116.0.0.0

* 네트워크 아이디 구하는 방법: https://dlgkstjq623.tistory.com/474
* 서브넷 마스크: 기존 IPv4 체계에서 표현할 수 있는 주소가 모자라서, 이를 나누어 쓰게 하기 위해 서브넷 마스크를 고안.
* 

# Q. _______ translates Internet domain names and host names into IP addresses
A. Domain name system
* 도메인 관련 자료: https://xn--3e0bx5euxnjje69i70af08bea817g.xn--3e0b707e/jsp/resources/domainInfo/domainInfo.jsp
* 도메인이란? 도메인은 인터넷에 연결된 컴퓨터를 사람이 쉽게 기억하고 입력할 수 있도록 문자(영문, 한글 등)로 만든 인터넷주소이다.
* ![image](https://user-images.githubusercontent.com/52701529/119633905-25bf8600-be4d-11eb-8cc2-31ca64f3875a.png)
* 도메인 네임 시스템(DNS) 관련 자료: https://xn--3e0bx5euxnjje69i70af08bea817g.xn--3e0b707e/jsp/resources/dns/dnsInfo.jsp
* 네트워크 상에서 컴퓨터들은 IP주소를 이용하여 서로를 구별하고 통신한다. 사람들이 네트워크를 통해 원격의 컴퓨터에 접속하기 위해서는 IP주소를 이용해야 하지만, 이를 일일이 외울 수 없기 때문에 쉽게 기억할 수 있는 도메인 주소 체계, DNS를 사용한다.
* DNS(Domain Name Server)는 할당된 도메인 영역에 대한 정보를 가지고 있는 서버로, 주로 도메인을 IP주소로 변환하는 역할을 한다.
* 호스트 이름(hostname)은 이런 호스트(host)에 부여된 이름(name)입니다. IP주소를 갖고 있는 '어떤 것'에 '이름(name)'을 부여한 것입니다. 이미 IP주소를 갖고 있는데 왜 이름을 더 부여할까요? IP주소는 사람이 일일이 기억하기 힘들기 때문에 기억하기 쉬운 이름을 부여하여 통신에 사용합니다.
* 단적으로 말하자면, 호스트 이름은 도메인 이름의 한 가지 특수한 유형입니다. 도메인 이름 중에서 IP주소를 설정할 수 있는 이름이 호스트 이름입니다. 호스트 이름은 도메인 이름의 유형 중 일부분입니다. 출처: https://dnssec.tistory.com/26 [DNS Lab.]

# Q Which IP address class has more host addresses available by default?
A. FIRST(A)
* Class란? 하나의 IP주소에서 네트워크 영역과 호스트 영역을 나누는 방법이자, 약속이다.
* IPv4주소는 네트워크의 크기나 호스트의 수에 따라 A, B, C, D, E 클래스로 나누어진다. A, B, C 클래스는 일반 사용자에게 부여하는 네트워크 구성용, D 클래스는 멀티캐스트용, E 클래스는 향후 사용을 위하여 예약된 주소이다.
* A class
  * A클래스는 하나의 네트워크가 가질 수 있는 호스트 수가 제일 많은 클래스이다. IP주소를 32자리 2진수로 표현했을때, 맨 앞자리 수가 항상 0 인 경우가 바로 A클래스이다. 즉 0xxx xxxx. xxxx xxxx. xxxx xxxx. xxxx xxxx 와 같이 되어있다. x 는 0 또는 1. 이 범위를 10진수로 표현하면 0.0.0.0 ~ 127.255.255.255 이다.
  * 그런데 A클래스에서 네트워트 주소는 1.0.0.0 ~ 126.0.0.0 까지로 규정되어있다. 약속이다. 그래서 IP주소 중 1부터 126으로 시작하는 네트워크는 A클래스라고 생각하면 된다.
  * 그리고 호스트 주소가 가질 수 있는 갯수는 (2^24) - 2개 이다. (-2 이유는 모두가 1인경우 브로드캐스트 주소로 사용하고 모두 0인 경우엔 네트워크 주소로 사용하기 때문)
  * 그리고 호스트 주소가 가질 수 있는 갯수는 (2^24) - 2개 이다. (-2 이유는 모두가 1인경우 브로드캐스트 주소로 사용하고 모두 0인 경우엔 네트워크 주소로 사용하기 때문)
![image](https://user-images.githubusercontent.com/52701529/119637498-adf35a80-be50-11eb-86cc-2941951a4c60.png)

# Q Which of the following propositions is not true?
A. UDP does not support broadcasting(X)
 * TCP와 구별되는 UDP의 특징. 
* 오답
* UDP is faster, simpler and more efficient than TCP
 * UDP는 비연결지향적. + 최소한의 오류만 검출 -> TCP에 비해 속도가 빠르다.
 * https://namu.wiki/w/UDP 활용되는 분야: 스트리밍 분야나 온라인 게임의 서버-클라이언트 통신에 대부분 UDP가 사용된다. 데이터가 빠짐없이 전송되는 것보다 빠른 응답속도가 중요하기 때문이다.
* UDP only has the basic error control mechanism
 * UDP 헤더의 CheckSum 필드를 통해 최소한의 오류만 검출한다. (신뢰성이 낮다)
 * 애초에 실시간 스트리밍 서비스 같은 분야에서 TCP의 신뢰성 중심의 통신 방법이 걸림돌이 되어 UDP가 제시된 것이다. 
* UDP is a datagram oriented protocol -> UDP는 데이터를 데이터그램 단위로 처리하는 프로토콜이다. 
* TCP/UDP? 전송계층에서 사용되는 프로토콜. 전송계층은 IP에 의해 전달되는 패킷의 오류를 검사하고 재전송 요구 등의 제어를 담당하는 계층이다.
* TCP(연결지향형 프로토콜) vs UDP(비연결지향형 프로토콜)
* Checksum: network를 통해 패킷을 송/수신하는 중에 헤더나 데이터가 손상되지 않았다는 것을 보증하기 위해 사용된다.
* Broadcasting: 한 개체가 특정 네트워크에 속한 모든 개체에게 데이터를 보내는 모델을 브로캐스팅이라 한다. 브로드캐스팅은 송신자가 보낸 데이터 하나를 다수의 수신자가 받는 방식이다. 송신자가 보내는 메시지는 모든 개체에게 전달되고, 각 개체는 이 메시지가 브로드캐스트 주소로 보낸 것임을 확인하고 읽어들인다.
