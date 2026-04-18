> 목적: 이전에 작성했던 네트워크 개념 총집합. 큰 구조에서 설명, 구체적으론 따로 찾아볼 수 있으므로... 한 토요일까진 이거 할 듯?

> (찾아봤을 때) 실제 작동되고 있는 것들만 설명한다. 이전의 지식인 경우 크게 설명하지 않거나 이전임을 설명하고 넘어간다.

# TCP/IP와 실제 컴퓨터의 동작 넓게 알아보기

대충 실제 동작 확인할거면 OSI 보다는 TCP/IP에 집중하라는 내용.

OSI 모델은 실제 장비를 한 계층으로 고정해서 분류하기보다, 네트워크 기능과 프로토콜을 나눠 보는 개념 모델에 가깝다. 실제 통신에서는 상위 데이터가 하위 프로토콜에 계속 감싸인다. 예를 들어 HTTP 메시지는 TCP segment 안에, TCP는 IP packet 안에, IP는 Ethernet frame 안에 들어간다. 이걸 **encapsulation**이라고 부른다.

https://www.youtube.com/watch?v=k1gyh9BlOT8&list=PLXvgR_grOs1BFH-TuqFsfHqbh-gpMbFoy&index=1

```
               OSI 7 Layers                TCP/IP Model
        +--------------------------+    +------------------+
        | L7  Application          |    |                  |
        +--------------------------+    |                  |
        | L6  Presentation         |    |   Application    |
        +--------------------------+    |                  |
        | L5  Session              |    |                  |
        +--------------------------+    +------------------+
        | L4  Transport            |    |   Transport      |
        +--------------------------+    +------------------+
        | L3  Network              |    |   Internet       |
        +--------------------------+    +------------------+
        | L2  Data Link            |    |                  |
        +--------------------------+    |      Link        |
        | L1  Physical             |    |                  |
        +--------------------------+    +------------------+
```

크게 어떤 식으로 동작하는지에 대한 개념(물론 예외도 있지만)

```
       ^             +----------------------------------+
       |             |             Process              |
       |             |        +----------------+        |
       |             |        |    Socket      |        |
       |             +--------+  (file I/O)    |--------+
       | User                 +----------------+
       | --------------------------------------------------
       | Kernel      +----------------------------------+
       |             |               TCP                |
       |             +----------------------------------+
       |             |                IP                |
       |             +----------------------------------+
  S/W  |
       |             +----------------------------------+
       |             |              Driver              |
       v ------------+----------------------------------+--
          H/W
                     +----------------------------------+
                     |               NIC                |
                     |    (Network Interface Card)      |
                     +----------------------------------+
```

# Part 1. 네트워크 인프라 레벨

## Physical Layer

OSI 7계층 중 1계층. 이산적 디지털 데이터(0/1)를 연속적 물리 매체(전기·빛·전파)로 변환해 전송하는 규약을 정의한다.

상위 계층(Data Link)에서 내려온 비트 스트림을 물리 신호로 인코딩하고, 수신 측에서 복원 가능하도록 전기적·기계적·절차적 표준을 규정한다.

L1은 "비트를 어떻게 신호로 바꿔 매체에 실을 것인가"만 다룬다.    
단, 실제 NIC에서는 L2의 MAC 블록과 L1의 PHY 블록이 붙어서 동작하므로 경계가 깔끔하게 보이지 않을 수 있다.

- **MAC**: 이더넷 프레임, MAC 주소 필터링, FCS/CRC, 송수신 큐 같은 L2 동작을 담당
- **PHY**: MAC에서 받은 비트/심볼을 전기·빛·전파 신호로 바꾸고, 반대로 매체에서 들어온 신호를 다시 복원
- 둘은 MII/GMII/RGMII/SGMII 같은 내부 인터페이스로 연결되며, 실제 칩에서는 하나로 통합되거나 NIC + SFP 트랜시버처럼 나뉘기도 한다.

### 역할

- **전달(Transmission)**: 비트를 전기 신호 / 광 펄스 / 전자기파로 변환
- **매체(Medium)**: 구리선, 광섬유, 자유공간(free space, 무선)
- **표준(Standard)**: 양 끝단이 동일하게 해석할 수 있는 규격 정의 (전압 레벨, 주파수, 커넥터 핀 배치, 타이밍 등)

### 표준의 성격

상위 프로토콜과 달리 주소·라우팅·재전송 같은 논리적 동작이 없다. 기계(커넥터·케이블), 전기(전압·타이밍), 기능(핀 역할), 절차(전송 순서) 규격만 정의한다.

