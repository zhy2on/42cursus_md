# NetWhat
## Which of the following is private IP address?
* 사설 ip주소를 고르는 문제이다.
* IP란? internet protocol. 인터넷에 연결되어 있는 각 장치들을 고유하게 식별할 수 있는 식별번호.
* ip주소에는 ipv4, ipv6 두 가지 버전이 있으며, 유동 아이피(DHCP) vs 고정 아이피 또는 공인 아이피 vs 사설 아이피로 나눌 수 있다.
* 사설 아이피의 대역: 10.0.0.0 – 10.255.255.255 / 172.16.0.0 – 172.31.255.255 / 192.168.0.0 – 192.168.255.255

## To test the IP stack on your local host, which IP address would you ping?
* 로컬 호스트의 ip를 묻는 문제이다.
* 거의 모든 컴퓨터환경에서 자기 자신을 접근하는(loopback 이라고 한다고 함) 경우가 잦다.
* 그리하여 OS 자체적으로 제공하고 , 항상 고정되어 있는 IP(127.0.0.1) 과 호스트네임(localhost)을 갖는다.
* 127.0.0.1은 예약된 IP 주소로 인터넷상에 일반 IP로는 쓰일 수 없는 주소이다.
* OS에서 가상으로 지원하며, 랜카드 등 디바이스 자체를 통과하지 않고 소프트웨어적으로 처리된다.

## Which of the following is the valid host range for the subnet on which the IP address 158.137.223.21/29 resides?
* 해당하는 host ip range를 구하는 문제이다.
* subnetmask란? 네트워크 영역을 분리시켜 주는 것. 0으로 된 부분에서 IP를 나눠쓰는 혹은 IP를 쪼개는 개념이다.
* 256 / 2^(subnetmask에서 끝 8자리의 1채워진 부분 구하기) = 분할할 범위
* 분할한 범위에서 처음 시작은 네트워크 어드레스, 마지막이 브로드캐스트 어드레스.
* 호스트범위 표: http://www.ymsys.co.kr/snet.php

## If an Ethernet port on a router were assigned an IP address of 104.69.192.245/23, which host address would be able to communicate with it?
* 위 방법대로 호스트 범위 구하고, 그 안에 해당하는 주소를 고르면 된다.

## What is the Network address of a host with an IP address of 141.225.245.17/12?
* 위 방법대로 서브넷마스크를 통한 범위 구하고, 맨 처음 범위인 값이 네트워크 어드레스이다.

## Which protocol does Ping use?
* Ping이란? 네트워크 상태를 체크할 때 쓰이는 ICMP중 하나이다.
* ICMP란? ICMP는 TCP/IP에서 IP 패킷을 처리할 때 발생되는 문제를 알려주는 프로토콜이다.
* 그냥 정의 되어 있는 개념. 외워야 한다.
* https://biggerdata.tistory.com/41

## Which of this is not a class of IP address?
* IPv4는 네트워크를 더욱 효율적으로 분배하기 위해 네트워크를 클래스별로 나누는데, A,B,C,D,E 총 5개의 클래스로 나누어져 있다.

## What is the maximum number of IP addresses that can be assigned to hosts on a local subnet that uses the 255.255.255.224 subnet mask?
* 32비트 중 뒤에 0 개수만큼을 2^ 계산 하고 -2.
* 224 -> 11111000 2^5 - 2 = 30

## The ____________ translates internet domain and host names to IP address
* 사람이 일일이 ip 주소를 외워 다닐 수 없기 때문에, 도메인 이름을 사용하게 되는데, 이와 같이 도메인 네임과 호스트 네임을 다시 ip 주소로 바꿔주는 시스템이 도메인 네임 시스템이다.

## How long is an IPv6 address?
* IPv4의 표현범위가 너무 작아(32bits) 더 확장 시킨 것이 IPv6(128bits)

## You have an interface on a router with the IP address of 56.211.104.158/20. Including the router interface, how many hosts can have IP addresses on the LAN attached to the router interface?
* 2^(32 - subnetmask) - 2
* 2^(32 - 12) - 2 = 4094

## Which of the following is the valid host range for the subnet on which the IP address 252.178.236.78/23 resides?
* 앞에서 구한 방법대로 구하면 된다.

## Which of this is not true?
  * TCP is a datagram-oriented protocol(X) -> connection-oriented
  * TCP is comparatively slower than UDP(O) -> TCP는 연결지향적. 신뢰성을 중시한다. UDP는 비연결지향적. 속도를 중시한다.
  * TCP doesn't supports Broadcasting(O) -> TCP는 무조건 1:1 연결. 브로드캐스팅은 1:N 연결로 UDP가 지원한다.
  * TCP provides extensive error checking mechanisms. It is because it provides flow control and acknowledgment of data(O)
  -> TCP는 checksum 외에도, sequence number, acknowledge number 등을 이용해 흐름에 관련한 오류도 검출한다. https://mr-zero.tistory.com/36
  * Sequencing of data is a feature of TCP (this means that packets arrive in-order at the receiver)(O) -> TCP는 흐름제어가 가능하다.
  sequence number, acknowledge number등을 통해 데이터 이동 흐름을 파악한다.
  * TCP is reliable as it guarantees delivery of data to the destination router(O) -> TCP는 신뢰성! 라우터로의 데이터 전송을 보장한다.
  
## You want to implement a mechanism that automates the IP configuration, including IP address, subnet mask, default gateway, and DNS information. Which protocol will you use to accomplish this?
* DHCP란? ip주소를 동적으로 할당해주는 프로토콜.
* ip주소에 고정 아이피와 동적 아이피가 있다고 했는데, 동적 아이피가 DHCP와 관련 된 것.

## Which protocol does DHCP use at the Transport layer?
* DHCP
* UDP : 
* ARP : 네트워크 상에서 IP 주소를 물리적 네트워크 주소로 대응(bind)시키기 위해 사용되는 프로토콜



