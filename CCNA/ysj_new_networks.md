> 목적: 이전에 작성했던 네트워크 개념 총집합. 큰 구조에서 설명, 구체적으론 따로 찾아볼 수 있으므로... 한 토요일까진 이거 할 듯?

> (찾아봤을 때) 실제 작동되고 있는 것들만 설명한다. 이전의 지식인 경우 크게 설명하지 않거나 이전임을 설명하고 넘어간다.

# TCP/IP와 실제 컴퓨터의 동작 넒게 알아보기

대충 실제 동작 확인할거면 OSI 보다는 TCP/IP에 집중하라는 내용

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

# Physical Layer

OSI 7계층 중 1계층. 이산적 디지털 데이터(0/1)를 연속적 물리 매체(전기·빛·전파)로 변환해 전송하는 규약을 정의한다.

상위 계층(Data Link)에서 내려온 비트 스트림을 물리 신호로 인코딩하고, 수신 측에서 복원 가능하도록 전기적·기계적·절차적 표준을 규정한다.

L1은 "비트를 어떻게 신호로 바꿔 매체에 실을 것인가"만 다룬다.    
단, 실제 NIC에서는 L2의 MAC 블록과 L1의 PHY 블록이 붙어서 동작하므로 경계가 깔끔하게 보이지 않을 수 있다.

- **MAC**: 이더넷 프레임, MAC 주소 필터링, FCS/CRC, 송수신 큐 같은 L2 동작을 담당
- **PHY**: MAC에서 받은 비트/심볼을 전기·빛·전파 신호로 바꾸고, 반대로 매체에서 들어온 신호를 다시 복원
- 둘은 MII/GMII/RGMII/SGMII 같은 내부 인터페이스로 연결되며, 실제 칩에서는 하나로 통합되거나 NIC + SFP 트랜시버처럼 나뉘기도 한다.

## 역할

- **전달(Transmission)**: 비트를 전기 신호 / 광 펄스 / 전자기파로 변환
- **매체(Medium)**: 구리선, 광섬유, 자유공간(free space, 무선)
- **표준(Standard)**: 양 끝단이 동일하게 해석할 수 있는 규격 정의 (전압 레벨, 주파수, 커넥터 핀 배치, 타이밍 등)

## 표준의 성격

상위 프로토콜과 달리 주소·라우팅·재전송 같은 논리적 동작이 없다. 기계(커넥터·케이블), 전기(전압·타이밍), 기능(핀 역할), 절차(전송 순서) 규격만 정의한다.

대표 제정 기관: IEEE, ITU-T, TIA/EIA.

## 구성 요소

### 하드웨어