대표 제정 기관: IEEE, ITU-T, TIA/EIA.

### 구성 요소

#### 하드웨어

- **커넥터**: RJ45 (정확히는 [8P8C](https://www.reddit.com/r/networking/comments/105p3aj/confusion_between_rj45_connector_8p8c_connector)), LC/SC (광), SMA (RF)
- **케이블**
  - 꼬임쌍선 (UTP/STP): Cat5e, Cat6, Cat6a — 전자기 간섭 상쇄 목적으로 꼬임
  - 동축 케이블
  - 광섬유: 싱글모드 / 멀티모드
- **송수신기**: NIC, SFP/SFP+ 트랜시버, 안테나

#### 통신 규약

- **라인 코딩 (Line Coding)**: 비트를 신호 파형에 매핑하는 방식 — Manchester / 8B/10B / 64B/66B / PAM4
- **변조 (Modulation)**: 반송파에 정보를 실어 보내는 방식 — ASK / FSK / PSK / QAM / OFDM
- **무선·링크 표준**
  - WiFi
  - Bluetooth
  - 5G NR
  - Ethernet (IEEE 802.3)

### 참고하면 좋을 자료

- [예전에 내가 정리했던 문서](https://github.com/YangSiJun528/B-major-study/blob/main/CCNA/section_10/ysj/note.md)
- [Making Software — Sending and Receiving Data](https://www.makingsoftware.com/chapters/sending-and-receiving-data): 비트가 실제 신호로 변환되는 과정을 시각적인 자료로 설명
- [Ben Eater — Networking Fundamentals (13부작)](https://youtube.com/playlist?list=PLowKtXNTBypH19whXTVoG3oKSuOcw_XeW&si=sDEyz93fSUIuPF37): 4번째 영상에 실제 기계 신호를 뜯어서 해석함.
- 한 권으로 읽는 컴퓨터 구조와 프로그래밍 - 2장
전자 회로의 조합 논리: 세계는 연속적인데, 어떻게 이산적인 컴퓨터가 존재할 수 있는가? 왜 2진수인가? 등의 개념 설명
- [위키피디아 - IEEE 802.1Q 설명](https://en.wikipedia.org/wiki/IEEE_802.1Q): 프레임 형식 확인용 링크. 

## Data Link Layer

물리 계층이 전달한 비트 스트림을 **프레임(frame)** 단위로 묶고, 동일한 로컬 네트워크(같은 링크/세그먼트) 내에서 인접 노드 간 전달을 담당한다.

L2는 "같은 네트워크 안에서 이 프레임을 누구에게 보낼 것인가"를 다룬다. (L1과 마찬가지로 하드웨어 구현이 묶여있어 L1,L2의 구분이 실제론 모호하다.)   

### 역할

- **프레이밍(Framing)**: 비트 스트림에 시작/끝 경계를 부여해 프레임으로 묶음
- **주소 지정(Addressing)**: MAC 주소로 동일 링크 상의 송수신자 식별
- **오류 검출(Error Detection)**: CRC(FCS)로 전송 중 비트 오류 탐지 — 손상 프레임은 폐기, 복구는 상위 계층(TCP) 소관
- **매체 접근 제어(MAC)**: 공유 매체에서 누가 언제 전송할지 조정
  - CSMA/CD: 고전 이더넷(half-duplex, hub 기반)에서 사용 — 현대 switched full-duplex 환경에서는 사실상 사용 안 함
  - CSMA/CA: WiFi(802.11)에서 현재도 사용

### 스위치의 프레임 전달 방식

- **MAC Learning**: 스위치가 프레임의 출발지 MAC과 들어온 포트를 MAC 주소 테이블에 기록
- **Forwarding**: 목적지 MAC의 포트를 알고 있으면 해당 포트로만 프레임 전달
- **Flooding**: 목적지 포트를 모르거나 여러 장비가 받아야 하는 프레임을 같은 L2 브로드캐스트 도메인 안의 다른 포트로 전달
  - **Broadcast flooding**: 목적지 MAC이 `FF:FF:FF:FF:FF:FF`인 경우. ARP 요청이 대표적
  - **Unknown unicast flooding**: 특정 목적지 MAC이 있지만, 스위치가 아직 해당 MAC의 포트를 모르는 경우
  - **Multicast flooding**: 멀티캐스트 제어가 없으면 멀티캐스트도 여러 포트로 퍼질 수 있음

### 구성 요소

#### 장비

- **NIC (Network Interface Controller/Card)**: MAC 주소 보유, 프레임 송수신, FCS/CRC 계산/검증, MAC 필터링 같은 L2 동작을 담당
- **PHY / 트랜시버**: MAC이 만든 비트 흐름을 실제 매체의 신호로 바꾸는 부분. 구리선 PHY, 광 SFP/SFP+ 트랜시버, 무선 RF 회로 등이 여기에 해당
- **스위치(Switch)**: MAC 주소 테이블 기반으로 프레임을 해당 포트로만 전달. 현대 LAN의 기본 장비 — VLAN, STP 등도 스위치에서 동작
  - IEEE 표준상으로는 "bridge"로 분류 (802.1D). 즉 스위치는 **멀티포트 브리지** (기존 브리지는 더 이상 안씀)
  - 가상화 환경에서는 소프트웨어 브리지로 구현됨 (Linux bridge, Docker `docker0`, 하이퍼바이저 vSwitch)

### L2 실제 통신 흐름

같은 L2 네트워크 안에서는 **프레임의 목적지 MAC 주소**를 보고 다음 포트를 정한다. 스위치는 라우터처럼 IP 서브넷 사이의 경로를 선택하지 않는다.

1. 호스트가 보낼 IP 패킷을 만든다.
   - 같은 서브넷이면 목적지 호스트의 MAC 주소로 보낸다.
   - 다른 서브넷이면 기본 게이트웨이의 MAC 주소로 보낸다.
   - 이 MAC 주소를 모르면 ARP 같은 방식으로 먼저 알아낸다.
2. NIC가 이더넷 프레임을 만든다.
   - 출발지 MAC: 자기 NIC의 MAC
   - 목적지 MAC: 목적지 호스트 또는 기본 게이트웨이의 MAC
3. 스위치는 프레임을 받은 포트와 출발지 MAC을 보고 **MAC 주소 테이블**을 학습한다.
4. 목적지 MAC이 테이블에 있으면 해당 포트로만 전달한다.
5. 목적지 MAC이 없거나 브로드캐스트이면, 같은 L2 브로드캐스트 도메인 안의 다른 포트로 flood 한다.
6. 목적지 NIC는 자기 MAC, 브로드캐스트, 가입한 멀티캐스트에 해당하는 프레임만 OS로 올린다.

L2 스위칭 흐름: **MAC 학습 -> 선택적 전달 -> 모르면 같은 L2 브로드캐스트 도메인 안에서 flood**

서로 다른 VLAN/IP 서브넷 사이의 통신은 L3 역할의 스위치/라우터가 필요.

### Switch 관리 (CCNA 관점)

L2 스위치는 IP 경로를 선택하지 않고, MAC/VLAN/STP 같은 정보로 같은 L2 영역 안의 프레임 흐름을 안정적으로 제한한다.   
그래서 CCNA에서 보는 스위치 관리는 전달 범위, 루프 방지, 장애 관측을 주로 다룬다.

- **MAC Table**: 프레임을 어느 포트로 보낼지 결정 — [section_11](section_11/ysj/note.md)
- **VLAN / Access / Trunk**: 브로드캐스트/flood 범위 분리 — [section_21](section_21/ysj/note.md)
- **STP**: L2 루프와 브로드캐스트 스톰 방지 — [section_24](section_24/ysj/note.md)
- **LACP**: 여러 물리 링크를 하나의 논리 링크로 묶음 — [section_26](section_26/ysj/note.md)
- **관리 IP / LLDP / Interface Counter / 보안 키워드**: 인프라 관측과 액세스 제어 — [section_14](section_14/ysj/note.md), [section_27](section_27/ysj/note.md)

#### 프레임 구조

여기선 설명 안함. 잘 설명하는 외부 자료 많음.

![https://www.makingsoftware.com/chapters/sending-and-receiving-data](https://www.makingsoftware.com/_next/image?url=%2Fnetworking-and-the-web%2Fsending-and-receiving-data%2Fethernet-frame.png&w=3840&q=75)

#### 주소 체계 (MAC)

- 48비트, 일반적으로 NIC에 기본 MAC 주소가 할당됨 (OUI 24비트 + 벤더 할당 24비트)
    - OS/가상화 환경에서 변경하거나 별도 가상 MAC을 쓸 수 있음
- 로컬 링크에서만 유효
    - 로컬 링크 (Local Link): 라우터를 거치지 않고 L2로 직접 닿을 수 있는 범위. 하나의 브로드캐스트 도메인
    - 라우터(L3)를 넘을 때 목적지 MAC은 다음 홉(hop)의 MAC으로 재작성됨. 출발지 MAC도 라우터 자신의 것으로 바뀜
    - 그래서 같은 L2 브로드캐스트 도메인 안에서만 고유하면 됨.
- 특수 주소
  - Broadcast: `FF:FF:FF:FF:FF:FF`
  - IPv4 Multicast: `01:00:5E:xx:xx:xx`
  - IPv6 Multicast: `33:33:xx:xx:xx:xx`
  - STP: `01:80:C2:00:00:00`

#### 주요 표준 / 프로토콜

**표준 (규격 — 주로 IEEE 802 계열)**
- **IEEE 802.3 (Ethernet)**: 유선 LAN의 프레임 형식, MAC 동작, 매체 규격
- **IEEE 802.11 (WiFi)**: 무선 LAN — MAC 계층은 CSMA/CA 사용
- **IEEE 802.1Q (VLAN)**: 프레임 태깅으로 논리적 네트워크 분할

**프로토콜 (동작 규약)**
- **PPP (Point-to-Point Protocol)**: 두 노드 간 직접 연결 링크용 (RFC 1661)
- **ARP (Address Resolution Protocol)**: IP ↔ MAC 주소 매핑 (RFC 826, 엄밀히는 L2.5)
- **STP (Spanning Tree Protocol, IEEE 802.1D)**: 스위치 루프 방지
- **LACP (Link Aggregation, IEEE 802.3ad/802.1AX)**: 여러 물리 링크를 하나로 묶음. EtherChannel 구성에 사용

### 참고하면 좋을 자료

- [Making Software — Sending and Receiving Data](https://www.makingsoftware.com/chapters/sending-and-receiving-data): 이더넷 프레임 시각적인 설명
- [Ben Eater — Networking Fundamentals (13부작)](https://youtube.com/playlist?list=PLowKtXNTBypH19whXTVoG3oKSuOcw_XeW&si=sDEyz93fSUIuPF37): 5~7번 영상
- [KTword — PHY 설명](http://www.ktword.co.kr/test/view/view.php?no=2786): PHY 칩과 MAC의 경계
- [Triton — Virtualizing NICs](https://tritondatacenter.com/blog/virtualizing-nics): NIC 동작 방식 및 가상화 설명
- [이더넷 프레임 정보](https://en.wikipedia.org/wiki/Ethernet_frame)
- 내가 정리한 관련 섹션: [스위치 기본](section_11/ysj/note.md), [스위치 관리 기초](section_14/ysj/note.md), [VLAN](section_21/ysj/note.md), [STP](section_24/ysj/note.md), [LACP](section_26/ysj/note.md), [스위치 보안](section_27/ysj/note.md)
- [DMA Controller: How Peripheral Devices Transfer Data to RAM](https://youtu.be/s8RGHggL7ws?si=nM924Xq_DHGcdGQb)

## Network Layer (L3)

인터넷은 하나의 거대한 L2 네트워크가 아니라, 여러 네트워크가 라우터로 연결된 구조다.

L3는 서로 다른 L2 네트워크/서브넷 사이에서 **IP 패킷을 다음 홉으로 넘기는 계층**이다. MAC 주소가 같은 로컬 네트워크 안에서만 의미 있다면, IP 주소는 네트워크를 넘어 목적지까지 가기 위한 논리 주소다.

### 역할

- **논리 주소 지정**: MAC이 로컬 링크 주소라면, IP는 네트워크 간 이동을 위한 논리 주소
- **라우팅/포워딩**: 목적지 IP prefix를 라우팅 테이블에서 찾아 다음 홉(next-hop) 또는 출력 인터페이스 선택
- **hop-by-hop 전달**: 라우터를 지날 때마다 L2 헤더(MAC)는 새로 만들어지고, L3의 출발지/목적지 IP는 보통 유지됨 
    - 라우터는 입력 링크의 L2 헤더를 벗기고 IP 패킷을 확인한 뒤, 다음 링크에 맞는 새 L2 헤더를 붙인다.
    - NAT(Network Address Translation), 터널링, 프록시 같은 예외는 있음
- **서브넷 경계**: 서로 다른 IP 서브넷/VLAN 사이 통신에는 라우터나 L3 스위치가 필요
  - VLAN 자체는 L2 분리이고, VLAN 간 통신은 L3 역할

대표 개념: **IP, ICMP, routing table, default gateway, CIDR, ARP/ND, TTL/Hop Limit**

### IP 프로토콜

L3의 중심은 **IP(Internet Protocol)**다. IP는 데이터를 **IP packet**으로 감싸고, 출발지/목적지 IP 주소를 기준으로 여러 네트워크를 지나갈 수 있게 한다.

- IP는 **best-effort / connectionless** 방식이다. 도착 보장, 순서 보장, 재전송은 TCP 같은 상위 계층이 맡는다.
  - **best-effort**: 가능한 만큼 전달을 시도하지만, 실패해도 IP 자체가 복구하지 않음
  - **connectionless**: 미리 연결을 맺지 않고, 각 packet이 독립적으로 전달됨
- IP header에는 출발지/목적지 IP, TTL/Hop Limit, 상위 프로토콜 정보(TCP/UDP/ICMP 등)가 들어간다.

### 호스트 입장에서 필요한 최소 설정

외부 네트워크와 통신하려면 보통 아래 정보가 필요하다. DNS는 L7으로, L3 자체는 아니지만, 실제 접속 문제를 볼 때 함께 확인한다.

- **IP address**: 내 인터페이스의 L3 주소
- **Prefix/Subnet mask**: 목적지가 같은 네트워크인지 판단하는 기준
- **Default gateway**: 로컬 밖으로 보낼 때 사용할 다음 홉 라우터
- **DNS server**: 도메인 이름을 IP 주소로 바꾸는 서버

이 값들은 수동 설정, DHCP, IPv6 RA/DHCPv6, VPN/컨테이너/클라우드 네트워크 설정 등으로 들어올 수 있다.

### L3 실제 통신 흐름

#### 같은 서브넷 안에서 통신

같은 서브넷이면 라우터를 거치지 않는다.

1. 호스트가 자신의 IP/prefix와 목적지 IP를 비교해 같은 서브넷인지 판단한다.
2. 목적지 MAC을 모르면 ARP(IPv4) 또는 ND(IPv6)로 MAC 주소를 찾는다.
3. NIC가 목적지 호스트 MAC을 넣어 이더넷 프레임을 만든다.
4. 스위치는 MAC 주소 테이블을 보고 같은 L2 네트워크(브로드캐스트 도메인) 안에서 프레임을 전달한다.

핵심: **IP 목적지는 같지만, 실제 링크에서는 목적지 호스트의 MAC으로 보낸다.**

#### 다른 서브넷/인터넷으로 통신

다른 서브넷이면 목적지 호스트에게 직접 프레임을 보낼 수 없고, 기본 게이트웨이로 보낸다.

1. 호스트 라우팅 테이블에서 목적지 IP에 맞는 경로를 찾는다.
   - 다른 서브넷이면 보통 `default route`의 다음 홉인 `default gateway`를 선택한다.
   - default gateway는 DHCP, 수동 설정, IPv6 RA, VPN/컨테이너/클라우드 네트워크 설정 등으로 라우팅 테이블에 등록된다.
2. 라우팅 테이블에서 찾은 다음 홉(default gateway)의 MAC을 ARP/ND로 알아낸다.
   - 이미 ARP/ND cache에 있으면 새로 묻지 않고 재사용한다.
3. NIC가 이더넷 프레임을 만든다.
   - L2 목적지 MAC: 기본 게이트웨이 MAC
   - L3 목적지 IP: 최종 목적지 IP
   - Ethernet frame의 payload로 IP packet이 들어간다. 즉 L2가 L3를 감싼다.
4. 라우터는 L2 헤더를 벗기고, IP 패킷의 목적지 주소를 확인한다.
5. 라우팅 테이블에서 가장 구체적인 prefix(Longest Prefix Match)를 찾는다.
6. TTL/Hop Limit을 줄이고, 다음 링크에 맞는 새 L2 프레임을 만들어 보낸다.
   - 이 값이 0이 되면 패킷을 폐기한다. 
   - 이 때, 가능하면 출발지 IP로 `ICMP Time Exceeded` 오류 메시지를 보낸다.
7. 이 과정이 라우터마다 반복되고, 마지막 라우터가 목적지 호스트 MAC으로 프레임을 보낸다.

요약: **IP는 end-to-end 목적지, MAC은 hop-by-hop 다음 링크 목적지**. 라우터는 IP packet은 보고 유지하되, 각 링크에 맞게 L2 frame은 새로 만든다.

### IP와 CIDR

IP 주소는 인터페이스에 붙는 L3 주소이고, prefix는 그 주소가 속한 네트워크 범위를 나타낸다.

- **Classful IP(A/B/C)**: 예전 IPv4 주소 분류 방식. 지금은 거의 사용하지 않고, CIDR 기반으로 주소 계획과 라우팅을 한다고 보면 됨
- **CIDR**: `192.168.10.0/24`처럼 네트워크 prefix 길이를 `/`로 표현
  - `/24`: 앞 24비트가 네트워크 영역, 나머지가 호스트 영역
  - 같은 prefix 안이면 직접 전달, 다른 prefix면 게이트웨이로 전달
  - prefix가 길수록 더 구체적인 경로
  - 예: `172.16.254.2`가 `172.16.0.0/16`과 `172.16.254.0/24`에 모두 매칭되면 `/24`가 선택됨
- **Subnetting**: 하나의 주소 범위를 여러 작은 네트워크로 나눔
  - VLAN/라우팅 경계와 함께 설계하면 브로드캐스트/flood 범위 축소
  - 주소 낭비 감소
  - 보안/관리 단위 분리
- **Route Aggregation**: 여러 작은 경로를 큰 prefix 하나로 요약해 라우팅 테이블을 줄임
- **Private IP + NAT(Network Address Translation)**: IPv4 운영에서 흔함. NAT는 IP 주소를 바꾸고, 보통 포트까지 같이 다루므로 L3/L4 경계에 걸친 실무 개념
    - (L4 부분에서 설명 예정)
- **IPv6**: 128비트 주소 체계. CIDR prefix를 계속 사용하고, ARP 대신 ND(Neighbor Discovery), default router 학습에는 RA/SLAAC/DHCPv6 같은 방식이 쓰임

### Routing

라우터나 L3 스위치는 프레임의 MAC이 아니라 **패킷의 목적지 IP**를 기준으로 다음 경로를 정한다. 이때 목적지 prefix와 다음 홉/출력 인터페이스를 담은 표를 routing table 또는 forwarding table이라고 볼 수 있다.

- **Connected Route**: 인터페이스에 IP를 설정하면 직접 연결된 네트워크 경로가 생김
- **Static Route**: 관리자가 직접 넣는 경로
- **Dynamic Routing**: 라우터끼리 경로를 교환해 자동으로 라우팅 테이블을 갱신
  - IGP: 조직 내부 라우팅(OSPF, IS-IS, RIP 등)
  - EGP: 조직 간 라우팅. 인터넷에서는 BGP
- **Default Route**: 모르는 목적지는 `0.0.0.0/0` 또는 `::/0` 방향으로 보냄
- **Longest Prefix Match**: 여러 경로가 맞으면 가장 구체적인 prefix를 선택

#### 대규모 인터넷 라우팅: AS, BGP, IXP

인터넷은 하나의 거대한 네트워크가 아니라, 독립적으로 운영되는 많은 네트워크가 연결된 구조다.   
통신사, 클라우드, 학교, 대형 기업처럼 자기 라우팅 정책을 가진 네트워크를 **AS(Autonomous System)**라고 하고, AS 사이의 경로 교환에는 보통 **BGP(Border Gateway Protocol)**를 사용한다.

- **BGP**: AS 사이 라우팅. 어느 prefix로 갈 수 있는지 이웃 AS와 교환
- **Routing Policy**: 최단 경로뿐 아니라 비용, 계약, 트래픽 제어 같은 운영 정책이 중요
- **Peering / Transit**: AS끼리 직접 교환하거나, 상위/대형 네트워크를 통해 다른 인터넷 경로로 나감
- **IXP(Internet Exchange Point)**: 여러 AS가 물리적으로 만나 peering을 만들 수 있는 교환 지점

즉 대규모 인터넷은 각 AS가 정책에 따라 경로를 주고받는 구조다. AS 간 상업적 관계에 기반한 전달 규칙(**Gao-Rexford 조건**) 덕분에 중앙 통제 없이도 안정적으로 동작한다.

통신사 내부망에서는 **MPLS(Multi-Protocol Label Switching)** 같은 label/tunnel 기반 전달을 쓰기도 한다.    
사용자 입장에서는 여전히 IP 통신이지만, 내부적으로 트래픽 제어·VPN·장애 우회 같은 **추가 기능을 붙이기 위한 레이어**에 가깝다.

### L3 인프라 관리 (CCNA 관점)

CCNA에서 L3를 보는 이유는 "패킷이 어디까지 가야 하고, 어디서 끊겼는지"를 판단하기 위해서다.   
장비 명령어보다 아래 키워드 중심으로 보면 된다.

- **IP 주소 계획 / CIDR**: 서브넷 크기, gateway 주소, 주소 낭비와 충돌 방지
- **Default Gateway / Routing Table**: 로컬 밖으로 나가는 방향 결정
- **Inter-VLAN Routing**: VLAN으로 나눈 L2 영역 사이를 L3에서 연결
- **Static/Dynamic Routing**: 작은 네트워크는 정적 경로, 규모가 커지면 동적 라우팅
- **Route Summary**: 라우팅 테이블과 변경 전파 범위 축소
- **Routing Loop / TTL**: 잘못된 경로로 패킷이 반복 순환하는 문제. TTL/Hop Limit이 0이 되면 폐기되어 무한 순환을 막음
- **ping / traceroute / ICMP**: ICMP는 IP 계층의 제어/오류 알림 프로토콜. ping은 ICMP Echo를 사용하고, traceroute는 TTL/Hop Limit과 `ICMP Time Exceeded` 응답을 이용해 중간 hop 확인

#### ICMP와 traceroute

ICMP는 IP 통신 중 발생한 상태/오류를 알려주는 L3 제어 프로토콜이다.   
TCP/UDP처럼 애플리케이션 데이터를 운반하기보다, 네트워크 상태를 확인하거나 오류를 알리는 데 쓰인다.

- **ping**: `ICMP Echo Request/Reply`로 목적지 IP까지 왕복 가능한지 확인
- **traceroute**: 테스트 패킷 자체는 UDP/ICMP/TCP일 수 있지만, 중간 hop 확인은 보통 라우터의 `ICMP Time Exceeded` 응답을 이용
- **Destination Unreachable**: 목적지 네트워크/호스트/포트 등에 도달할 수 없을 때 받는 오류 응답
- traceroute에서 `* * *`가 보이면 응답이 없다는 뜻. ICMP 차단, rate limit, 장비 정책일 수 있으므로 바로 장애라고 단정하지 않음

### 참고하면 좋을 자료

- 내가 정리한 관련 섹션: [L3 기본과 subnet](section_06/ysj/note.md), [IP class 개념](section_07/ysj/note.md), [CIDR/subnetting/VLSM](section_08/ysj/note.md), [라우터/스위치 기본](section_11/ysj/note.md), [장비 관리 기초](section_14/ysj/note.md), [Routing/BGP 개요](section_17/ysj/note.md), [ping/traceroute](section_18/ysj/note.md), [동적 라우팅 프로토콜](section_19/ysj/note.md), [OSPF](section_20/ysj/note.md), [Inter-VLAN Routing](section_22/ysj/note.md), [IPv6](section_30/ysj/note.md)
- [Making Software — How the internet works](https://www.makingsoftware.com/chapters/how-the-internet-works): OSI, IP routing, ARP, encapsulation을 그림으로 설명
- [Cloudflare — BGP란?](https://www.cloudflare.com/ko-kr/learning/security/glossary/what-is-bgp/): AS, BGP peering, BGP 속성 개요
- [AWS — BGP란 무엇인가?](https://aws.amazon.com/ko/what-is/border-gateway-protocol/): eBGP/iBGP, 경로 어그리게이션, 확장성 설명
- 책: `How the Internet Really Works` — 4장의 AS, BGP, peering/transit, IXP 설명

## 인프라 관점의 전체 통신 흐름

실제 통신에는 DNS, TCP/UDP, TLS, HTTP, NAT/firewall 같은 L3 밖의 요소도 함께 등장하지만, 여기서는 이를 제외하고 네트워크 인프라가 IP packet을 목적지 방향으로 보내는 흐름만 본다.

1. 호스트는 목적지 IP가 같은 subnet인지 확인한다.
   - 같으면 목적지 호스트의 MAC을 찾는다.
   - 다르면 default gateway의 MAC을 찾는다.
2. MAC 주소를 모르면 ARP(IPv4) 또는 ND(IPv6)로 같은 L2 영역에 물어본다.
3. NIC는 IP packet을 Ethernet/WiFi 같은 L2 frame에 담고, L1 신호로 매체에 보낸다.
4. 스위치는 MAC table을 보고 같은 VLAN/L2 영역 안에서 frame을 전달한다.
   - 목적지 MAC을 모르면 같은 L2 영역 안에서 flood 할 수 있다.
5. 라우터/L3 스위치는 L2 header를 벗기고 IP 목적지를 확인한다.
6. Routing table에서 가장 구체적인 prefix를 찾고, 다음 hop 방향으로 새 L2 frame을 만들어 보낸다.
   - 라우터를 지날 때마다 MAC은 바뀌지만, 목적지 IP는 보통 유지된다.
   - TTL/Hop Limit은 줄어들고, 0이 되면 packet은 폐기된다.
7. 통신사/클라우드 같은 대규모망에서는 AS 간 BGP 정책, IXP, MPLS 같은 내부 전달 방식이 경로 선택과 운용에 영향을 준다.
8. 마지막 L3 장비가 목적지 subnet에 도달하면 목적지 호스트의 MAC으로 frame을 보내고, 목적지 NIC가 이를 OS로 올린다.

- 요약
  - Layer
    - L1은 신호
    - L2는 같은 링크/VLAN 안의 frame 전달
    - L3는 IP 기준의 네트워크 간 전달
  - MAC과 IP
    - IP: end-to-end
    - MAC 주소: hop-by-hop

# Part 2. OS / 커널 레벨

## NIC 드라이버와 네트워크 I/O

### NIC의 핵심 동작

NIC는 L2 기능(MAC 필터링, 프레이밍, CRC)을 하드웨어로 수행한다. 네트워크 장치에서 중요한 부분은 **어떤 프레임을 OS로 올릴지 1차 필터링**하고 **큐 단위로 CPU 부하를 분산**하는 점이다.

**프레임 필터링**
- 기본: 목적지 MAC이 자기 자신 / 브로드캐스트 / 가입한 멀티캐스트인 프레임만 OS로 전달
- **Promiscuous mode**: 모든 프레임을 OS로 전달. 패킷 캡처, 브리지, 가상 스위치에서 사용

**RX/TX Ring**
- 수신/송신 프레임을 담는 호스트 메모리의 원형 큐
- 여러 ring = 여러 CPU 코어가 병렬 처리 가능 — **큐와 CPU 분산의 단위**

**RSS (Receive Side Scaling)**
- 수신 프레임을 flow 단위(IP·포트 해시)로 여러 RX ring에 분산
- **같은 flow는 같은 ring**: 패킷 re-ordering으로 인한 TCP 성능 저하 방지
- **다른 flow는 다른 ring**: 멀티코어 병렬 처리

**가상화 지원**
현대 NIC는 가상화 환경을 위한 기능을 제공한다.

VM/컨테이너용 가상 인터페이스(**VNIC**), NIC를 하드웨어적으로 분할해 VM에 직접 할당하는 **SR-IOV** 등.   
물리 NIC가 이를 지원할수록 OS/하이퍼바이저의 소프트웨어 처리 부담이 줄어든다.

## Transport Layer (L4)

## TCP

## UDP

# Part 3. 유저 레벨

## 네트워크 프로그래밍 소개

### 네트워크 프로그래밍과 네트워크

## 응용계층 레벨의 동작

## Everything is File

### 디바이스와 네트워크 통신은 파일로 추상화된다.

### 다만 예외도 있다.

## 소켓 통신을 해보자

## Proxy란?

## 응용 프로그래밍 개발

# Part 4. 경계가 애매한 현대 네트워크

## QUIC

## Linux 기반 미니 PC를 라우터로 만드는 방법

Docker, VM, Android hotspot, 홈 라우터는 겉모습은 달라도 내부적으로는 비슷한 방식으로 동작한다. 
L2로 내부 네트워크를 묶고, L3에서 forwarding/routing을 켜고, 필요하면 NAT와 firewall을 붙인다.

- **Linux bridge**: 컨테이너/VM/무선 AP 쪽 인터페이스를 같은 L2 네트워크로 묶음
- **network namespace**: 컨테이너처럼 독립된 인터페이스, IP, 라우팅 테이블을 가진 공간
- **veth pair**: namespace와 host를 잇는 가상 케이블
- **IP forwarding + routing table**: host가 내부망과 외부망 사이에서 L3 라우터처럼 패킷 전달
- **NAT/firewall**: 내부 주소를 외부로 내보내고, 들어오고 나가는 트래픽을 제어

**인상깊은 의견**
- 리눅스를 라우터로 만드는 일이 특수한 마법이 아니라, Docker/VM NAT 네트워크나 Android hotspot에서 이미 쓰는 Linux 커널 네트워킹 기능을 직접 조립해 보는 것
  - Docker나 VM에서 NAT routing을 써봤다면 이것과 같은 일을 한 것
- 소비자용 “router”라는 이름이 혼란을 만든다. 실제로는 NAT gateway, DHCP server, DNS cache, WiFi AP, firewall 등이 한 박스에 묶인 것.
  - 이런 기능들을 OSI 계층으로 구분하면 대부분 L1~L7까지 전체 범위를 포함하고 있음.

## 참고하면 좋을 자료

- [How to turn anything into a router](https://nbailey.ca/post/router/): Linux 장비가 router/firewall/NAT/DHCP/AP 조합으로 동작하는 예시
- [Hacker News discussion](https://news.ycombinator.com/item?id=47574034): 위 글에 대한 실무적인 보충 논의
- [리눅스의 네트워크 네임스페이스](https://gornoba.github.io/devops/kubernetes/networking/network-namespaces): network namespace, veth, bridge, routing/NAT 예시