- **커넥터**: RJ45 (정확히는 [8P8C](https://www.reddit.com/r/networking/comments/105p3aj/confusion_between_rj45_connector_8p8c_connector)), LC/SC (광), SMA (RF)
- **케이블**
  - 꼬임쌍선 (UTP/STP): Cat5e, Cat6, Cat6a — 전자기 간섭 상쇄 목적으로 꼬임
  - 동축 케이블
  - 광섬유: 싱글모드 / 멀티모드
- **송수신기**: NIC, SFP/SFP+ 트랜시버, 안테나

### 통신 규약

- **라인 코딩 (Line Coding)**: 비트를 신호 파형에 매핑하는 방식 — Manchester / 8B/10B / 64B/66B / PAM4
- **변조 (Modulation)**: 반송파에 정보를 실어 보내는 방식 — ASK / FSK / PSK / QAM / OFDM
- **무선·링크 표준**
  - WiFi
  - Bluetooth
  - 5G NR
  - Ethernet (IEEE 802.3)

## 참고하면 좋을 자료

- [예전에 내가 정리했던 문서](https://github.com/YangSiJun528/B-major-study/blob/main/CCNA/section_10/ysj/note.md)
- [Making Software — Sending and Receiving Data](https://www.makingsoftware.com/chapters/sending-and-receiving-data): 비트가 실제 신호로 변환되는 과정을 시각적인 자료로 설명
- [Ben Eater — Networking Fundamentals (13부작)](https://youtube.com/playlist?list=PLowKtXNTBypH19whXTVoG3oKSuOcw_XeW&si=sDEyz93fSUIuPF37): 4번째 영상에 실제 기계 신호를 뜯어서 해석함.
- 한 권으로 읽는 컴퓨터 구조와 프로그래밍 - 2장
전자 회로의 조합 논리: 세계는 연속적인데, 어떻게 이산적인 컴퓨터각 존재할 수 있는가? 왜 2진수인가? 등의 개념 설명
- [위키피디아 - IEEE 802.1Q 설명](https://en.wikipedia.org/wiki/IEEE_802.1Q): 프레임 형식 확인용 링크. 

# Data Link Layer

물리 계층이 전달한 비트 스트림을 **프레임(frame)** 단위로 묶고, 동일한 로컬 네트워크(같은 링크/세그먼트) 내에서 인접 노드 간 전달을 담당한다.

L2는 "같은 네트워크 안에서 이 프레임을 누구에게 보낼 것인가"를 다룬다. (L1과 마찬가지로 하드웨어 구현이 묶여있어 L1,L2의 구분이 실제론 모호하다.)   

## 역할

- **프레이밍(Framing)**: 비트 스트림에 시작/끝 경계를 부여해 프레임으로 묶음
- **주소 지정(Addressing)**: MAC 주소로 동일 링크 상의 송수신자 식별
- **오류 검출(Error Detection)**: CRC(FCS)로 전송 중 비트 오류 탐지 — 손상 프레임은 폐기, 복구는 상위 계층(TCP) 소관
- **매체 접근 제어(MAC)**: 공유 매체에서 누가 언제 전송할지 조정
  - CSMA/CD: 고전 이더넷(half-duplex, hub 기반)에서 사용 — 현대 switched full-duplex 환경에서는 사실상 사용 안 함
  - CSMA/CA: WiFi(802.11)에서 현재도 사용

## 스위치의 프레임 전달 방식

- **MAC Learning**: 스위치가 프레임의 출발지 MAC과 들어온 포트를 MAC 주소 테이블에 기록
- **Forwarding**: 목적지 MAC의 포트를 알고 있으면 해당 포트로만 프레임 전달
- **Flooding**: 목적지 포트를 모르거나 여러 장비가 받아야 하는 프레임을 같은 VLAN 안의 다른 포트로 전달
  - **Broadcast flooding**: 목적지 MAC이 `FF:FF:FF:FF:FF:FF`인 경우. ARP 요청이 대표적
  - **Unknown unicast flooding**: 특정 목적지 MAC이 있지만, 스위치가 아직 해당 MAC의 포트를 모르는 경우
  - **Multicast flooding**: 멀티캐스트 제어가 없으면 멀티캐스트도 여러 포트로 퍼질 수 있음

## 구성 요소

### 장비와 커널 컴포넌트

- **NIC (Network Interface Controller/Card)**: OS에 네트워크 인터페이스로 노출되는 하드웨어. MAC 주소 보유, 프레임 송수신, FCS/CRC 계산/검증, MAC 필터링, 송수신 큐 처리를 담당
- **NIC 드라이버**: 커널에서 NIC를 제어하는 소프트웨어. 장비 설정, interrupt/polling, RX/TX queue 관리를 담당한다.
- **PHY / 트랜시버**: MAC이 만든 비트 흐름을 실제 매체의 신호로 바꾸는 부분. 구리선 PHY, 광 SFP/SFP+ 트랜시버, 무선 RF 회로 등이 여기에 해당
- **스위치(Switch)**: MAC 주소 테이블 기반으로 프레임을 해당 포트로만 전달. 현대 LAN의 기본 장비 — VLAN, STP 등도 스위치에서 동작
  - IEEE 표준상으로는 "bridge"로 분류 (802.1D). 즉 스위치는 **멀티포트 브리지** (기존 브리지는 더 이상 안씀)
  - 가상화 환경에서는 소프트웨어 브리지로 구현됨 (Linux bridge, Docker `docker0`, 하이퍼바이저 vSwitch)

### NIC의 핵심 동작

NIC는 L2 기능(MAC 필터링, 프레이밍, CRC)을 하드웨어로 수행하며, 호스트와는 DMA로 프레임을 주고받는다. **어떤 프레임을 OS로 올릴지 1차 필터링**하고 **CPU 부하를 분산하는 큐 관리자** 역할을 한다.

(DMA 메커니즘 자체는 다른 장치와 동일하다. 다만 비동기적 입력과 병렬 처리, 낮은 지연, 필터링 등 특수한 요구사항이 필요하다.)

**프레임 필터링**
- 기본: 목적지 MAC이 자기 자신 / 브로드캐스트 / 가입한 멀티캐스트인 프레임만 OS로 전달
- **Promiscuous mode**: 모든 프레임을 OS로 전달. 패킷 캡처, 브리지, 가상 스위치에서 사용

**RX/TX Ring**
- 수신/송신 프레임을 담는 원형 큐 (호스트 메모리, NIC가 DMA로 접근)
- 여러 ring = 여러 CPU 코어가 병렬 처리 가능 — **큐와 CPU 분산의 단위**

**RSS (Receive Side Scaling)**
- 수신 프레임을 flow 단위(IP·포트 해시)로 여러 RX ring에 분산
- **같은 flow는 같은 ring**: 패킷 re-ordering으로 인한 TCP 성능 저하 방지
- **다른 flow는 다른 ring**: 멀티코어 병렬 처리

**가상화 지원**
현대 NIC는 가상화 환경을 위한 기능을 제공한다 — VM/컨테이너용 가상 인터페이스(**VNIC**), NIC를 하드웨어적으로 분할해 VM에 직접 할당하는 **SR-IOV** 등. 물리 NIC가 이를 지원할수록 OS/하이퍼바이저의 소프트웨어 처리 부담이 줄어든다.

## L2 실제 통신 흐름

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
5. 목적지 MAC이 없거나 브로드캐스트이면, 같은 VLAN 안의 다른 포트로 flood 한다.
6. 목적지 NIC는 자기 MAC, 브로드캐스트, 가입한 멀티캐스트에 해당하는 프레임만 OS로 올린다.

L2 스위칭 흐름: **MAC 학습 -> 선택적 전달 -> 모르면 같은 VLAN 안에서 flood**

서로 다른 VLAN/IP 서브넷 사이의 통신은 L3 역할의 스위치/라우터가 필요.

## Switch 관리 (CCNA 관점)

CCNA는 네트워크 인프라 관리까지 다루므로, 스위치를 **설정하고 관측에 필요한 기능도 배운다**. 이때 스위치 관리는 라우팅을 설정하는 일이 아니라, L2 전달 범위와 장애 가능성을 관리하는 쪽에 가깝다.

- **MAC Table**: 프레임을 어느 포트로 보낼지 결정 — [section_11](section_11/ysj/note.md)
- **VLAN / Access / Trunk**: 브로드캐스트/flood 범위 분리 — [section_21](section_21/ysj/note.md)
- **STP**: L2 루프와 브로드캐스트 스톰 방지 — [section_24](section_24/ysj/note.md)
- **LACP**: 여러 물리 링크를 하나의 논리 링크로 묶음 — [section_26](section_26/ysj/note.md)
- **관리 IP / LLDP / Interface Counter / 보안 키워드**: 인프라 관측과 액세스 제어 — [section_14](section_14/ysj/note.md), [section_27](section_27/ysj/note.md)

### 프레임 구조

여기선 설명 안함. 잘 설명하는 외부 자료 많음.

![https://www.makingsoftware.com/chapters/sending-and-receiving-data](https://www.makingsoftware.com/_next/image?url=%2Fnetworking-and-the-web%2Fsending-and-receiving-data%2Fethernet-frame.png&w=3840&q=75)

### 주소 체계 (MAC)

이거 개념 설명이 있긴 해야하는거 아님?

- 48비트, 일반적으로 NIC에 기본 MAC 주소가 할당됨 (OUI 24비트 + 벤더 할당 24비트)
    - OS/가상화 환경에서 변경하거나 별도 가상 MAC을 쓸 수 있음
- 로컬 링크에서만 유효
    - 로컬 링크 (Local Link): 라우터를 거치지 않고 L2로 직접 닿을 수 있는 범위. 하나의 브로드캐스트 도메인
    - 라우터(L3)를 넘을 때 목적지 MAC은 다음 홉(hop)의 MAC으로 재작성됨. 출발지 MAC도 라우터 자신의 것으로 바뀜
    - 그래서 같은 VLAN/브로드캐스트 도메인 안에서만 고유하면 됨.
- 특수 주소
  - Broadcast: `FF:FF:FF:FF:FF:FF`
  - IPv4 Multicast: `01:00:5E:xx:xx:xx`
  - IPv6 Multicast: `33:33:xx:xx:xx:xx`
  - STP: `01:80:C2:00:00:00`

### 주요 표준 / 프로토콜

**표준 (규격 — 주로 IEEE 802 계열)**
- **IEEE 802.3 (Ethernet)**: 유선 LAN의 프레임 형식, MAC 동작, 매체 규격
- **IEEE 802.11 (WiFi)**: 무선 LAN — MAC 계층은 CSMA/CA 사용
- **IEEE 802.1Q (VLAN)**: 프레임 태깅으로 논리적 네트워크 분할

**프로토콜 (동작 규약)**
- **PPP (Point-to-Point Protocol)**: 두 노드 간 직접 연결 링크용 (RFC 1661)
- **ARP (Address Resolution Protocol)**: IP ↔ MAC 주소 매핑 (RFC 826, 엄밀히는 L2.5)
- **STP (Spanning Tree Protocol, IEEE 802.1D)**: 스위치 루프 방지
- **LACP (Link Aggregation, IEEE 802.3ad/802.1AX)**: 여러 물리 링크를 하나로 묶음. EtherChannel 구성에 사용

## 참고하면 좋을 자료

- [Making Software — Sending and Receiving Data](https://www.makingsoftware.com/chapters/sending-and-receiving-data): 이더넷 프레임 시각적인 설명
- [Ben Eater — Networking Fundamentals (13부작)](https://youtube.com/playlist?list=PLowKtXNTBypH19whXTVoG3oKSuOcw_XeW&si=sDEyz93fSUIuPF37): 5~7번 영상
- [KTword — PHY 설명](http://www.ktword.co.kr/test/view/view.php?no=2786): PHY 칩과 MAC의 경계
- [Triton — Virtualizing NICs](https://tritondatacenter.com/blog/virtualizing-nics): NIC 동작 방식 및 가상화 설명
- [이더넷 프레임 정보](https://en.wikipedia.org/wiki/Ethernet_frame)
- 내가 정리한 관련 섹션: [스위치 기본](section_11/ysj/note.md), [스위치 관리 기초](section_14/ysj/note.md), [VLAN](section_21/ysj/note.md), [STP](section_24/ysj/note.md), [LACP](section_26/ysj/note.md), [스위치 보안](section_27/ysj/note.md)


# 스위치 레벨까지의 동작 (L3)

## 프로토콜

(아래 개념이랑 묶어서 봐야 이해 가능)

## IP

# OS 커널의 동작 (L4)

(아래 개념이랑 묶어서 봐야 이해 가능)

## TCP/IP

## UDP

# 라우터의 동작 (L4)

(아래 개념이랑 묶어서 봐야 이해 가능)

## 라우터가 하는 일

## ??

# 이제 큰 그림을 보자 (인프라 레벨)

# 네트워크 프로그래밍 소개

## 네트워크 프로그래밍과 네트워크

# 응용계층 레벨의 동작

# Everything is File

## 디바이스와 네트워크 동신은 파일로 추상화된다.

## 다만 예외도 있다.

# 소켓 통신을 해보자

# Proxy란?

# 응용 프로그래밍 개발
