# CCNA yangsjun 통합 문서

> 원본: `CCNA/section_*/ysj/*.md` 파일을 섹션 번호와 파일명 순서로 병합했습니다.


---

> Source: `section_03/ysj/note.md`

## Section 03 정리

#### OSI Model
> 네트워크 프로토콜의 상호 작용 방식을 이해하는데 도움을 주는 개념적 프레임워크 

(개념적 = 실제가 아님)   

[관련해서 정리했던 글](https://github.com/YangSiJun528/memory/blob/master/notes/Computer%20Science/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC%20%EA%B8%B0%EC%B4%88%20%EA%B0%9C%EB%85%90.md)

#### 내트워크 개요

- Node(노트북, 프린터)
- 이더넷 케이블: 유선 통신
- 스위치: 많은 포트
- 무선 액세스 포인트 (= 공유기)
- 인터넷 (=외부 연결 시 사용)
- 라우터: 인터넷 간 통신, 여러 포트 타입 지원 = 여러 종류의 네트워크 접근 가능, 보안을 위한 방화벽
- Local Area Network: 라우터를 넘어가지 않는 범위?
- Wide Area Network: 특정 라우터 간의 전용 연결?

- 네트워크 핵심: 엔드 호스트 간의 연결

- 네트워크 핵심
    - 토폴로지: 장치가 어떤 식으로 연결되었는가?
    - 속도
    - 비용
    - 보안
    - 가용성(Availability): 항상 사용 가능한 상태
    - 확장성(Scalability)
    - 신뢰성(Relaibility): 계속 작동


#### OSI 모델 개요

- 7 layer로 네트워크 통신 분리
- ISO에 속한 표준
- 위,아래 계층끼리 상호작용
- 각 level에서 내려갈 때 Encapsulation(상위 정보 + 본인 level의 정보), 올라갈 때 Decapsulation
- (각 layer 별 설명 생략)
- ![](https://storage.googleapis.com/blogs-images-new/ciscoblogs/1/osi-768x593.gif)
    - [출처](https://blogs.cisco.com/cloud/an-osi-model-for-cloud), 강의에 포함된건 아닌데, layer 별 설명으론 충분해 보임
- OSI 모델은 여전히 네트워크 문제를 해결하는 데 유용하다. (의사소통, 관심사 분리, 네트워크 이해)

#### TCP/IP Suite
여기서 Suite는 Set 보다는 더 격식있는 표현 정도라고 함.

OSI와 같은 Model이 아니라 실제로 사용되는 프로토콜 스택, 집합 정도로 해석할 수 있음.

이전에는 TCP/IP 외에 다른 스택도 있었으나 사라짐.

OSI 계층을 사용하긴 하지만, 더 적게 4(어떤 곳에서는 5)개 정도만 가짐.

![](https://www.cisco.com/c/dam/en/us/support/docs/ip/routing-information-protocol-rip/13769-5-01.gif)
[출처](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13769-5.html)

###### 주요 용어
- 계층 별 통신 시 사용하는 데이터의 이름
    - Data
    - Segemt
    - Packet
    - Frame
- PDU(Protocol Data Unit)
    - OSI의 1~7 계층까지의 전체 통신
    - 두 호스트 간의 통신 시 PDU 프로토콜 데이터 단위를 교환한다.
- 일상적으론 명확히 데이터의 이름을 구분하지는 않고, PDU를 포함해 Packet이라고 부르기도 함.


#### OSI 상위 계층

5~7 계층이 해당

(설명 생략 - 나중에 참고할때는 cisco 공식문서 설명 참고하기)

#### OSI 하위 계층

4~1 계층이 해당

(설명 생략 - 나중에 참고할때는 cisco 공식문서 설명 참고하기)

## 느낀점

책 읽는것보다는 정보가 적을듯. 

여기 섹션이 30분정도 쓰는데, 대본으로 하면 좀 큰 개발서적 기준으로 10페이지 안으로 끝날거 같은 분랑임.

"OSI는 개념적이고 TCP/IP는 실질적인 프로토콜 집합이다." 이 개념을 몰라서 계속 삽질하고 착각했었는데, 이 강의에서는 이름부터 확실하게 구분짓고 명확하게 설명하는게 좋았다.

위에 예전에 삽질하면서 정리했던 노트 링크가 있음. 강의 내용이랑 겹치는게 많은데, 한 번 보면 좋을듯.



---

> Source: `section_04/ysj/note.md`

## Section 04 정리

#### Cisco OS (IOS)
Cisco의 여러 기기에 사용되는 OS는 IOS OS이다.

- Cisco OS 역사
    - 라우터만 파는 회사로 시작
    - 라우터에 IOS OS를 사용함.
    - 스위치 파는 회사 인수.
    - 기존 스위치에 있는 CatOS 대신 IOS 사용
    - 방화벽도 마찬가지로 IOS로 대체
    - Cisco는 거의 모든 기기에서 IOS를 사용함.
        - 일부 최신 라우터, 스위치를 제외한
        - 그러나 IOS와 비슷한 명령어를 제공함.

- IOS 특징 
    - 모놀리식 커널임.
    - 따라서 프로세스 하나가 충돌하면 전체 라우터가 충돌함.
    - 앞서 말한 다른 OS는 마이크로 커널을 사용해서 프로세스 충돌이 다른 시스템에 영향을 주지 않음.
    - 그럼에도 IOS는 여러 Cisco 기기에 쓰이는 만큼, 신뢰 가능하고 견고한 OS임.

#### 네트워크로 Cisco 장치 연결

강의에서 사용하는 Cisco Packet Tracer 소프트웨어는 네트워크 환경을 시뮬레이션하는 도구로, 실제 라우터나 스위치 조작이 아님.

주로 업무를 하면, 네트워크를 통해 원격으로 접근하여 관리함.

SSH를 사용함. (암호화되어 Telnet보다 안전함.)    
SSH 외에 추가로 중앙 집중식 AAA 서버가 있을 수 있음.    
AAA: 인증(Authentification), 인가(Authorization), 계정(Accounting)

(실제로 어떻게 PuTTY 소프트웨어를 사용해서 접속하는지 강의에서 보여줌.)

Production Network: 일반 직원 트래픽에서 사용되는 네트워크

Management Netowrk: 관리 전용 네트워크 - 백업, 관리 면에서 사용

#### Cisco 장치로 초기 연결

초기 연결은 물리적으로 이루어져야 함.
- IP 주소를 포함한 기본 설정이 전혀 되어있지 않기 때문.
- 그 외 유선 연결 사용 이유: 네트워크 연결이 불가능한 상태인 경우, 콘솔 연결을 통해서 어디가 문제인지 알 수 있음.



물리적 장치에 초기 연결을 하는 방법
- IP 아래의 하위 레벨(이더넷?)으로 연결해서 명령 수행
- 커넥터
    - DB9 to RJ45(LAN 커넥터랑 비슷하게 생김)을 사용해서 연결 가능
    - DB9를 노트북에 꼽는데, 요즘에는 지원 안함. 그래서 확장 어댑처를 사용해야 함.
    - 최근에는 Mini USB to USB 케이블을 지원하기도 함.
- PuTTY에서 Serial 연결 유형을 사용해서 연결 가능
- 연결이 완료된 이후에는 CLI 창에서 초기 설정을 하면 됨.

#### Cisco IOS 운영 체제 탐색 파트 1,2

(Cisco IOS에서 사용하는 여러 명령어에 대한 설명. 따로 Perplexity 사용해서 요약본으로 적고, 강의 내용은 생략함.)


#### Cisco IOS 구성 관리

구성은 기기가 사용하는 설정을 이야기 함.

IOS가 시작되면 시작 구성으로부터 관리자 구성을 불러옴.

- 실행중인(running) 구성
    - 변경사항이 바뀌면 그 바뀐 정보가 실행중인 구성으로 즉시 전송이 됨.
    - 실행중인 구성은 RAM에 저장됨. 휘발성.
    
- 시작 구성
    - 다시 시작되야만 적용되는 구성.
    - 실행중인 구성과 별개로 따로 설정해줘야 함.
    - 재시작 시, 시작 구성을 기준으로 설정됨.
    - 시작 구성은 NVRAM에 저장되므로 비휘발성

만약 라우터의 이름을 바꾼다면, 실행중인 구성만 바뀌고, 시작 구성은 바뀌지 않아서, 재시작하면 다시 돌아옴. runinng 구성을 시작 구성에 copy 명령어를 사용해 적용해줘야 함.

구성을 백업(따로 저장)해서 나중에 덮어씌우거나 할 수 있음.

파일을 기기 내부 대신 외부에 저장하는게 안전함. TFTP 서버가 가장 간단한 방법.

## 후기

- [GPT 한테 물어본 모놀리식, 마이크로 커널](https://chatgpt.com/share/6703e562-0bcc-8009-aa29-17ddff8c058b)

## 실습

실습 자료는 보고, 강의에서 이야기한 거 정리한거 직접 다뤄보는게 끝.

![](section_04/ysj/img1.png)

이 옵션 눌러서 Text 읽어주는 기능 꺼야함.


---

> Source: `section_04/ysj/ref_sec_20.md`

## 한국어 버전

### IOS 명령어 계층 구조

| 모드 | 프롬프트 | 설명 |
|------|----------|------|
| 사용자 실행 | `hostname>` | 기본 사용자 모드 |
| 특권 실행 | `hostname#` | 관리자 모드 ('Enable') |
| 전역 구성 | `hostname(config)#` | 전역 구성 모드 ('Configure Terminal') |
| 인터페이스 구성 | `hostname(config-if)#` | 인터페이스 구성 모드 ('Interface (x)') |

- `Exit`: 한 단계 아래로 내려갑니다.
- `End`: 어느 레벨에서든 특권 실행 모드로 돌아갑니다.

### 명령어 축약

- 명령어의 축약된 버전을 입력할 수 있습니다.
- 예: 'enable' 대신 'en'
- 입력한 내용에 대해 가능한 일치 항목이 하나만 있어야 축약이 성공합니다.

### 상황별 도움말

- 물음표(?)를 입력하여 도움말에 액세스할 수 있습니다.
- `sh?`: 'sh'로 시작하는 모든 명령어 표시
- `show ?`: 'show' 명령어에 사용 가능한 모든 키워드 옵션 표시
- `show ip ?`: 'show ip' 명령어에 사용 가능한 모든 키워드 옵션 표시

### 커서 이동

- Backspace: 이전 문자 삭제
- 화살표 키 (< 및 >): 커서를 좌우로 한 문자씩 이동
- Ctrl-A: 커서를 줄의 시작으로 이동
- Ctrl-U: 전체 줄 삭제

### 명령어 기록

- 위아래 화살표 (^ 및 v): 동일한 계층에서 이전에 입력한 명령어를 순환합니다.

### 명령어 출력 표시

- Enter: 'show' 명령어 출력을 한 줄씩 스크롤하여 표시
- Spacebar: 페이지 단위로 표시
- Ctrl-C: 'show' 명령어 출력을 중단하고 명령 프롬프트로 돌아감

### 파이프 명령어 예시

```
show running-config interface FastEthernet0/0
show running-config | begin FastEthernet0/0
show running-config | include FastEthernet0/0
show running-config | exclude FastEthernet0/0
show running-config | section interface
```

## English Version

### IOS Command Hierarchy

| Mode | Prompt | Description |
|------|--------|-------------|
| User Exec | `hostname>` | Basic user mode |
| Privileged Exec | `hostname#` | Administrator mode ('Enable') |
| Global Configuration | `hostname(config)#` | Global configuration mode ('Configure Terminal') |
| Interface Configuration | `hostname(config-if)#` | Interface configuration mode ('Interface (x)') |

- `Exit`: Drops back down one level
- `End`: Returns to Privileged Exec mode from any level

### Command Abbreviation

- You can enter an abbreviated version of a command
- Example: 'en' instead of 'enable'
- Abbreviation succeeds only if there's one possible match for what you typed

### Context Sensitive Help

- Enter a question mark to access Help
- `sh?`: Shows all commands that begin with 'sh'
- `show ?`: Shows all available keyword options for the 'show' command
- `show ip ?`: Shows all available keyword options for the 'show ip' command

### Moving the Cursor

- Backspace: Deletes the previous character
- Arrow keys (< and >): Moves the cursor left and right one character at a time
- Ctrl-A: Moves the cursor to the beginning of the line
- Ctrl-U: Deletes the whole line

### Command History

- Up and down arrows (^ and v): Cycles through previously entered commands at the same level in the hierarchy

### Showing Command Output

- Enter: Shows 'show' command output line by line
- Spacebar: Shows output page by page
- Ctrl-C: Breaks out of the show command output and returns to the command prompt

### Piped Command Examples

```
show running-config interface FastEthernet0/0
show running-config | begin FastEthernet0/0
show running-config | include FastEthernet0/0
show running-config | exclude FastEthernet0/0
show running-config | section interface
```


---

> Source: `section_04/ysj/ref_sec_24.md`

# IOS Operating System - Lab Exercises

## English Version

### Exploring User Exec Mode and CLI Command Help

- Notice you are in User Exec mode as indicated by the ‘Router>’ prompt.
- Enter a question mark to explore available commands.

```bash
Router> ?
Exec commands:
  <1-99>  Session number to resume
  connect  Open a terminal connection
  disable  Turn off privileged commands
  disconnect  Disconnect an existing network connection
  enable  Turn on privileged commands
  exit  Exit from the EXEC
  logout  Exit from the EXEC
  ping  Send echo messages
  resume  Resume an active network connection
  show  Show running system information
  ssh  Open a secure shell client connection
  telnet  Open a telnet connection
  terminal  Set terminal line parameters
  traceroute  Trace route to destination
```

- Limited commands are available in User Exec mode. For example, `show run` needs Privileged Exec mode.

```bash
Router> show run
% Invalid input detected at '^' marker.
```

### Viewing Additional Output

- To scroll through additional output, use the Space Bar.

```bash
--More—
```

- You can also check possible options for the `show aaa` command:

```bash
Router# sh aaa ?
local      Show AAA local method options
sessions   Show AAA sessions as seen by AAA Session MIB
user       Show users active in AAA subsystem
```

### Configuration Management

- To drop back to Privilege Exec mode:

```bash
R1(config-if)# end
R1#
```

- View configurations:

```bash
R1# show running-config
Building configuration...
Current configuration : 737 bytes
!
hostname R1
!
Output truncated --
```

- Change the hostname and save configurations:

```bash
R1# config t
R1(config)# hostname RouterX
RouterX(config)#
RouterX# copy run start
Building configuration...
[OK]
```

### Available Show Commands

- To see available show commands, enter:

```bash
Router# sh ?
aaa                        Show AAA values
access-lists              List access lists
arp                       Arp table
...
```

## Korean Version

### 사용자 실행 모드 및 CLI 명령 도움말 탐색하기

- ‘Router>’ 프롬프트에 의해 사용자 실행 모드에 있음을 알 수 있습니다.
- 사용 가능한 명령을 탐색하려면 물음표를 입력합니다.

```bash
Router> ?
Exec commands:
  <1-99>  세션 번호 계속하기
  connect  터미널 연결 열기
  disable  특권 명령 끄기
  disconnect  기존 네트워크 연결 끊기
  enable  특권 명령 켜기
  exit  EXEC 종료
  logout  EXEC 종료
  ping  에코 메시지 보내기
  resume  활성 네트워크 연결 계속하기
  show  실행 중인 시스템 정보 보기
  ssh  보안 셸 클라이언트 연결 열기
  telnet  텔넷 연결 열기
  terminal  터미널 라인 매개변수 설정하기
  traceroute  목적지로의 경로 추적하기
```

- 사용자 실행 모드에서는 제한된 명령만 사용할 수 있습니다. 예를 들어, `show run`은 특권 실행 모드가 필요합니다.

```bash
Router> show run
% 잘못된 입력이 '^' 표시 위치에서 감지되었습니다.
```

### 추가 출력 보기

- 추가 출력을 스크롤하려면 Space Bar를 사용합니다.

```bash
--더 많은 내용--
```

- `show aaa` 명령에 대한 가능한 옵션도 확인할 수 있습니다:

```bash
Router# sh aaa ?
local      AAA 로컬 메서드 옵션 보기
sessions   AAA 세션 보기
user       AAA 서브시스템에서 활성 사용자의 보기
```

### 구성 관리

- 특권 실행 모드로 돌아가려면 다음을 입력합니다:

```bash
R1(config-if)# end
R1#
```

- 구성을 보기:

```bash
R1# show running-config
구성 작성 중...
현재 구성 : 737 바이트
!
hostname R1
!
출력이 잘림 --
```

- 호스트 이름을 변경하고 구성을 저장합니다:

```bash
R1# config t
R1(config)# hostname RouterX
RouterX(config)#
RouterX# copy run start
구성 작성 중...
[OK]
```

### 사용 가능한 show 명령

- 사용 가능한 show 명령을 보려면 입력합니다:

```bash
Router# sh ?
aaa                        AAA 값 보기
access-lists              액세스 목록 표시
arp                       ARP 테이블
...
```

---

> Source: `section_05/ysj/note.md`

## Section 05 정리

#### OSI Model - Layer 4 Transfer Layer

- Host 간의 데이터를 전송하는 역할
- 세션 다중화(Session Multiplexing) 지원
    - Host가 여러 Session을 지원하고, 단일 링크(두 호스트 간의 네트워크 연결)에서 개별 트래픽 흐름을 관리
    - Post를 사용해서 같은 Host더라도 여러 Session을 가지고, 어떤 어플리케이션에 사용되는 트래픽인지 식별할 수 있음.

- 트래픽을 주고받는 과정
    - Sender의 Port와 Host의 Port가 연결됨.
    - 각 Port로만 주고 받음.
    - Sender Port가 15000이고 Receiver Port가 80로 연결을 맺으면 해당 포트로만 통신.
        - 어디로부터 온 요청인 지 식별 가능.
            - Stateful 방화벽의 동작 원리.   

#### TCP, UDP

- TCP
    - 순서가 보장된 데이터 전송: 발신자는 순서 번호를 포함하여 데이터 전송, 수신자는 해당 번호를 확인하여 올바른 순서로 트래픽 조립.
    - 세그먼트 누락 여부: 누락된 세그먼트를 확인하여 발신자에게 알릴 수 있음. (응답을 받은경우 수취 알림을 보내고, 누락이 생기면 보내지 않는 방식)
    - 흐름 제어: 수신 Host가 데이터를 전부 처리할 수 있도록 발신자의 데이터 흐름 조정
    - 연결 기반: TCP 3-Way Handshake를 통한 연결과 4-Way Handshake를 통한 해제
    - 헤더를 보면 꽤 많은 내용이 있음. (20 Byte) 각 내용과 역할은 [링크](https://networklessons.com/cisco/ccie-routing-switching-written/tcp-header) 참고 
    - (혼잡 제어도 있는데, 여기선 설명 안함.)

- UDP
    - best effort 방식 사용
        - 발신자가 패킷을 구성해서 수신자에게 보내기만 하고, 따로 응답 확인을 하지 않음.
    - 발신/수신자 사이의 아무 연결이 없음.
    - 따라서 신뢰할 수 없음.
        - 흐름 제어, 세그먼트 누락, 순서 제어 지원하지 않음.
    - 신뢰성을 보장하려면 더 상위 계층에서 이루어져야 함.
    - 헤더를 보면 출발지, 목적지 포트, 체크섬, 데이터만 포함함. (8 Byte)
        - 따라서 간접 비용(오버헤드)가 적게 듬.
- 언제 사용하는가?
    - TCP: 신뢰성이 중요한 경우
    - UDP: 지연에 민감한 실시한 트래픽
    - 꼭 하나만 사용하지는 않고, 두 방식을 함꼐 사용하는 어플리케이션도 있다. (e.g. DNS)


## 후기

- [널널한 개발자 TV - TCP 연결이라는 착각에 대해](https://youtu.be/DC9FfKSgisg?si=fuJ0XrQ1-3vrt4sm)를 시간되면 보면 좋을듯.
    - 설명 잘해줌. 좀 어그로 같은 제목이긴 한데...
    - `연결 != 보안성`이라는 의미
    - 간단 정리
        - TCP 연결은 segment 단위의 3-way handshake로 이루어짐.
        - 서로의 정보을 주고 받는 것. (syn, MSS, 혼잡제어 정책 등...)
            - 신뢰성 있는 데이터 송수신을 가능하게 하는데 필요한 정보들
        - 연결 이후 각 커널에 상대방의 정보를 저장(TCB)하고, 사용함.
        - 위 과정에서 보안성을 지켜주는게 없음. TCP Session hijacking 같은 문제가 발생할 수 있다.

---

> Source: `section_06/ysj/note.md`

## Section 06 정리

#### OSI Model - Layer 3 Network Layer

패킷을 네트워크 상의 목적지로 라우팅하는 역할.

라우터가 네트워크 층에서 동작.

서비스 품질 담당 역할: 더 나은 수준의 서비스를 필요로하는 트래픽을 우선 처리

논리적 주소 지정 체계인 IP 주소를 사용함.

#### IP Protocol

3계층의 가장 유명한 프로토콜. (이외에는 ICMP, IPSec)

Connectionless Protocol이므로 응답을 받을 수 없음.

IPv4와 IPv6를 사용함.
- 둘은 다른 버전이고, 다른 헤더 형식을 가짐. (상호 호환성 X)
- [IPv4](https://www.geeksforgeeks.org/introduction-and-ipv4-datagram-header/), [IPv6](https://www.geeksforgeeks.org/internet-protocol-version-6-ipv6-header/)
- 다른 버전도 있었는데, 거의 사용 안함.
- 각 헤더의 역할은 위에 링크한거 참고.

#### Unicast, Broadcast, Multicast Traffic

IP 네트워크를 통해 전송되는 트래픽 유형.

유형 별로 스위치에서 어떻게 각 Host에 트래픽을 전달하는지가 다름.

- Unicast: 
    - 유효한 단일 Host로 전송
- Broadcast: 
    - 스위치에 연결된 모든 Host로 이동함.
    - Host의 요청 여부와 무관하게 모든 곳으로 전송.
- Multicast: 
    - 하나의 사본을 여러 목적지로 전송함.
    - Unicast 여러 번 보내는 것보다 효율적임. (1MB 데이터를 한 번만 받고, 사본을 여러 번 보내면 효율적. 대신 목표 Host(n명이라 가정) 만큼 여러번 보내면 nMB의 트래픽이 필요함.)
    - 수신자가 어떤 유형의 데이터가 필요한지 일종의 등록을 한다. (IPTV 채널 or 라디오 방송의 주파수 같은 느낌. 실제로 재네가 Multicast를 쓴다는건 아님.)

#### 2진수 계산법, IPv4 Format - 강의에 있는데 아니까 생략

#### Subnet Network

하나의 큰 네트워크를 여러 작은 서브넷 네트워크로 나눔.

이를 통해 관리적 용의, 트래픽의 범위 제한을 통한 성능 향상 등의 이점을 가짐.

#### Subnet Mask

Host는 목적지의 IP 주소를 자신의 IP 주소 + 서브넷 마스크를 비교함으로써, 목적지가 같은 서브넷 상에 있는지 알 수 있다.

이를 통해 로컬 라우터(기본 게이트웨이)를 통해서 전송할지, 아닌지가 결정됨.

Host의 IP 주소는 Network Portion(영역)과 Host Portion으로 구분되며, 그것을 결정짓는 것이 Subnet Mask이다.

255.255.255.0 와 같이 연속된 1이후 연속된 0이 나오는 형식을 띄는데, 2진수로 1의 경우 Network Portion, 0의 경우 Host Portion이라고 볼 수 있다.

이렇게 길게 작성하지 않고, Host의 IP 뒤에 1의 개수를 사용하는 슬래쉬 표기법을 사용해 `192.168.10.15/24` (`/24`가 subnet mask) 같이 작성하기도 한다.

Host의 IP로 할당할 수 없는 주소가 있는데, subnet의 최솟값과 최대값이다. 최소값은 네트워크 주소, 최대값은 브로드케스트 주소 역할을 한다.

## 셜명 보완 - AI 피셜

##### 서브넷 내 통신

같은 서브넷 내의 장치들은 직접 통신할 수 있습니다[1].

- **ARP 프로토콜 사용**: 목적지 IP 주소를 MAC 주소로 변환합니다.
- **스위치를 통한 전송**: 데이터는 라우터를 거치지 않고 스위치를 통해 직접 전달됩니다.

##### 서브넷 간 통신

다른 서브넷에 있는 장치와 통신할 때는 라우터를 통해 이루어집니다[1].

- **게이트웨이 사용**: 패킷은 먼저 기본 게이트웨이(라우터)로 전송됩니다.
- **라우팅 테이블 참조**: 라우터는 목적지 IP 주소를 확인하고 적절한 경로로 패킷을 전달합니다.

##### 서브넷 마스크의 역할

서브넷 마스크는 IP 주소를 네트워크 부분과 호스트 부분으로 구분하는 데 사용됩니다[1].

- **예시**: IP 주소가 192.168.1.100이고 서브넷 마스크가 255.255.255.0인 경우
  - 네트워크 주소: 192.168.1.0
  - 호스트 주소: 0.0.0.100

##### CIDR 표기법

서브넷은 CIDR(Classless Inter-Domain Routing) 표기법으로 표현할 수 있습니다[1].

- **형식**: IP주소/서브넷 마스크의 1비트 수
- **예**: 192.168.1.0/24는 192.168.1.0 네트워크에 24비트 서브넷 마스크를 사용함을 의미합니다.

##### 서브넷의 이점

1. **네트워크 성능 향상**: 트래픽을 분산시켜 네트워크 혼잡을 줄입니다[1].
2. **보안 강화**: 서브넷 간 접근 제어를 통해 보안을 강화할 수 있습니다.
3. **효율적인 주소 관리**: 큰 네트워크를 작은 단위로 나누어 관리할 수 있습니다.

서브넷은 네트워크 관리와 효율성 향상에 중요한 역할을 합니다. 같은 서브넷 내의 장치들은 직접 통신이 가능하며, 다른 서브넷과의 통신은 라우터를 통해 이루어집니다. 이를 통해 네트워크 트래픽을 효율적으로 관리하고 보안을 강화할 수 있습니다.

Citations:
[1] https://www.cloudflare.com/ko-kr/learning/network-layer/what-is-a-subnet/
[2] https://velog.io/@sangmin1998/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%84%9C%EB%B8%8C%EB%84%B7Subnet-%EA%B0%9C%EB%85%90
[3] https://brunch.co.kr/%40growthminder/104
[4] https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/configure-subnets.html
[5] https://velog.io/@honggom/%EC%84%9C%EB%B8%8C%EB%84%B7-%EA%B2%8C%EC%9D%B4%ED%8A%B8%EC%9B%A8%EC%9D%B4

## 후기

IPv4, IPv6가 그냥 형식 차이인줄 알았는데, 다른 버전의 프로토콜이였음. 


---

> Source: `section_07/ysj/note.md`

## Section 07 정리

#### IP 주소 클래스
![](https://www.cisco.com/c/dam/en/us/support/docs/ip/routing-information-protocol-rip/13788-3-00.png)

Network Address Classes는 최초에 설계된 IPv4의 동작 방식이다.

- 역사적 배경
    - IPv4는 현재처럼 인터넷이 거대해질지 몰랐을 때 만들어졌고, 지금과 같은 확장성을 고려하지 않았다. 이런 역사적 배경을 이해하는 것이 중요하다.
    - 대부분의 기업 네트워크에선 NAT(Network Address Translation)와 Private Address를 사용하여 해결하고 있다.
    - 장기적으로는 높은 확장성을 가지는 IPv6가 이 자리를 대체할 것이다.


- 네트워크 영역, 호스트 영역은 클래스로 결정된다. A,B,C 클래스는 고정 된 서브넷 마스크 값을 가진다. D, E는 뒤에서 추가로 다룬다.
- IPv4에서, 전체 영역(4개의 octat)은 한정되어 있다.
    - 네트워크 영역이 줄어들면 호스트 영역이 늘어난다. 즉, 네트워크 영역으로 표현 가능한 네트워크 개수가 줄어들지만. 표현 가능한 호스트 영역은 늘어난다.
- 클래스는 A,B,C,D,E 클래스로 나뉜다.
    - A가 가장 네트워크(호스트) 영역 넒은 범위, C가 가장 작은 범위를 가진다.
    - D, E 클래스는 일반적인 Host의 IP 할당이 아닌 다른 목적으로 사용된다. (이 글 아래에서 추가로 설명)
    - 클래스 별 자세한 설명은 강의 본문 + 아래 링크 참고
        - https://www.geeksforgeeks.org/introduction-of-classful-ip-addressing/
        - https://en.wikipedia.org/wiki/Classful_network
        - https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html
- Network 영역의 bit가 모두 0과 1인 경우는 HOST ID로 사용할 수 없다. 미리 예약된 값이기 때문.
    - 모두 0인 경우, 네트워크 주소로 사용된다. 모두 1인 경우, 브로드캐스트 주소로 사용된다.
- A 클래스의 0.0.0.0/8, 127.0.0.0/8는 특수 목적으로 예약되어 있다.
    - 0.0.0.0/8 현재 네트워크(=디폴트 라우트)를 의미한다. 127.0.0.0/8 루프백 주소를 의미한다.
    - 루프백은 네트워크 장치가 자기 자신과 통신할 때 사용되는 IP 주소이다.
    - 그 외 예약된 IP 주소 범위 정보: https://en.wikipedia.org/wiki/Reserved_IP_addresses
- 특정 Host ID는 인터넷 승인 기관에서 기업이나 단체에 배정해준다.
    - 많은 Host를 표현 가능한 경우, 여러 이유로 더 작은 서브넷으로 나눈다.

- D 클래스: 멀티케스트에서 사용된다. 
    - 특징: 
        - 서브넷 마스크 개념이 적용되지 않음
        - 네트워크 부분과 호스트 부분으로 나누어지지 않음
        - 전체 32비트가 멀티캐스트 그룹 식별자로 사용됨
    - 멀티케스트 값을 받고 싶어하는 Host에서 특정 D 클래스의 IP를 받고 싶다고 표시하고 있으면, (멀티케스트를 지원한다면) 라우터에서 해당 호스트에 나눠서 전달한다.
        - 즉, 브로드캐스트 트래픽은 속한 서브넷 바깥으로 벗어날 수 없다.
        - 이는 유니케스트보다 대역폭이 적고, 브로드캐스트와 달리 불필요한 Host에게 전달되어 인터럽트가 발생하지 않는다. (= 효율적이다.)
- E 클래스: 연구 및 실험용으로 예약되었으며, 실제론 전혀 사용되지 않는다. 


### 느낀점

저번 스터디 때, 궁금해 했던 멀티케스트 내용이 여기 나왔음.

이 부분은 많이 듣긴 듣는데, 진짜 이해 잘 안돼는 부분중에 하나라고 생각함.   
나중에 실습 문제라도 풀다보면 좀 이해가려나?

---

> Source: `section_08/ysj/note.md`

## Section 08 정리

## 서브네팅

#### CIDR - Classless Inter-Domain Routing

- CIDR (Classless Inter-Domain Routing)
기존 클래스 기반 IP 주소는 비효율적으로 많은 호스트 주소를 낭비하는 문제가 있었다.
- CIDR은 이를 해결하기 위해 고정된 서브넷 요구사항을 제거하고, 주소를 필요한 만큼만 할당할 수 있도록 한다.
    - e.g. 175.10.10.0/20처럼 네트워크의 일부만을 할당하여 IP 자원을 절약.
- **경로 요약(Route Aggregation)**이 가능하여 라우터의 메모리 및 성능을 최적화하고 네트워크의 안정성(추상화)을 높인다.
    - 이 경우 라우터에 알려지는 주소가 254개가 아니라 1개므로 라우터가 관리할 메모리가 줄어든다.
    - e.g. ISP A가 175.10.1.0/24에서 175.10.255.0/24까지 관리할 때, 라우터는 175.10.0.0/16로 한 번에 처리할 수 있다.
- `/~~ 서브넷 마스크`라는 표현이 CIDR로 인해서 나왔다. (기존에는 주소가 고정되었으므로, ip 값만 보고 바로 알 수 있었음.)


#### Subneting  

- IPv4는 원래 모든 호스트가 공공 IP 주소를 가지도록 설계되었다. 그러나 현대 네트워크는 주로 개인 IP 주소를 사용하며, 이를 이해하기 위해 IPv4의 기본 동작 방식을 먼저 학습해야 한다.

- 서브네팅 (Subnetting)
    - 서브네팅은 하나의 IP 주소 범위를 여러 작은 네트워크로 나누는 기술로, 네트워크 관리 효율성과 비용 절감을 위해 사용한다.
    - 큰 네트워크를 구입해 작은 서브넷으로 나누는 것이 여러 작은 네트워크를 구입하는 것보다 비용적으로 유리하기 때문.
- 서브넷은 **호스트 비트를 네트워크 비트로 빌려오는 과정**을 통해 만들어지며, 이를 통해 더 많은 서브넷을 생성하고 각 서브넷의 호스트 수는 줄어듭니다.
    - 서브넷 수는 `2^서브넷 비트 수`로 계산되고, 호스트 수는 `2^호스트 비트 수 - 2`로 계산된다. 네트워크 ID와 브로드캐스트 주소는 호스트로 사용할 수 없기 때문.
    - e.g. /28 서브넷 마스크를 사용하면 16개의 서브넷이 생성되고, 각 서브넷에 14개의 호스트 주소가 할당된다.

- Subnet Zero 과 All-Ones Subnet (더 찾아본 내용 추가됨)
    - Subnet Zero:
        - 네트워크 주소의 서브넷 부분이 모두 0인 서브넷.
        - e.g.: 172.16.0.0/24에서 172.16.0.0.
    - All-Ones Subnet
        - 네트워크 주소의 서브넷 부분이 모두 1인 서브넷.
        - e.g. 172.16.0.0/24에서 172.16.255.0.
        - 역사적 배경
            - 초기 IP 구현에서는 이러한 서브넷 사용이 금지되었습니다.
            - RFC 950에서 이 제한을 명시했으나, 현재는 대부분의 시스템에서 지원됩니다. (네트워크 부족 문제로 인해서)
    - Cisco IOS 12.0 이후부터 기본적으로 활성화되어 있다.
    - 두 옵션이 사용 가능한 이유는 더 작은 서브넷 단위로 나누었기 때문에, 네트워크 ID와 브로드캐스트 주소 또한 서브넷만 가져도 된다. 가장 상위 네트워크 주소의 네트워크 ID와 브로드캐스트 주소는 없어도 처리 가능하다.
    - 하지만, 오래된 시스템에서 지원하지 않을 수 있는 문제가 있어서 사용할 필요가 없다면 사용하지 않는게 좋을 듯. 

- 참고: https://www.cisco.com/c/ko_kr/support/docs/ip/dynamic-address-allocation-resolution/13711-40.html

#### /31 vs /30 서브넷 마스크

- /31 서브넷
    - 이 경우 2를 빼면 0이기 때문에, 주로 네트워크 및 브로드캐스트 주소가 필요없는 **지점 간 링크(point-to-point link)**에서 사용한다.
        - [관련 위키피디아 링크](https://ko.wikipedia.org/wiki/%EC%A0%90%EB%8C%80%EC%A0%90_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
        - Cisco 라우터 등에서 지원하며 트래픽이 두 지점 간에만 흐른다.
- /30 서브넷
    - 2(`(2^2)-2`)개의 호스트를 가질 수 있다.
    - 일반적으로는 /31보다 /30을 더 많이 사용한다.

#### VLSM

- 용어
    - VLSM(Variable-Length Subnet Mask)
        - 가변 길이 서브넷 마스크
        - 여러 크기의 서브넷 마스크를 하나의 네트워크 내에서 함께 사용 가능
        - 초기 이후 라우팅 프로토콜에서 지원
    - FLSM(Fixed-Length Subnet Masking)
        - 고정 길이 서브넷 마스크
        - 초기 라우팅 프로코톨에서 지원
        - 한 서브넷 마스크를 사용했다면 각 서브넷이 모두 같은 크기여야 했다.

#### Private IP

RFC 1918

- 인터넷에 연결되지 않아야 하는 IP를 할당하는 경우, 구매하지 않고 사용 가능한 Private IP를 사용함.
- [여기서 범위를 알 수 있음.](https://en.wikipedia.org/wiki/Private_network)
- Private IP를 사용하는 경우 인터넷에 사용되지 않기 때문에 재사용 가능하다.
    - 이 점 때문에 뒤에서 후술할 NAT에서도 쓰임.

#### IPv6, NAT

- IPv4를 대체하기 위해서 나옴. 앞으로도 충분히 대응 가능한 주소 범위를 가짐.
- 그러나, 이미 IPv4를 사용하는 조직이 많아서 NAT라는 대체 방법을 사용했음.
- IPv6의 주소 형식은 IPv4와 많은 차이가 있고 NAT나 잘 동작하고 있기 때문에, 새로운 시스템을 구축하는게 아닌 이상 IPv6로 전환하지 않는 경우가 많다.
- 그러나 장기적으로는 IPv6를 사용하게 될 것.

- NAT는 공인 IP 하나를 공유하는 여러 Private IP가 있고, 인터넷을 통할떄는 공인 IP로 처리하도록 한다.
    - 이 경우 하나의 공인 IP만으로 많은 호스트를 처리 가능하므로 널리 쓰이고 있다.

## 리뷰

- Subnet Zero 과 All-Ones Subnet 부분이 이해가 안가서 찾아보느라 힘들었다.
- 실제 연습 부분이 많아서 좀 스킵하면서 봄.
    - 학교에서 많이 했으니까 뭐...





---

> Source: `section_09/ysj/note.md`

## Section 09 정리

#### OSI Model - Layer 2 - Reference Layer

- 자주 헷갈리는 부분: 실제 전송은 PDU(Protocol Data Unit) 하나만 이루어진다. 각 계층의 관점에 따라서 Data, Segment, Packet, Frame으로 불린다.

- [2계층에서 사용되는 프로토콜](https://en.wikipedia.org/wiki/List_of_network_protocols_(OSI_model)) 종류

- 이 계층에서 프레임이 비트로 인코딩되고, 물리층에 배치될 준비를 하며 오류 감지 및 수정 기능도 제공된다. 

- [이더넷 프레임 정보](https://en.wikipedia.org/wiki/Ethernet_frame)

- 이더넷은 로컬 네트워크(LAN)에서 주로 사용되는 2계층 매체로, 이더넷 헤더에는 출발지와 목적지 MAC 주소, 그리고 데이터가 포함됩니다. 
    - LAN이 아닌 광역망에서 사용되기도 한다. (이건 강의 후반부에 따로 한다고 함.)

- MAC 주소는 이더넷 장치 간 통신을 위한 48비트의 고유한 주소이다. 
    - 첫 24비트는 OUI(Organizationally Unique Identifier)로 제조사를 나타내고, 나머지 24비트는 제조사가 할당한 고유 값이다. 
    - 이를 통해 네트워크 카드, 라우터 등의 장비가 네트워크 상에서 서로를 식별한다.
- MAC 주소는 논리적 주소 지정이 없다.
    - 물리적(기기에 의존되는 값)이라는 말이 아니라, 논리적인 관계가 없다는 뜻이다.
    - MAC 주소에는 논리적인 순서가 없으므로 IP처럼 그룹화해서 관리할 수 없다.


## 리뷰

예전에 도현이랑 (뭔지는 기억 안남) 공부하면서 나왔던 "MAC 주소 값도 바꿀 수 있어서 충분히 네트워크 통신이 가능한데, 왜 IP를 사용하는가?"라는 주제가 있었다.

그때는 MAC은 바꾸기 어렵고, IP가 일종의 구현을 가리는 추상화 같은 효과를 가지기 떄문이라고 애매하게 결론 난걸로 기억하는데, 

강의 이 파트 보면서 더 확실하게 알게 되었다. 

IP를 사용해야 하는 이유는, MAC 주소는 논리적 주소 지정이 없기 때문에 대규모의 인프라 관리가 어렵기 때문이다.



---

> Source: `section_10/ysj/note.md`

## Section 10 정리

#### OSI Model - Layer 2 - Physical Layer


- 역할 및 기능
    - 비트스트림 전달: OSI 1계층은 데이터를 실제 비트스트림으로 변환하여 전송한다. 전기 임펄스, 광 신호, 라디오 신호를 사용해 데이터를 전송한다.
    - 하드웨어 제어: 네트워크의 전기 및 기계적 수준을 제어하며, 데이터 전송을 위한 하드웨어 수단을 제공한다.
    - 물리적 구성 요소 관리: 어떤 케이블, 인터페이스 카드, 이더넷 또는 WAN 포트 유형을 사용할지 결정한다.

- 이더넷 LAN 연결
    - 동축 케이블: 과거에 사용되었으나 현재는 더 이상 사용되지 않음.
    - 현대적 연결: 꼬인 구리 쌍 케이블, 광섬유, 무선을 사용.
- 구리 케이블
    - UTP(Unshielded Twisted Pair): 데스크탑과 스위치 연결에 가장 일반적으로 사용되는 구리 케이블.
    - RJ-45 커넥터: UTP 케이블의 끝에 연결되는 표준 커넥터. (일반적인 LAN선 끝에 있는거임.)
    - [케이블 카테고리 차이는 여기서 확인](https://en.wikipedia.org/wiki/Ethernet_over_twisted_pair)
- 케이블 유형: 직선 및 교차
    - 직선 케이블: PC나 라우터와 같은 단말 장치를 스위치에 연결할 때 주로 사용.
    - 교차 케이블: 동일한 유형의 장치(예: 두 대의 스위치나 PC)를 연결할 때 사용.
        - 요즘에는 PC 간에는 잘 안쓰이고, 스위치 같이 네트워크 구성할 때 주로 사용함.
    - Auto MDI-X: 현대적 스위치는 수신 및 전송 신호를 자동으로 재구성하여 직선 케이블로도 교차 케이블처럼 사용할 수 있음.
- 광섬유 케이블
    - 장점: 더 긴 거리와 더 넓은 대역폭 지원. 두 건물 간 또는 건물 내부에서 스위치 간 연결에 사용.
    - 종류:
        - 단일 모드(Single-mode): 더 긴 거리와 높은 대역폭을 지원하지만 더 비쌈.
        - 다중 모드(Multi-mode): 단일 모드보다 짧은 거리 지원, 더 저렴함.
    - 거리 및 대역폭: 다중 모드 광섬유는 최대 400m까지, 단일 모드는 수백 킬로미터까지 연결 가능.
    - 광섬유 케이블과 커넥터:
        - 광섬유 케이블은 데이터를 빛의 형태로 전송하므로, 빛 신호를 전기 신호로 변환해주는 트랜스시버(transceiver)가 필요하다.
        - 또한 광섬유 케이블용 포트는 종류가 다양하고, 스위치에서 따로 지원하지 않기 때문에, 트랜스시버가 스위치와 광섬유를 연결하는 역할을 한다.
        - [참고](https://en.wikipedia.org/wiki/Transceiver)

- PoE(Power over Ethernet)
    - 전원 공급 방식: 이더넷 케이블을 통해 전원 공급을 가능하게 하는 기술.
    - 활용 사례: IP 전화, 무선 액세스 포인트(WAP) 등의 장치에 전원과 네트워크 연결을 동시에 제공.
    - PoE 스위치: 별도의 전원 공급 장치가 필요 없는 편리한 네트워크 환경을 제공.
    - 파워 인젝터: 전원 연결이 어려운 무선 액세스 포인트에 전원을 공급하기 위한 장치.
        - 무선에서 접속 가능한데, 이더넷 케이블로 power 공급이 안되는 경우, 이더넷을 받고, 외부에서 power를 끌고 와서 PoE로 사용할 수 있음.


## 리뷰

딱히 대충 다 알던 내용이라 AI 도움 좀 받아서 정리함...

광섬유 케이블을 전기 신호로 변환하기 위해서 트랜스시버를 사용한다는 건 좀 신기했음.


---

> Source: `section_11/ysj/note.md`

## Section 11 정리

#### 스위치 vs 허브

허브와 스위치는 로컬 네트워크의 PC, 서버, 프린터 같은 장치를 연결하는데 사용됩니다. 

과거에는 스위치가 고가였기 때문에 허브가 주로 사용되었지만, **지금은 스위치가 저렴해져 허브는 사용되지 않는다**.

- 허브는 반이중(Half-Duplex) 모드로 작동하여 데이터를 한 방향으로만 전송할 수 있으며, 모든 연결된 장치가 같은 충돌 도메인을 공유해 동시에 전송 시 충돌이 발생할 수 있다. 
    - 충돌이 발생하면 CSMA/CD 방식을 통해 충돌을 감지하고 복구한다. 
    - 또한, 허브는 OSI 모델의 1계층에서 작동하기 때문에 MAC 주소를 인식하지 못하고, 수신한 프레임을 모든 포트로 전송한다.

- 스위치는 전이중(Full-Duplex) 모드로 작동해 데이터의 수신과 전송을 동시에 할 수 있으며, 각 연결된 장치는 독립된 충돌 도메인(전용 통신 경로)을 가지기 때문에 충돌이 발생하지 않는다. 
    - 스위치는 OSI 모델의 2계층에서 작동하며, MAC 주소를 기억해 관련 포트로만 프레임을 전송함으로써 성능과 보안을 개선한다. 
    - 다만, 브로드캐스트 프레임이나 알 수 없는 유니캐스트(목적지의 포트를 모르는 상태인 경우) 프레임은 모든 포트로 전송된다.

- 하나의 허브나 스위치에 연결해야 하는 포트가 부족한 경우, 여러 허브나 스위치를 다른 포트로 연결하여 확장 가능하다.

#### 스위치의 동작

- MAC 주소 테이블을 참고하여 특정 포트로만 트래픽을 전송한다.
- MAC 주소 테이블: 연결된 포트와 MAC 주소를 매핑하는 테이블(표).
- 목적지가 MAC 주소 테이블에 없는 경우 동작
    - 수신 포트를 제외한 나머지 포트로 프레임을 전송한다.
    - 응답을 받은 모든 호스트는 프레임을 확인한다. 본인이면 응답하고, 아니라면 버린다.
    - 응답이 온 포트를 MAC 주소 테이블에 기록한다.
        - `포트: MAC 주소` 이런 느낌.
- 여러 스위치가 연결 된 경우, 한 포트에 여러 MAC 주소가 있을 수 있다.
    - ![alt text](section_11/ysj/image.png)
    - 스위치 2의 포트 24에는 MAC 주소 1.1.1과 2.2.2가 기록될 수 있다. 스위치 1의 여러 호스트들이 모두 포트 24를 통해 스위치 2에 연결되기 때문.

#### 라우터 vs 스위치

- 라우터
    - 라우터는 여러 IP 서브넷 사이에서 트래픽의 방향을 지시하는 역할을 하며, OSI 모델의 제3계층에서 운용
    - 이는 라우터가 IP 서브넷 간의 트래픽 경로를 지정하는 데 필요. 
    - 제1계층과 제2계층에서도 운용되며(3계층 하위의 기능을 전부 지원하므로)
    - 다양한 인터페이스(이더넷, 시리얼 등)를 지원.
    - 브로드캐스트 트래픽을 전송하지 않음.
    - 호스트의 서브넷이 다른 경우, IP를 기준으로 통신하기 위해서 사용함.
- 스위치
    - 2계층에서 로컬 네트워크를 연결하는데 사용됨.
    - 보통 라우터보다 더 많은 포트를 가지고, 대부분 이더넷 인터페이스만 지원함.
    - 브로드캐스트 트래픽을 전송함.
    - 호스트의 서브넷이 같은 경우만 통신 가능함.
- 3계층 스위치 
    - IP를 인식 가능한 스위치
    - 스위치의 특징을 가짐: 이더넷 + 더 많은 포트
    - 로컬 네트워크 내에서 다른 서브넷 간 통신을 위해서 주로 사용함.


다양한 종류의 포트를 지원한다. (인터페이스를 사용해서 다양한 방식의 통신이 가능.) 

#### 기타 Cisco 기기

네트워크 공부에는 별로 안중요해서 생략

## 실습

- 그냥 자료해서 하라는거 그대로 따라하면 됨.
    - 프롬프트 관련한거 설명은 없어서, 이전 자료 찾아봄.

## 리뷰

허브가 이제 안 쓰인다고 하는데, 그럼 우린 어째서 학교에서 네트워크 수업시간에 CSMA/CD를 공부헀던걸까...

대충 들어만 봤던게 좀 더 명확해진 느낌.


---

> Source: `section_11/ysj/ref_sec_66_my.md`


# 11 Cisco 장치 기능 - 실습 연습

이 실습은 Cisco IOS 스위치의 MAC 주소 테이블과 Cisco IOS 라우터의 라우팅 테이블을 탐구합니다.

이 실습은 Cisco 장치 기능에 대한 안내된 연습입니다. 여기에 있는 모든 명령을 아직 이해하지 못하더라도 걱정하지 마세요 - 과정의 나머지 부분을 진행하면서 더 자세히 다룰 것입니다.

## 실습 토폴로지
[이미지]

## 시작 구성 로드하기

Packet Tracer에서 '11 Cisco Device Functions.pkt' 파일을 열어 실습을 로드하세요.
이는 각 라우터를 10.10.10.0/24 네트워크의 IP 주소로 미리 구성합니다.

## 스위치 MAC 주소 테이블 확인하기

1) R1에서 R4까지의 라우터에 로그인하고 10.10.10.0/24 네트워크에 구성된 인터페이스를 확인하세요.

```
R1#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 10.10.10.1 YES manual up up
GigabitEthernet0/1 unassigned YES unset administratively down down 
GigabitEthernet0/2 unassigned YES unset administratively down down 
Vlan1 unassigned YES unset administratively down down

R2#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 10.10.10.2 YES manual up up
GigabitEthernet0/1 unassigned YES unset administratively down down
GigabitEthernet0/2 unassigned YES unset administratively down down
Vlan1 unassigned YES unset administratively down down

R3#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 unassigned YES unset administratively down down
GigabitEthernet0/1 10.10.10.3 YES manual up up
GigabitEthernet0/2 unassigned YES unset administratively down down
Vlan1 unassigned YES unset administratively down down

R4#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 10.10.10.4 YES manual up up
GigabitEthernet0/1 unassigned YES unset administratively down down 
GigabitEthernet0/2 unassigned YES unset administratively down down 
Vlan1 unassigned YES unset administratively down down
```

R1, R2, R4는 GigabitEthernet0/0을 사용하고, R3는 GigabitEthernet0/1을 사용합니다.

2) 이 인터페이스들의 MAC 주소를 기록하세요.

```
R1#show interface gig0/0
GigabitEthernet0/0 is up, line protocol is up (connected) 
Hardware is CN Gigabit Ethernet, address is 0090.2b82.ab01 (bia 0090.2b82.ab01)

R2#show interface gig0/0
GigabitEthernet0/0 is up, line protocol is up (connected) 
Hardware is CN Gigabit Ethernet, address is 0060.2fb3.9152 (bia 0060.2fb3.9152)

R3#show interface gig0/1 
GigabitEthernet0/1 is up, line protocol is up (connected) 
Hardware is CN Gigabit Ethernet, address is 0001.9626.8970 (bia 0001.9626.8970)

R4#show interface gig0/0
GigabitEthernet0/0 is up, line protocol is up (connected) 
Hardware is CN Gigabit Ethernet, address is 00d0.9701.02a9 (bia 00d0.9701.02a9)
```

**참고: 실습에서의 MAC 주소는 다를 수 있습니다.**

3) R1에서 R2, R3, R4로 ping을 보내 라우터 간 연결을 확인하세요.

- (`enable` 키워드 사용해서 특권? 더 높은 권한 프롬프트로 이동)

```
R1#ping 10.10.10.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.2, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/3 ms

R1#ping 10.10.10.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.3, timeout is 2 seconds:
.!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms

R1#ping 10.10.10.4
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.4, timeout is 2 seconds:
.!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms
```

4) R2에서 R3와 R4로 ping을 보내세요.

```
R2#ping 10.10.10.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.3, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms

R2#ping 10.10.10.4
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.4, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms
```

5) SW1에서 동적으로 학습된 MAC 주소를 보고 라우터의 MAC 주소가 예상된 포트를 통해 도달 가능한지 확인하세요. 테이블의 다른 MAC 주소는 무시하세요.

```
SW1#show mac address-table dynamic
Mac Address Table

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0001.9626.8970    DYNAMIC     Fa0/24
   1    000c.cf84.8418    DYNAMIC     Fa0/24
   1    0060.2fb3.9152    DYNAMIC     Fa0/2
   1    0090.2b82.ab01    DYNAMIC     Fa0/1
   1    00d0.9701.02a9    DYNAMIC     Fa0/24
```

6) SW2에서 반복하세요.

```
SW2#show mac address-table dynamic 
Mac Address Table

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0001.9626.8970    DYNAMIC     Fa0/3
   1    000b.be53.6418    DYNAMIC     Fa0/24
   1    0060.2fb3.9152    DYNAMIC     Fa0/24
   1    0090.2b82.ab01    DYNAMIC     Fa0/24
   1    00d0.9701.02a9    DYNAMIC     Fa0/4
```


7) SW1의 동적 MAC 주소 테이블을 지우세요.

```
SW1#clear mac address-table dynamic
```

8) SW1의 동적 MAC 주소 테이블을 보여주세요. MAC 주소가 보이나요? 왜 그런가요?

- (내가 하면 이거 지워진 버전으로 아무것도 없이 보임.)

```
SW1#show mac address-table dynamic 
Mac Address Table

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0001.9626.8970    DYNAMIC     Fa0/24
   1    000c.cf84.8418    DYNAMIC     Fa0/24
   1    0060.2fb3.9152    DYNAMIC     Fa0/2
   1    0090.2b82.ab01    DYNAMIC     Fa0/1
   1    00d0.9701.02a9    DYNAMIC     Fa0/24
```

실제 네트워크의 장치들은 자주 트래픽을 보내는 경향이 있어 MAC 주소 테이블이 업데이트됩니다(Packet Tracer에서는 더 적은 항목을 볼 수 있습니다).

스위치는 주기적으로 오래된 항목을 삭제합니다.

## 라우팅 테이블 검사하기

1) R1의 라우팅 테이블을 보세요. 어떤 경로가 있고 왜 그런가요?

```
R1#show ip route

Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

      10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C        10.10.10.0/24 is directly connected, GigabitEthernet0/0
L        10.10.10.1/32 is directly connected, GigabitEthernet0/0
```

라우터는 10.10.10.0/24 네트워크에 대한 연결된 경로와 10.10.10.1/32에 대한 로컬 경로를 가지고 있습니다. 이 경로들은 GigabitEthernet0/0 인터페이스에 IP 주소 10.10.10.1/24가 구성되었을 때 자동으로 생성되었습니다.

2) GigabitEthernet0/1 인터페이스에 IP 주소 10.10.20.1/24를 구성하세요.

- (`config` 프롬프트로 들어가기 위한 키워드)
      - (`enable` -> `config t`)

```
R1(config)#interface GigabitEthernet 0/1
R1(config-if)#ip address 10.10.20.1 255.255.255.0
R1(config-if)#no shutdown
```

- (ip address 10.10.20.1 255.255.255.0 해석?)
      - ip address 할당
      - 주소: 10.10.20.1 
      - 서브넷: 255.255.255.0

3) 지금 라우팅 테이블에는 어떤 경로가 있나요?

```
R1#show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

      10.0.0.0/8 is variably subnetted, 4 subnets, 2 masks
C        10.10.10.0/24 is directly connected, GigabitEthernet0/0
L        10.10.10.1/32 is directly connected, GigabitEthernet0/0
C        10.10.20.0/24 is directly connected, GigabitEthernet0/1
L        10.10.20.1/32 is directly connected, GigabitEthernet0/1
```

- (ip 경로 추가된 모습 확인 가능)
      - 아마 보면 C가 직접 연결된 범위, L은 직접 연결된 Host

라우터는 두 인터페이스에 대한 경로를 가지고 있으며 10.10.10.0/24와 10.10.20.0/24 네트워크의 호스트 간 트래픽을 라우팅할 수 있습니다.

4) 10.10.30.0/24에 대한 정적 경로를 다음 홉 주소 10.10.10.2로 구성하세요.

```
R1(config)#ip route 10.10.30.0 255.255.255.0 10.10.10.2
```

- (위에 키워드 참고해서 똑같이)

5) 지금 라우팅 테이블에는 어떤 경로가 있나요?

```
R1(config)#do show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

      10.0.0.0/8 is variably subnetted, 5 subnets, 2 masks
C        10.10.10.0/24 is directly connected, GigabitEthernet0/0
L        10.10.10.1/32 is directly connected, GigabitEthernet0/0
C        10.10.20.0/24 is directly connected, GigabitEthernet0/1
L        10.10.20.1/32 is directly connected, GigabitEthernet0/1
S        10.10.30.0/24 [1/0] via 10.10.10.2
```
라우터에는 로컬로 연결된 네트워크에 대한 경로가 있으며 10.10.10.2를 통해 사용할 수 있는 10.10.30.0/24에 대한 경로도 있습니다.

- (S는 static이라는데, GPT 피셜로는 자동 라우팅 프로토콜 없이 수동으로 설정하면 저렇게 뜨는듯.)


---

> Source: `section_11/ysj/ref_sec_66_src.md`


# 11 Cisco 장치 기능 - 실습 연습

이 실습은 Cisco IOS 스위치의 MAC 주소 테이블과 Cisco IOS 라우터의 라우팅 테이블을 탐구합니다.

이 실습은 Cisco 장치 기능에 대한 안내된 연습입니다. 여기에 있는 모든 명령을 아직 이해하지 못하더라도 걱정하지 마세요 - 과정의 나머지 부분을 진행하면서 더 자세히 다룰 것입니다.

## 실습 토폴로지
[이미지]

## 시작 구성 로드하기

Packet Tracer에서 '11 Cisco Device Functions.pkt' 파일을 열어 실습을 로드하세요.
이는 각 라우터를 10.10.10.0/24 네트워크의 IP 주소로 미리 구성합니다.

## 스위치 MAC 주소 테이블 확인하기

1) R1에서 R4까지의 라우터에 로그인하고 10.10.10.0/24 네트워크에 구성된 인터페이스를 확인하세요.

```
R1#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 10.10.10.1 YES manual up up
GigabitEthernet0/1 unassigned YES unset administratively down down 
GigabitEthernet0/2 unassigned YES unset administratively down down 
Vlan1 unassigned YES unset administratively down down

R2#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 10.10.10.2 YES manual up up
GigabitEthernet0/1 unassigned YES unset administratively down down
GigabitEthernet0/2 unassigned YES unset administratively down down
Vlan1 unassigned YES unset administratively down down

R3#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 unassigned YES unset administratively down down
GigabitEthernet0/1 10.10.10.3 YES manual up up
GigabitEthernet0/2 unassigned YES unset administratively down down
Vlan1 unassigned YES unset administratively down down

R4#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 10.10.10.4 YES manual up up
GigabitEthernet0/1 unassigned YES unset administratively down down 
GigabitEthernet0/2 unassigned YES unset administratively down down 
Vlan1 unassigned YES unset administratively down down
```

R1, R2, R4는 GigabitEthernet0/0을 사용하고, R3는 GigabitEthernet0/1을 사용합니다.

2) 이 인터페이스들의 MAC 주소를 기록하세요.

```
R1#show interface gig0/0
GigabitEthernet0/0 is up, line protocol is up (connected) 
Hardware is CN Gigabit Ethernet, address is 0090.2b82.ab01 (bia 0090.2b82.ab01)

R2#show interface gig0/0
GigabitEthernet0/0 is up, line protocol is up (connected) 
Hardware is CN Gigabit Ethernet, address is 0060.2fb3.9152 (bia 0060.2fb3.9152)

R3#show interface gig0/1 
GigabitEthernet0/1 is up, line protocol is up (connected) 
Hardware is CN Gigabit Ethernet, address is 0001.9626.8970 (bia 0001.9626.8970)

R4#show interface gig0/0
GigabitEthernet0/0 is up, line protocol is up (connected) 
Hardware is CN Gigabit Ethernet, address is 00d0.9701.02a9 (bia 00d0.9701.02a9)
```

**참고: 실습에서의 MAC 주소는 다를 수 있습니다.**

- (내 로컬에서는 나머지는 다 같은데, R3만 00d0.bc25.21e2로 다름.)

3) R1에서 R2, R3, R4로 ping을 보내 라우터 간 연결을 확인하세요.

```
R1#ping 10.10.10.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.2, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/3 ms

R1#ping 10.10.10.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.3, timeout is 2 seconds:
.!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms

R1#ping 10.10.10.4
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.4, timeout is 2 seconds:
.!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms
```

4) R2에서 R3와 R4로 ping을 보내세요.

```
R2#ping 10.10.10.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.3, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms

R2#ping 10.10.10.4
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.4, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms
```

5) SW1에서 동적으로 학습된 MAC 주소를 보고 라우터의 MAC 주소가 예상된 포트를 통해 도달 가능한지 확인하세요. 테이블의 다른 MAC 주소는 무시하세요.

```
SW1#show mac address-table dynamic
Mac Address Table

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0001.9626.8970    DYNAMIC     Fa0/24
   1    000c.cf84.8418    DYNAMIC     Fa0/24
   1    0060.2fb3.9152    DYNAMIC     Fa0/2
   1    0090.2b82.ab01    DYNAMIC     Fa0/1
   1    00d0.9701.02a9    DYNAMIC     Fa0/24
```

6) SW2에서 반복하세요.

```
SW2#show mac address-table dynamic 
Mac Address Table

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0001.9626.8970    DYNAMIC     Fa0/3
   1    000b.be53.6418    DYNAMIC     Fa0/24
   1    0060.2fb3.9152    DYNAMIC     Fa0/24
   1    0090.2b82.ab01    DYNAMIC     Fa0/24
   1    00d0.9701.02a9    DYNAMIC     Fa0/4
```


7) SW1의 동적 MAC 주소 테이블을 지우세요.

```
SW1#clear mac address-table dynamic
```

8) SW1의 동적 MAC 주소 테이블을 보여주세요. MAC 주소가 보이나요? 왜 그런가요?

```
SW1#show mac address-table dynamic 
Mac Address Table

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0001.9626.8970    DYNAMIC     Fa0/24
   1    000c.cf84.8418    DYNAMIC     Fa0/24
   1    0060.2fb3.9152    DYNAMIC     Fa0/2
   1    0090.2b82.ab01    DYNAMIC     Fa0/1
   1    00d0.9701.02a9    DYNAMIC     Fa0/24
```

실제 네트워크의 장치들은 자주 트래픽을 보내는 경향이 있어 MAC 주소 테이블이 업데이트됩니다(Packet Tracer에서는 더 적은 항목을 볼 수 있습니다).

스위치는 주기적으로 오래된 항목을 삭제합니다.

## 라우팅 테이블 검사하기

1) R1의 라우팅 테이블을 보세요. 어떤 경로가 있고 왜 그런가요?

```
R1#show ip route

Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

      10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C        10.10.10.0/24 is directly connected, GigabitEthernet0/0
L        10.10.10.1/32 is directly connected, GigabitEthernet0/0
```

라우터는 10.10.10.0/24 네트워크에 대한 연결된 경로와 10.10.10.1/32에 대한 로컬 경로를 가지고 있습니다. 이 경로들은 GigabitEthernet0/0 인터페이스에 IP 주소 10.10.10.1/24가 구성되었을 때 자동으로 생성되었습니다.

2) GigabitEthernet0/1 인터페이스에 IP 주소 10.10.20.1/24를 구성하세요.

```
R1(config)#interface GigabitEthernet 0/1
R1(config-if)#ip address 10.10.20.1 255.255.255.0
R1(config-if)#no shutdown
```

3) 지금 라우팅 테이블에는 어떤 경로가 있나요?

```
R1#show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

      10.0.0.0/8 is variably subnetted, 4 subnets, 2 masks
C        10.10.10.0/24 is directly connected, GigabitEthernet0/0
L        10.10.10.1/32 is directly connected, GigabitEthernet0/0
C        10.10.20.0/24 is directly connected, GigabitEthernet0/1
L        10.10.20.1/32 is directly connected, GigabitEthernet0/1
```

라우터는 두 인터페이스에 대한 경로를 가지고 있으며 10.10.10.0/24와 10.10.20.0/24 네트워크의 호스트 간 트래픽을 라우팅할 수 있습니다.

4) 10.10.30.0/24에 대한 정적 경로를 다음 홉 주소 10.10.10.2로 구성하세요.

```
R1(config)#ip route 10.10.30.0 255.255.255.0 10.10.10.2
```

5) 지금 라우팅 테이블에는 어떤 경로가 있나요?

```
R1(config)#do show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

      10.0.0.0/8 is variably subnetted, 5 subnets, 2 masks
C        10.10.10.0/24 is directly connected, GigabitEthernet0/0
L        10.10.10.1/32 is directly connected, GigabitEthernet0/0
C        10.10.20.0/24 is directly connected, GigabitEthernet0/1
L        10.10.20.1/32 is directly connected, GigabitEthernet0/1
S        10.10.30.0/24 [1/0] via 10.10.10.2
```

라우터에는 로컬로 연결된 네트워크에 대한 경로가 있으며 10.10.10.2를 통해 사용할 수 있는 10.10.30.0/24에 대한 경로도 있습니다.


---

> Source: `section_12/ysj/note.md`

## Section 12 정리

#### DNS - 도메인 이름 시스템

- 패킷은 제4계층인 전송 계층에서 TCP 또는 UDP로 구분되고, 포트 번호가 포함. 
- 그 후 제3계층인 네트워크 계층에서는 IP 주소를 처리하는데, 일반적으로 FQDN(도메인 이름)에서 IP 주소로 변환하기 위해 DNS를 사용한다.
- 네트워크 인프라를 관리하는 조직 내에서는 주로 내부 DNS 서버나 DNS 서버의 군집(클러스터)를 갖는다.
- DNS는 FQDN(Fully Qualified Domain Name)을 IP 주소로 변환해 주며, 내부 DNS 서버는 조직 내에서 호스트의 IP 주소를 관리한다. 
- 하지만 외부의 IP 주소 정보를 요청할 경우 공공 DNS 서버로 요청을 보내야 한다.
    - e.g. 1.1.1.1, 8.8.8.8
- DNS 요청은 일반적으로 UDP + 53 포트를 사용하고, 경우에 따라 TCP + 53 포트로도 전송할 수 있다.
    - TCP 사용 경우: 패킷의 크기가 크거나(여러 패킷으로 보내야 해서), 그 외 특수한 경우.
- DNS 클라이언트: DNS 서버에 질의(요청)를 보내는 역할.
- DNS 서버: 도메인 이름을 IP 주소로 변환하는 역할.

##### Cisco 실습

- 라우터를 DNS 클라이언트로 설정하는 방법:
    - ip domain-lookup: DNS 조회를 활성화.
    - ip name-server [DNS 서버 IP]: 사용할 DNS 서버를 설정.
    - ip domain-name [도메인 이름]: 기본 도메인 이름을 설정.
    - ip domain-list [도메인 접미어]: 추가 DNS 접미어를 설정.
- 라우터를 DNS 서버로 설정하는 방법:
    - ip dns server: 라우터를 DNS 서버로 설정.
    - ip host [호스트명] [IP 주소]: 도메인에 해당하는 호스트명과 IP 주소를 설정.

이러한 명령어들은 라우터가 FQDN을 IP 주소로 변환할 수 있도록 하며, 특히 라우터 간의 네트워크 테스트 시 호스트명을 사용하여 핑 테스트를 할 수 있게 해준다.

- 구체적인 실습과정 설명: https://gist.github.com/YangSiJun528/82bf47cf1bd4d4de8a77f6bcb28ca2a1

#### ARP 주소 변환 프로토콜

- ARP 작동 과정:
    - ARP 필요성: 발신자는 목적지의 IP 주소를 알고 있어 패킷을 3계층(네트워크 계층)까지 구성할 수 있지만, 2계층에서 전송을 위해 MAC 주소를 알아야 한다.
    - ARP 요청 전송: 발신자는 목적지의 MAC 주소를 모르기 때문에, 2계층의 브로드캐스트 트래픽으로 ARP 요청을 보낸다. (MAC 주소에서 브로드캐스트 주소는 `FF:FF:FF:FF:FF:FF`)
    - 수신자가 ARP 요청에 응답: 네트워크 상의 장치 중 해당되는 IP 주소 (예: `172.23.4.2`)를 가진 수신자는 자신의 MAC 주소를 포함한 ARP 응답을 보낸다. (요청에 발신자의 MAC 주소가 있음.) 이 응답은 유니캐스트로 발신자에게 직접 전달됩니다.
    - ARP 캐시에 저장: 발신자는 수신자의 MAC 주소를 받아 자신의 ARP 캐시에 저장한다. 이후 같은 수신자에게 데이터를 보낼 때는 다시 ARP 요청을 보내지 않고, 캐시에서 MAC 주소를 참조해 바로 통신할 수 있다.

- 두 호스트가 서로 다른 서브넷에 있을 때 동작:
    - 서로 다른 서브넷 간 통신에서 ARP의 역할
        - 서로 다른 서브넷에 있는 두 호스트가 통신할 때는 라우터를 통해 트래픽이 전달되어야 한다.
        - 송신자는 자신의 IP 주소와 서브넷 마스크를 사용해 목적지가 다른 서브넷에 있음을 인지하고, 기본 게이트웨이(라우터)의 MAC 주소를 알아내기 위해 ARP 요청을 보낸다.
        - ARP 요청을 받은 라우터는 자신의 MAC 주소로 응답하고, 이후 송신자는 라우터의 MAC 주소로 IP 패킷을 전달한다.
    - 라우터에서의 ARP 동작
        - 라우터는 송신자로부터 받은 IP 패킷을 목적지 서브넷으로 전달하기 전에 목적지 호스트의 MAC 주소를 알아내야 한다. 이를 위해 목적지 서브넷에서 ARP 요청을 보내 MAC 주소를 알아낸다.
        - 라우터는 이렇게 받은 MAC 주소를 사용해 최종적으로 IP 패킷을 목적지 호스트로 전달한다.
    - MAC 주소의 변경
        - 통신 중에 IP 주소는 변경되지 않지만, MAC 주소는 각 네트워크 홉(라우터를 포함한 장치)마다 변경된다. 
            - 왜냐면 IP 주소는 최종 목적지지만, MAC 주소는 최종 목적지 + 그 목적지를 위해 거쳐갈 중간 목적지(기본 게이트웨이, 다른 라우터 등)도 포함하기 때문이다.
        - 즉, 송신자에서 라우터로, 라우터에서 목적지 호스트로 갈 때마다 MAC 주소는 그에 맞게 업데이트된다.
    - 메모: 그냥 간단하게 기본 게이트웨이(라우터)가 중간 중개자 역할을 한다고 생각하면 됨.
        - 게이트웨이에 접근하기 위해서도 MAC 주소가 필요하므로 다른 HOST 처럼 ARP를 통해 게이트웨이의 MAC 주소를 구하기도 한다.
        - 생각해보니 라우터나 스위치도 MAC 주소가 있어야 했음. 스위치는 관리(원격)외에는 딱히 쓰이지 않겠지만, 라우터는 hop으로 사용되기 때문에 필요함.

- 기본 게이트웨이
    - 서로 다른 네트워크(서브넷)에 있는 장치와 통신할 때는 기본 게이트웨이가 필수적이다. 
    - 패킷을 받아 적절한 네트워크로 데이터를 전달하는 기능을 수행하며, 주로 라우터(해당 기능을 수행할 수 있는)이다.
    - 기본 게이트웨이는 NAT를 구현하는 라우터로 작동할 수 있으나, 그게 기본 게이트웨이의 필요성의 유일한 원인은 아니다.

- 강의에선 안나오는데, 생각나서 찾은 RARP
    - RARP(Reverse Address Resolution Protocol, 역방향 주소 결정 프로토콜)
    - 지금은 BOOTP(Bootstrap Protocol)와 DHCP(Dynamic Host Configuration Protocol)로 대체됨.
        - MAC 주소와 IP 주소만 처리할 수 있었고, 서브넷 마스크나 게이트웨이 정보 같은 추가적인 설정을 처리할 수 없다는 한계가 있었음.
    - RARP는 주로 디스크 없는 장치(diskless device)나 부팅 시 IP 주소를 모르는 장치들이 자신의 IP 주소를 할당받기 위해 사용되었다.

#### 패킷의 생에

- 이건 굳이 설명하기보단 그냥 강의 보는게 더 나아보임. 자막 + 2배속이면 15분도 안됨.
    - 아니면 AI 사용해서 정리한거 보던가: https://gist.github.com/YangSiJun528/82bf47cf1bd4d4de8a77f6bcb28ca2a1
    - https://www.udemy.com/course/cisco-ccna-complete-guide-korean/learn/lecture/46337711
        - 2부로, 다음 영상까지 보면됨.

## 실습

## 리뷰

- 이 부분은 내용이 좋았다. 네트워크 송수신의 기초(핵심)적인 동작을 알게 됨.
- 네트워크 통신 중 IP 주소는 고정되지만, MAC 주소가 변경된다는 건 OSI 계층에 따라서 역할이 다르다는 걸 보여주는 좋은 예시인것 같음.
    - MAC은 상대적으로 저수준이라 중간 목적지 + 최종 목적지를 표시하므로 계속 바뀌지만 IP는 고수준이라 값이 고정임.


---

> Source: `section_12/ysj/ref_sec_74_answer.md`

이 실습은 Cisco 라우터의 DNS 클라이언트 구성과 ARP 캐시를 탐구합니다.

## 라우터를 DNS 클라이언트로 구성

**참고:** Packet Tracer에서 라우터는 DNS 서버가 될 수 없습니다('ip dns server' 명령을 지원하지 않음). 따라서 Packet Tracer 서버 장치를 DNS 서버로 사용합니다.

IP 주소가 10.10.10.10인 호스트가 DNS 서버로 구성되어 'R1', 'R2', 'R3'에 대한 DNS 요청을 해결할 수 있습니다. 도메인 이름은 사용되지 않습니다.

1) R1, R2, R3을 10.10.10.10을 DNS 서버로 사용하도록 구성하세요. 도메인 이름이나 도메인 목록을 구성할 필요는 없습니다.

```
R1(config)#ip domain-lookup
R1(config)#ip name-server 10.10.10.10
R2(config)#ip domain-lookup
R2(config)#ip name-server 10.10.10.10
R3(config)#ip domain-lookup
R3(config)#ip name-server 10.10.10.10
```

2) R1에서 호스트 이름 'R2'와 'R3'을 사용하여 R2와 R3에 ping을 보낼 수 있는지 확인하세요(DNS 서버가 DNS 요청을 해결하는 데 시간이 걸릴 수 있습니다).

```
R1#ping R2
```

3) R3에서 호스트 이름 'R1'과 'R2'를 사용하여 R1과 R2에 ping을 보낼 수 있는지 확인하세요.

```
R3#ping R1
R3#ping R2
```

## 라우터의 ARP 캐시 검사

4) R1의 ARP 캐시에 R3에 대한 항목이 있을 것으로 예상하나요? 그 이유는 무엇인가요?

ARP 요청은 브로드캐스트 트래픽을 사용하므로 라우터에 의해 전달되지 않습니다. R1은 직접 연결된 네트워크(10.10.10.0/24)에서 본 모든 호스트에 대한 항목을 ARP 캐시에 가지게 됩니다.

R1은 10.10.20.0/24 네트워크에 직접 연결되어 있지 않으므로 10.10.20.1의 R3에 대한 항목이 ARP 캐시에 없을 것입니다.

R1은 R2의 IP 주소 10.10.10.2를 통해 R3에 도달할 수 있습니다 - 이 IP 주소는 ARP 캐시에 포함됩니다.
10.10.10.10의 DNS 서버도 R1과 동일한 IP 서브넷에 있으므로 ARP 캐시에 나타날 것입니다.

5) R1, R2, R3의 ARP 캐시를 확인하세요.

```
R1#show arp
R2#show arp
R3#show arp
```

R2는 10.10.10.0/24와 10.10.20.0/24에 직접 연결되어 있으므로 두 네트워크 모두에 대한 항목이 ARP 캐시에 있습니다.

R3는 10.10.20.0/24 네트워크에 직접 연결되어 있으므로 해당 네트워크에 대한 항목만 ARP 캐시에 있습니다. 10.10.10.0/24 네트워크에 대한 항목은 없습니다.


---

> Source: `section_12/ysj/ref_sec_74_ex_src.md`

# 12 패킷의 생명 - 실습 연습

이 실습은 Cisco 라우터의 DNS 구성과 ARP 캐시를 탐구합니다.

## 실습 토폴로지


Packet Tracer에서 '12 The Life of a Packet.pkt' 파일을 열어 실습을 로드하세요.
이는 위에 표시된 대로 실습 토폴로지를 구성하고 R1과 R3 사이에 정적 경로를 추가합니다.

## 라우터를 DNS 클라이언트로 구성

Packet Tracer에서는 라우터가 DNS 서버가 될 수 없음('ip dns server' 명령을 지원하지 않음)에 유의하세요. 따라서 우리는 Packet Tracer 서버 장치를 DNS 서버로 사용하고 있습니다.

IP 주소가 10.10.10.10인 호스트가 DNS 서버로 구성되어 있으며 'R1', 'R2', 'R3'에 대한 DNS 요청을 해결할 수 있습니다.
도메인 이름은 사용되지 않습니다.

1) R1, R2, R3가 10.10.10.10을 DNS 서버로 사용하도록 구성하세요. 도메인 이름이나 도메인 목록을 구성할 필요는 없습니다.
2) R1에서 호스트 이름 'R2'와 'R3'를 사용하여 R2와 R3에 ping을 보낼 수 있는지 확인하세요(DNS 서버가 DNS 요청을 해결하는 데 시간이 걸릴 수 있습니다).
3) R3에서 호스트 이름 'R1'과 'R2'를 사용하여 R1과 R2에 ping을 보낼 수 있는지 확인하세요.

## 라우터의 ARP 캐시 검사
4) R1의 ARP 캐시에 R3에 대한 항목이 있을 것으로 예상하나요? 그 이유는 무엇인가요?
5) R1, R2, R3의 ARP 캐시를 확인하세요. 무엇이 보이나요?


---

> Source: `section_13/ysj/note.md`

## Section 13 정리

#### Cisco 문제 해결 방법론


- Cisco 문제 해결 방법론 추천
    - 문제 정의
    - 정보 수집
    - 정보 분석
    - 잠재적 원인 제거
    - 가설 제시
    - 가설 검증
    - 해결 방법 기록
- 위에서 아래로 진행하되, 필요에 따라 중간 단계 스킵 가능.

- 문제 해결 접근 방식:
    - 탑다운 방식
    - 바텀업 방식
    - 분할 정복 방식: 특정 계층 원인이라고 예상되는 부분부터

- 문제 해결 방법:
    - 설정 비교: 다른 설정들과 비교
    - 경로 추적: 출발지부터 목적지까지의 과정 따라가기
    - 부품 교체: 설정 문제 없는데도 오류 발생 시

- 자주 사용되는 문제 해결 명령어:
    - ping: 양방향 연결성 확인 - 3계층이라서 IP까지만 확인 가능. port X
    - traceroute: 경로상의 라우터 정보 제공 - 3계층
    - telnet: 포트 연결성 확인 및 장치 관리 - 4계층


## 실습

## 리뷰

여기는 딱히 없다...

---

> Source: `section_13/ysj/ref_sec_78_answer.md`

## 13 시스코 문제해결 방법론 - 답변 키

이 실습은 네트워크 문제해결 능력을 테스트합니다.

**DNS 서버 연결 문제 해결**

Packet Tracer에서는 라우터가 DNS 서버가 될 수 없으므로('ip dns server' 명령을 지원하지 않음) Packet Tracer 서버 장치를 DNS 서버로 사용하고 있습니다.

1) IP 주소가 10.10.10.10인 호스트가 DNS 서버로 구성되어 'R1', 'R2', 'R3'에 대한 요청을 해결할 수 있어야 합니다. 직원들이 DNS가 작동하지 않는다고 불평했습니다.

2) R3에서 Telnet을 사용하여 10.10.10.10의 DNS 서버에서 DNS 서비스가 작동하는지 확인하십시오.

R3#telnet 10.10.10.10
Trying 10.10.10.10 ...
% Connection timed out; remote host not responding

3) DNS가 작동하지 않는 것을 확인한 후 문제를 해결하고 수정하십시오. R3가 호스트 이름으로 R1을 ping할 수 있을 때 문제가 해결된 것입니다. 문제의 원인이 하나 이상일 수 있습니다.
(DNS 서버를 클릭한 다음 '서비스' 탭을 클릭하여 서버의 DNS 구성을 확인할 수 있습니다.)

[이미지]

문제를 해결하는 방법은 여러 가지가 있습니다. 제안된 워크플로우는 아래와 같습니다.

문제를 해결할 때 처음 두 가지 질문은 다음과 같습니다:
1. 이전에 작동했습니까? 그렇다면 문제를 일으킬 수 있는 변경 사항이 있었습니까? 이는 일반적으로 원인을 가리킵니다.

이 질문은 DNS 서버가 처음으로 온라인 상태가 되었기 때문에 우리의 예시에는 특별히 유용하지 않습니다.

2. 문제가 모든 사람에게 영향을 미치나요, 아니면 특정 사용자에게만 영향을 미치나요? 한 사용자에게만 영향을 미친다면 문제가 그 사용자 쪽에 있을 가능성이 높습니다.

이 경우 문제는 모든 사용자에게 영향을 미치므로 문제는 서버 쪽이나 네트워크에 있을 가능성이 높습니다.

Telnet을 시도했을 때 오류 메시지는 '원격 호스트가 응답하지 않음'이었으므로 연결 문제로 보입니다.

R3에서 DNS 서버로 ping을 보냅니다.

R3#ping 10.10.10.10
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.10, timeout is 2 seconds:
U.U.U

Success rate is 0 percent (0/5)

ping이 네트워크 계층에서 실패하므로 이 문제를 해결할 때까지 더 높은 계층에서 DNS 서비스를 확인할 필요가 없습니다.

hop by hop으로 연결을 확인하는 대신 traceroute를 사용하여 시간을 절약할 수 있습니다.

R3#traceroute 10.10.10.10
Type escape sequence to abort.
Tracing the route to 10.10.10.10
1 10.10.20.2 0 msec 0 msec 0 msec
2 10.10.20.2 !H * !H
3 * *

traceroute가 R2까지 도달했음을 알 수 있으며, 이는 R3가 DNS 서버에 도달하기 위한 올바른 경로를 가지고 있고 문제가 R2와 DNS 서버 사이에 있을 가능성이 높다는 것을 알려줍니다.

R2는 10.10.10.0/24 네트워크에 연결된 인터페이스를 가지고 있으므로 DNS 서버로의 경로가 있는지 확인할 필요가 없습니다. 하지만 인터페이스가 작동 중인지 확인해야 합니다.

R2#sh ip int brief
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            10.10.10.2      YES NVRAM  administratively down down
FastEthernet0/1            unassigned      YES NVRAM  administratively down down
FastEthernet1/0            10.10.20.2      YES NVRAM  up                    up
FastEthernet1/1            unassigned      YES NVRAM  administratively down down
Vlan1                      unassigned      YES NVRAM  administratively down down

문제가 여기 있습니다 - DNS 서버를 향하는 FastEthernet0/0이 관리적으로 종료되어 있습니다. 이를 수정합시다.

R2(config)#interface f0/0
R2(config-if)#no shutdown

다음으로 R3에서 DNS 서버로 다시 ping을 보내 연결이 수정되었는지 확인합니다.

R3#ping 10.10.10.10
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.10, timeout is 2 seconds:
. .!!!
Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms

더 나아 보입니다 - 처음 한두 개의 ping이 떨어져도 걱정하지 마세요. ARP 캐시가 업데이트되는 동안 지연이 있을 수 있습니다. 다음으로 DNS가 작동하는지 확인합니다.

R3#ping R1
Translating "R1"...domain server (10.10.10.1)
% Unrecognized host or address or protocol not running.

오류 메시지를 자세히 읽어보면 문제를 알 수 있습니다 - R3가 10.10.10.1을 DNS 서버로 사용하고 있지만 올바른 주소는 10.10.10.10입니다.

다음으로 이를 수정합니다. 잘못된 항목을 먼저 제거하는 것을 잊지 마세요.

R3(config)#no ip name-server 10.10.10.1
R3(config)#ip name-server 10.10.10.10

그런 다음 다시 테스트합니다.

R3#ping R1
Translating "R1"...domain server (10.10.1)
% Unrecognized host or address or protocol not running.

오류 메시지가 여전히 있습니다. 우리는 연결이 있고 R3에서 DNS 서버가 올바르게 구성되어 있다는 것을 알고 있으므로 문제는 DNS 서버에 있는 것 같습니다.

10.10.10.10 호스트에서 DNS 서비스가 실행 중인지, 그리고 'R1', 'R2', 'R3'에 대한 주소 레코드가 구성되어 있는지 확인합니다.

[이미지]

주소 레코드는 있지만 DNS 서비스가 꺼져 있습니다. 다시 켭니다.

[이미지]

R3에서 다시 테스트할 시간입니다.

R3#ping R1
Translating "R1"...domain server (10.10.10.10)
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/4 ms

문제가 해결되었습니다.

요약하자면 문제는 다음과 같았습니다: R2의 FastEthernet0/0 포트가 종료되어 있었고, R3가 DNS 서버에 대해 잘못된 IP 주소를 사용하고 있었으며, 서버에서 DNS 서비스가 실행되지 않고 있었습니다.

실제 세계에서의 문제는 보통 이 경우처럼 세 가지 오류가 아닌 하나의 오류로 인해 발생합니다. 그러나 특히 새로운 서비스가 배포될 때는 여전히 이런 일이 발생할 수 있습니다.


---

> Source: `section_13/ysj/ref_sec_78_ex_src.md`

## 13 시스코 문제해결 방법론 실습 연습

이 실습은 네트워크 연결 문제해결 능력을 테스트합니다.

**실습 토폴로지**

[이미지]

**시작 구성 로드**

Packet Tracer에서 '13 The Cisco Troubleshooting Methodology.pkt' 파일을 열어 실습을 로드합니다.

이는 위에 표시된 대로 실습 토폴로지를 구성하고 10.10.10.10을 DNS 서버로 설정하며 R1과 R3 사이에 정적 경로를 추가합니다.

**DNS 서버 연결 문제 해결**

Packet Tracer에서는 라우터가 DNS 서버가 될 수 없으므로('ip dns server' 명령을 지원하지 않음) Packet Tracer 서버 장치를 DNS 서버로 사용하고 있습니다.

1) IP 주소가 10.10.10.10인 호스트가 DNS 서버로 구성되어 'R1', 'R2', 'R3'에 대한 요청을 해결할 수 있어야 합니다. 직원들이 DNS가 작동하지 않는다고 불평했습니다.

2) R3에서 Telnet을 사용하여 10.10.10.10의 DNS 서버에서 DNS 서비스가 작동하는지 확인하십시오.

R3#telnet 10.10.10.10
Trying 10.10.10.10 ...
% Connection timed out; remote host not responding

3) DNS가 작동하지 않는 것을 확인한 후 문제를 해결하고 수정하십시오. R3가 호스트 이름으로 R1을 ping할 수 있을 때 문제가 해결된 것입니다. 문제의 원인이 하나 이상일 수 있습니다.
(DNS 서버를 클릭한 다음 '서비스' 탭을 클릭하여 서버의 DNS 구성을 확인할 수 있습니다.)

[이미지]

힌트: show ip interface brief 명령을 사용하여 라우터와 스위치의 인터페이스가 작동하는지 확인할 수 있습니다. 이 명령은 다음 섹션에서 더 자세히 다룰 것입니다.


---

> Source: `section_14/ysj/note.md`

## Section 14 정리

## 실습

#### 스위치와 라우터 기초

1. 라우터 구성:
   - **라우터는 서로 다른 서브넷을 연결하는 역할을 한다.** 각 서브넷마다 라우터의 인터페이스에 IP 주소를 설정해야 하며, 이 IP 주소는 해당 서브넷의 호스트들이 사용하는 기본 게이트웨이 역할을 합니다.
   - 라우터의 인터페이스는 기본적으로 비활성화되어 있기 때문에, 설정 후에 `no shutdown` 명령어로 활성화해야 합니다.
   - 예시로, `FastEthernet 0/0`에는 IP 주소 `192.168.0.1/24`, `FastEthernet 0/1`에는 `192.168.1.1/24`로 설정하고 `no shutdown`을 실행했다.

2. 스위치 구성:
   - 2계층 스위치는 라우팅(IP 기반)을 하지 않지만, 관리 목적으로 단일 IP 주소를 가질 수 있다. 이는 가상 인터페이스인 VLAN 1에 할당된다. (VLAN은 나중에 설명)
   - 스위치에서 관리 IP 주소는 `VLAN 1`에 설정되며, 이를 통해 telnet이나 SSH로 원격 관리가 가능.
   - 스위치에는 기본 게이트웨이를 설정해 관리자가 다른 서브넷에서 접근할 수 있도록 해야 하며, 이를 위해 `ip default-gateway` 명령어로 게이트웨이 IP를 설정.

3. 실습 예시:
   - 라우터 `R1`의 `FastEthernet 0/0`에 `192.168.0.1`로 IP 주소를 설정한 뒤, 스위치 `SW1`의 가상 인터페이스 `VLAN 1`에 IP 주소 `192.168.0.10`을 설정하여 두 장치가 같은 서브넷에 연결.
   - 스위치에도 기본 게이트웨이로 라우터의 IP `192.168.0.1`을 설정해, 스위치에서 외부 네트워크와 통신이 가능하도록 구성.

4. 호스트 이름과 설명 설정:
   - 호스트 이름**은 장치 식별을 위해 중요하며, 스위치 `SW1`의 호스트 이름을 `hostname SW1`으로 설정.
   - 인터페이스 설명도 문제 해결 시 도움이 되며, `FastEthernet 0/1`에 `description Link to R1`을 추가해 해당 인터페이스가 라우터와 연결되어 있음을 명확히 함.

#### 설정 마법사

초기화된 라우터/스위치에 접속했을 때, 초기 설정을 도와주는 도구.

실무에서는 거의 안씀. 이미 주로 쓰는 구성을 재사용함.

#### 속도 및 듀플렉스 설정

- Duplex: 시스템 상호간 통신시 송신과 수신이 어떤 형식으로 이루어 지는 지에 대한 mode를 말한다. Simplex, Half Duplex, Full Duplex 등.

1. 인터페이스 속도와 듀플렉스 설정
   - 기본적으로 Cisco 장치들은 속도와 듀플렉스가 자동으로 설정됨.
   - 자동 협상(Autonegotiation)을 통해 양쪽 장치가 전이중(Full-Duplex) 및 최대 속도로 설정됨.
   - 수동 설정이 가장 신뢰성 높음. 특히 라우터, 스위치, 서버와 같은 네트워크 장치에서 속도와 듀플렉스를 수동으로 설정하는 것이 추천됨.
   - 중요한 것은 링크 양쪽을 동일하게 설정해야 한다는 것. 양쪽 모두 자동 또는 수동으로 설정해야 함.
   - 한쪽만 자동, 다른 한쪽은 수동으로 설정하면 성능 저하 또는 연결 해제 등의 문제가 발생할 수 있음.
2. 명령어 소개 및 사용
   - duplex full: 인터페이스의 듀플렉스를 전이중으로 설정.
   - speed 100: 인터페이스 속도를 100Mbps로 설정.
3. 구성 및 상태 확인을 위한 명령어
   - show running-config (show run): 현재 스위치 또는 라우터의 전체 구성을 확인하는 명령어. 자주 사용됨.
   - show ip interface brief (sh ip int brief): 인터페이스의 상태 및 IP 주소 구성을 보여주는 명령어. 네트워크 엔지니어가 자주 사용하는 기본 명령어 중 하나.
   - show run interface vlan 1: VLAN 1 인터페이스의 구성을 확인.
   - show run interface: 특정 인터페이스의 구성만을 확인.
   - show version: Cisco 장치의 IOS 버전, 메모리 크기 등의 정보를 확인하는 명령어.
4. 트래픽 확인 및 오류 검사
   - sh int fast0/1: 해당 인터페이스의 MAC 주소, IP 주소, 트래픽 상태 및 오류 여부를 확인.
   - 트래픽이 정상적으로 흐르고 있는지, 에러가 발생하고 있는지를 확인할 수 있음.

#### CDP와 LLDP

- CDP(Cisco Discovery Protocol)
    - CDP는 Cisco 장비 간에 정보를 공유하기 위해 사용되는 Cisco 전용 2계층 프로토콜. 운영 체제, IP 주소 등의 정보를 인접한 Cisco 장비와 교환하며, 이를 통해 네트워크 관리자들이 토폴로지를 파악하고 문제를 해결할 수 있다.
    - 활용:
        - show cdp neighbors 명령어를 통해 인접 장치의 정보를 볼 수 있어 문제 해결이 용이.
    - 설정:
        - 기본적으로 활성화되어 있으나, no cdp run 명령어로 비활성화할 수 있다.
    보안이 중요한 환경에서는 외부로 향하는 인터페이스에서 비활성화할 수 있다(no cdp enable).
    - 명령어: show cdp, show cdp neighbors, show cdp neighbors detail.

- LLDP(Link Layer Discovery Protocol)
    - 개요:
        - LLDP는 CDP와 유사하지만, Cisco 전용이 아닌 공개 표준 프로토콜. 거의 모든 제조사에서 지원되며, CDP와 비슷한 방식으로 네트워크 정보를 교환.

    - 차이점:
        - LLDP는 표준 프로토콜로 Cisco 이외의 장비에서도 사용.
        - 물리적 인터페이스에서만 작동하고, 가상 인터페이스는 지원하지 않음.
        - CDP는 물리적 포트마다 여러 장치를 감지할 수 있지만, LLDP는 포트당 하나의 장치만 감지.
    - 명령어:
        - lldp run, no lldp transmit, no lldp receive, show lldp, show lldp neighbors, show lldp neighbors detail

#### 1, 2 계층 문제 해결

대충 정리

- 1계층 문제: 케이블 손상, 인터페이스 비활성화, 연결 문제 등
    - 구리/광섬유 케이블 손상 주의: 묶거나 감지 않기
    - 스위치 인터페이스 기본 활성, 라우터는 기본 비활성(no shutdown 명령 필요)
    - 케이블 연결 불량, 장치 전원 꺼짐, 손상된 커넥터 등 주의
    - EMI(전자기 간섭): 최신 케이블로 차폐 가능
    - show ip interface brief로 인터페이스 상태 확인
- 2계층 문제: VLAN 설정 불일치, 속도/듀플렉스 불일치
    - 양쪽 인터페이스 설정 일치 확인: 속도, 듀플렉스 자동/수동 설정
    - 듀플렉스 불일치 시 충돌 발생, CDP 로그로 감지

## 실습

## 리뷰

여기서 알게 된 것

- 스위치의 각 인터페이스(포트)는 기본적으로 하나의 MAC 주소를 가지는 호스트만 연결된다.
    - 다른 스위치나 허브에 연결되는 경우 한 포트에 여러 MAC 주소가 학습(매핑? 테이블에 저장)될 수 있다.
- 라우터의 각 인터페이스는 일반적으로 하나의 서브넷을 가지며, 그 인터페이스에 연결된 네트워크의 기본 게이트웨이 역할을 한다.
    - 라우터 하나에 여러 인터페이스가 있다.
        - 라우터 인터페이스 A: IP 주소 192.168.1.1/24 → 이 인터페이스는 서브넷 192.168.1.0/24에 속함.
        - 라우터 인터페이스 B: IP 주소 10.0.0.1/24 → 이 인터페이스는 서브넷 10.0.0.0/24에 속함.
    - 근데, 인터페이스 B는 다른 라우터에 연결되어있고, A는 로컬 내부의 스위치에 연결되서 로컬에서 처리할 수도 있음.
    - 즉, 라우터의 인터페이스 하나는 다른 서브넷에 연결되며, 정적 라우팅 or 동적 라우팅을 통해서 다른 라우터에 연결되거나, 로컬에서 본인이 처리할 수 있다.

- 실제로 동작하는걸 보다보니까 더 잘 이해됨.

---

> Source: `section_14/ysj/ref_sec_86_answer.md`

14 Cisco 라우터 및 스위치 기본 사항 - 답변 키

이 실습에서는 스위치에 대한 기본 구성을 완료하고, Cisco Discovery Protocol CDP를 확인하며, 인터페이스 속도 및 이중 구성의 효과를 분석합니다.

Cisco 라우터 및 스위치 초기 구성
1) Router 1을 'R1'이라는 호스트 이름으로 구성

Router(config)#hostname R1
R1(config)#

2) Router 2를 'R2'라는 호스트 이름으로 구성

Router(config)#hostname R2
R2(config)#

3) Switch 1을 'SW1'이라는 호스트 이름으로 구성

Switch(config)#hostname SW1
SW1(config)#

4) 토폴로지 다이어그램에 따라 R1의 IP 주소 구성

R1(config)#interface FastEthernet0/0
R1(config-if)#ip address 10.10.10.1 255.255.255.0
R1(config-if)#no shutdown

5) 토폴로지 다이어그램에 따라 R2의 IP 주소 구성

R2(config)#interface FastEthernet0/0
R2(config-if)#ip address 10.10.10.2 255.255.255.0
R1(config-if)#no shutdown

6) SW1에 관리 IP 주소 10.10.10.10/24 부여

SW1(config)#interface vlan1
SW1(config-if)#ip address 10.10.10.10 255.255.255.0
SW1(config-if)#no shutdown

7) 스위치는 R2를 통해 다른 IP 서브넷에 연결성을 가져야 함

SW1(config)#ip default-gateway 10.10.10.2

8) 스위치가 기본 게이트웨이를 ping할 수 있는지 확인

SW1#ping 10.10.10.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = (1 / 2 / 8 ms)

9) 장치를 연결하는 인터페이스에 적절한 설명 입력

R1(config)#interface FastEthernet 0/0 R1(config-if)#description Link to SW1

R2(config-if)#interface FastEthernet 0/0
R2(config-if)#description Link to SW1

SW1(config)#interface FastEthernet 0/1
SW1(config-if)#description Link to R1
SW1(config-if)#interface FastEthernet 0/2
SW1(config-if)#description Link to R2

10) SW1에서 R1로의 링크에서 속도와 이중 모드가 100 Mbps 전이중으로 자동 협상되는지 확인

SW1#show interface f0/1
FastEthernet0/1 is up, line protocol is up (connected)
Hardware is Lance, address is 00e0.8fd6.8901 (bia
00e0.8fd6.8901)
Description: Link to R1
BW 100000 Kbit, DLY 1000 usec,
reliability 255/255, txload 1/255, rxload 1/255
Encapsulation ARPA, loopback not set
Keepalive set (10 sec)
Full-duplex, 100Mb/s

11) R2로의 링크에 전이중 및 FastEthernet 속도를 수동으로 구성

SW1(config)#interface FastEthernet 0/2
SW1(config-if)#speed 100
SW1(config-if)#duplex full

R2에서 일치하는 설정을 구성하는 것을 잊지 마세요!
R2(config)#interface FastEthernet 0/0
R2(config-if)#speed 100
R2(config-if)#duplex full

12) 스위치가 실행 중인 IOS 버전은 무엇입니까?

SW1#show version
Cisco IOS Software, C2960 Software (C2960-LANBASE-M), Version 12.2(25)FX, RELEASE SOFTWARE (fc1)

CDP 구성
13) Cisco Discovery Protocol을 사용하여 직접 연결된 Cisco 이웃 확인

SW1#show cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
Device ID Local Intrfce Holdtme Capability Platform Port ID
R1 Fas 0/1 (170   R   C 2800) Fas 0/0
R2 Fas 0/2 (134   R   C 2800) Fas 0/0

14) R1이 CDP를 통해 Switch 1에 대한 정보를 발견하지 못하도록 방지

SW1(config)#interface FastEthernet 0/1
SW1(config-if)#no cdp enable

15) 전역 구성 모드에서 'no cdp run' 명령을 입력한 다음 'cdp run' 명령을 입력하여 R1의 CDP 캐시를 플러시

R1(config)#no cdp run
R1(config)#cdp run

16) R1이 CDP를 통해 SW1을 볼 수 없는지 확인

R1#show cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone, D - Remote, C - CVTA, M - Two-port Mac Relay

Device ID Local Intrfce Holdtme Capability Platform Port ID R1#

스위치 문제 해결
17) show ip interface brief 명령으로 R2에 연결된 스위치 포트의 상태를 확인합니다. 상태와 프로토콜이 up/up으로 표시되어야 합니다.

SW1#show ip interface brief Interface Protocol
Vlan1 10.10.10.10
FastEthernet0/1
FastEthernet0/2

IP-Address
unassigned
unassigned

OK? Method Status
YES manual up up
YES unset up up
YES unset up up

18) R2에 연결된 인터페이스를 종료하고 show ip interface brief 명령을 다시 실행합니다. 상태와 프로토콜이 administratively down/down으로 표시되어야 합니다.

SW1(config)#interface FastEthernet 0/2
SW1(config-if)#shutdown
*Mar 1 00:44:34.212: %LINK-5-CHANGED: Interface
FastEthernet0/2, changed state to administratively down
*Mar 1 00:44:35.219: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/2, changed state to down

SW1(config-if)#do show ip interface brief
Interface IP-Address OK? Method Status
Protocol
Vlan1 10.10.10.10 YES manual up up
FastEthernet0/1 unassigned YES unset up up
FastEthernet0/2 unassigned YES unset administratively down down

19) 인터페이스를 다시 활성화합니다. 속도와 이중 설정을 확인합니다.

SW1(config)#interface FastEthernet 0/2
SW1(config-if)#no shutdown
SW1(config-if)#
*Mar 1 00:45:52.637: %LINK-3-UPDOWN: Interface
FastEthernet0/2, changed state to up
*Mar 1 00:45:53.644: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/2, changed state to up

SW1#sh interface f0/2
FastEthernet0/2 is up, line protocol is up (connected)
Hardware is Lance, address is 00e0.8fd6.8902 (bia 00e0.8fd6.8902)
BW 100000 Kbit, DLY 1000 usec,
reliability 255/255, txload 1/255, rxload 1/255
Encapsulation ARPA, loopback not set
Keepalive set (10 sec)
Full-duplex, 100Mb/s

20) Switch 1에서 이중 모드를 반이중으로 설정합니다. R2의 설정은 그대로 둡니다.

SW1(config-if)#duplex half
SW1(config-if)#
%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to down
%LINEPROTO-5-UPDOWN: Line protocol on Interface
FastEthernet0/2, changed state to down

21) 인터페이스의 상태를 확인합니다.

인터페이스는 down/down 상태입니다. 트래픽을 전달하지 않을 것입니다.
SW1#show ip interface brief
Interface IP-Address OK? Method Status Protocol
FastEthernet0/1 unassigned YES manual up up
FastEthernet0/2 unassigned YES manual down down

22) 이중 모드를 다시 전이중으로 설정합니다.

SW1(config)#int f0/2
SW1(config-if)#duplex full
SW1(config-if)#
%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface
FastEthernet0/2, changed state to up

23) 속도를 10 Mbps로 설정합니다.

SW1(config)#int f0/2
SW1(config-if)#speed 10
SW1(config-if)#
%LINK-5-CHANGED: Interface FastEthernet0/2, changed state to down
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/2, changed state to down

24) 인터페이스가 여전히 작동하는지 확인합니다.

SW1#show ip interface brief
Interface IP-Address OK? Method Status Protocol
Vlan1 10.10.10.10 YES manual up up
FastEthernet0/1 unassigned YES unset up up
FastEthernet0/2 unassigned YES unset down down

인터페이스 상태는 down/down입니다.

25) R2에서 인터페이스가 작동하는지 확인합니다. 인터페이스의 상태는 어떻습니까?

R2#show ip interface brief
Interface IP-Address
FastEthernet0/0 10.10.10.2

R2의 인터페이스 상태는 up/down입니다.



---

> Source: `section_14/ysj/ref_sec_86_ex_src.md`

14 Cisco 라우터 및 스위치 기본 사항 - 실습 연습

이 실습에서는 스위치에 대한 기본 구성을 완료하고, Cisco Discovery Protocol CDP를 확인하며, 인터페이스 속도 및 이중 구성의 효과를 분석합니다.

실습 토폴로지


시작 구성 로드

Packet Tracer에서 '14 Cisco Router and Switch Basics.pkt' 파일을 열어 실습을 로드합니다.

Cisco 라우터 및 스위치 초기 구성
1) Router 1을 'R1'이라는 호스트 이름으로 구성
2) Router 2를 'R2'라는 호스트 이름으로 구성
3) Switch 1을 'SW1'이라는 호스트 이름으로 구성
4) 토폴로지 다이어그램에 따라 R1의 IP 주소 구성
5) 토폴로지 다이어그램에 따라 R2의 IP 주소 구성
6) SW1에 관리 IP 주소 10.10.10.10/24 부여
7) 스위치는 R2를 통해 다른 IP 서브넷에 연결성을 가져야 함
8) 스위치가 기본 게이트웨이를 ping할 수 있는지 확인
9) 장치를 연결하는 인터페이스에 적절한 설명 입력
10) SW1에서 R1로의 링크에서 속도와 이중 모드가 100 Mbps 전이중으로 자동 협상되는지 확인
11) R2로의 링크에 전이중 및 FastEthernet 속도를 수동으로 구성
12) 스위치가 실행 중인 IOS 버전은 무엇입니까?

CDP 구성
13) Cisco Discovery Protocol을 사용하여 직접 연결된 Cisco 이웃 확인
14) R1이 CDP를 통해 Switch 1에 대한 정보를 발견하지 못하도록 방지
15) 전역 구성 모드에서 'no cdp run' 명령을 입력한 다음 'cdp run' 명령을 입력하여 R1의 CDP 캐시를 플러시
16) R1이 CDP를 통해 SW1을 볼 수 없는지 확인

스위치 문제 해결
17) show ip interface brief 명령으로 R2에 연결된 스위치 포트의 상태를 확인합니다. 상태와 프로토콜이 up/up으로 표시되어야 합니다.
18) R2에 연결된 인터페이스를 종료하고 show ip interface brief 명령을 다시 실행합니다. 상태와 프로토콜이 administratively down/down으로 표시되어야 합니다.
19) 인터페이스를 다시 활성화합니다. 속도와 이중 설정을 확인합니다.

---

> Source: `section_15/ysj/note.md`

## Section 15 정리

#### 부팅 프로세스

- 메모리 종류:
    - ROM (Read Only Memory): 장치가 켜질 때 사용되며, POST(Power On Self Test, 하드웨어 상태 확인) 테스트와 부트스트랩을 담당한다.  IOS 소프트웨어 이미지를 Flash에서 찾고, 실패 시 ROMMON 프롬프트를 보여준다.
    - Flash: IOS 소프트웨어 이미지가 저장되는 장소로, 이동식 CompactFlash 카드로도 사용될 수 있다. 부팅 시 ROM에서 Flash로 부트스트랩이 호출된다.
    - NVRAM (Non-Volatile RAM): startup-config 파일이 저장되어 있으며, 부팅 시 RAM으로 불러와져 실행된다. 이 파일이 없으면 설정 마법사가 호출됩니다. (= 공장초기화 상태이므로)
    - RAM (Random Access Memory): 부팅 중 IOS 이미지와 startup-config가 불러와지는 작업 메모리. 휘발성이기 때문에 전원이 꺼지면 데이터가 사라진다. (의도적으로 롤백?이 쉽도록 이런 구성을 가짐)

- 부팅 과정:
    - 장치 전원이 켜지면 ROM에서 POST 테스트가 실행되고, 부트스트랩이 Flash에서 IOS 이미지를 찾고 로딩한다. (이미지는 압축되어 있음.)
    - IOS는 NVRAM에서 startup-config를 불러와 현재의 running-config로 적용한다.
    - 사용자 설정 변경 시 running-config에 즉시 반영되며, copy running-config startup-config 명령어를 통해 NVRAM에 저장할 수 있다.
- TFTP 서버: 외부 TFTP 서버에서 시스템 이미지나 startup-config를 불러올 수 있지만, 연결이 끊기면 부팅할 수 없으므로 권장되지 않음.

#### 공장 초기화 및 비밀번호 복구

- 공장 초기화 방법
    - 활성화 프롬프트에서 `write erase` 명령 입력 -> `startup-config` 제거됨.
    - 장치 재부팅 후 설정 마법사 실행

- 비밀번호 복구 방법
    - 구성 레지스터 이해
        - 기본 부팅 설정: `0x2102`
        - ROMMON 모드 부팅: `0x2120`
        - NVRAM 무시: `0x2142`
    - 재부팅 시 (주로) Ctrl-Break 조합으로 ROMMON 프롬프트 진입
    - ROMMON에서 `confreg 0x2142` 명령 입력하여 startup-config 무시 설정
    - 장치 재부팅 후 설정 마법사에서 "no" 입력하여 우회
    - `enable` 명령으로 활성화 모드 진입, startup-config를 running-config로 복사
    - 새로운 활성화 비밀번호 설정
    - `config-register 0x2102` 입력하여 정상 부팅 가능하도록 설정
    - `copy run start` 명령으로 변경 사항 저장
    - 내 메모: startup-config에 접속하기 위해 암호가 필요한데, 그걸 우회해서 가져오고, 비밀번호를 새로 설정한다고 보면 됨.
    - 주의 사항
        - startup-config를 running-config로 복사하는 것 잊지 않기
        - 구성 레지스터를 원래 설정으로 되돌리는 것 잊지 않기


#### 시스템 이미지 및 구성의 백업

시스템 이미지(IOS)나 구성(Config)를 백업하는 방법 설명.

- 백업 장소: 외부 FTP, TFTP 서버, USB, 장치의 Flash 메모리에 가능.

- 백업 이유:
    - 시스템 이미지를 TFTP 서버에 백업하면 Cisco 웹사이트에서 다시 다운로드할 필요 없이 복구할 수 있음.
    - 구성 파일을 백업하여 나중에 이전 버전으로 롤백할 수 있음. 단, 파일을 복사하면 병합되므로 아예 교체해야 함.

- 백업 명령어:
    - copy flash tftp: 시스템 이미지를 TFTP 서버에 백업.
    - copy running-config tftp: 실행 중인 구성을 TFTP 서버에 백업.
    - copy startup-config usb: 시작 구성을 USB에 백업.

- 실행 예시:
    - TFTP 서버에 시스템 이미지와 실행 중인 구성 백업 과정 설명.
    - Flash에 백업 후 기존 구성을 복원하는 과정 시연.

- 복원 과정:
    - write erase 명령으로 시작 구성을 삭제한 후, copy flash startup-config 명령으로 백업한 구성 파일을 복원.
    - 재부팅 후 이전 구성이 복원된 상태를 확인.

#### IOS 업그레이드

- 소프트웨어 이미지 다운로드
    - Cisco 웹사이트(https://software.cisco.com)에서 새로운 IOS 소프트웨어 이미지를 다운로드
    - "Software Download" 링크 클릭 후 업그레이드할 장치 모델 검색

- TFTP 서버로 복사
    - 다운로드한 IOS 이미지를 TFTP 서버로 복사
    - TFTP 서버에서 장치의 Flash 메모리로 다운로드

- 기존 이미지 처리
    - Flash에 새로운 이미지 다운로드 후 기존 이미지 삭제 가능
    - 기존 이미지 유지 시 boot system 명령어로 새로운 이미지로 부팅 설정

- 업그레이드 과정 예시
    - 스위치 주소 10.10.10.2에서 TFTP 서버 10.10.10.10의 최신 IOS 이미지 다운로드
    - 현재 실행 중인 소프트웨어 확인: sh flash, sh ver 명령어 사용
    - TFTP 서버에서 최신 이미지(버전 15.0) 선택 후 copy tftp flash 명령어로 다운로드

- 부팅 설정
    - boot system 명령어로 새로운 시스템 이미지 경로 설정
    - copy run start 명령어로 변경 사항 저장 후 reload 명령어로 재부팅
    - 재부팅 후 실행 중인 버전 확인하여 업그레이드 완료 여부 확인

## 리뷰

AI 써서 정리.

나중에도 쓸일이 없는 내용같아서 대충 듣고 넘김.

그나저나 비밀번호 복구 방법에 쓰는 저런걸 보면, 해킹당하기 쉽지 않을까?    
막 영화에서 보는 거처럼 서버 랙에 노트북 연결해가지고 내부 데이터 빼고 그런게 이론상으로는 가능할거같음.

뭔가 이런 강의를 생각한건 아니긴 한데...

일단 끝은 볼 예정.

그래도 맨날 네트워크 인프라를 AWS나 클라우드로만 다루다가, 뭔가 실제로 어떤 식으로 동작하는지 보는거라서 의도치 않게 다른 방향으로 좀 유익한 느낌.



---

> Source: `section_15/ysj/ref_sec_94_answer.md`

답안 키

이 실습에서는 Cisco 라우터에서 공장 초기화, 비밀번호 복구, 구성 백업, 시스템 이미지 백업 및 복구를 수행할 것입니다. 또한 Cisco 스위치에서 IOS 업그레이드를 수행할 것입니다.

공장 초기화

1) R1의 실행 중인 구성을 확인합니다. 호스트 이름과 인터페이스가 구성되어 있음을 주목하세요.
```
R1#sh run
Building configuration...

Current configuration : 696 bytes
!
hostname R1
!
interface GigabitEthernet0/0
ip address 10.10.10.1 255.255.255.0
duplex auto
speed auto
```
2) R1을 공장 초기화하고 재부팅합니다.
```
R1#write erase
Erasing the nvram filesystem will remove all configuration
files! Continue? [confirm]
[OK]
Erase of nvram: complete
%SYS-7-NV_BLOCK_INIT: Initialized the geometry of nvram
R1#reload
Proceed with reload? [confirm]
```
3) 라우터가 부팅되는 동안 부팅 과정을 지켜봅니다.
```
System Bootstrap, Version 15.1(4)M4, RELEASE SOFTWARE (fc1)

Readonly ROMMON initialized

IOS Image Load Test
___________________

Digitally Signed Release Software

Self decompressing the image :
###########################################################
############### [OK]
```
4) 라우터가 설정 마법사로 부팅되어야 합니다. 마법사를 종료한 다음 시작 구성과 실행 중인 구성이 비어 있는지 확인합니다.
```
--- System Configuration Dialog ---

Continue with configuration dialog? [yes/no]: no

Router>enable
Router#show run
Building configuration...
hostname Router
!
interface GigabitEthernet0/0
no ip address
duplex auto
speed auto
shutdown

Router#show start
startup-config is not present
```
5) '15 Cisco Device Management Configs.zip' 파일에서 R1의 구성을 다시 구성에 붙여넣고 저장합니다.
```
Router#configure terminal
Router(config)#hostname R1
R1(config)#!
R1(config)#interface GigabitEthernet0/0
R1(config-if)# ip address 10.10.10.1 255.255.255.0
R1(config-if)# duplex auto
R1(config-if)# speed auto
R1(config-if)# no shutdown
R1(config-if)#!
R1(config-if)#line con 0
R1(config-line)# exec-timeout 30 0
R1(config-line)#end

R1#copy run start
Destination filename [startup-config]?
Building configuration...
[OK]
```
비밀번호 복구

6) R1에서 enable secret을 'Flackbox1'로 설정하고 실행 중인 구성을 저장합니다.
```
R1(config)#enable secret Flackbox1
R1(config)# do copy run start
Destination filename [startup-config]?
Building configuration...
[OK]
R1(config)#
```
7) 적절한 명령을 사용하여 다음 재부팅 시 라우터가 rommon 프롬프트로 부팅되도록 구성하고 라우터를 재부팅합니다.
```
R1(config)#config-register 0x2120
R1(config)#end
R1#reload
Proceed with reload? [confirm]
```
8) rommon 모드에서 라우터가 부팅 시 시작 구성을 무시하도록 구성하고 라우터를 재부팅합니다.
```
rommon 1 > confreg 0x2142
rommon 2 > reset
```
9) 라우터가 설정 마법사로 부팅되어야 합니다. 마법사를 종료합니다.
```
--- System Configuration Dialog ---
Continue with configuration dialog? [yes/no]: no
```
10) 실행 중인 구성과 시작 구성을 보면 어떤 것이 보일 것으로 예상하십니까? 이를 확인하세요.

라우터가 부팅 시 시작 구성을 로드하지 않았기 때문에 실행 중인 구성은 비어 있어야 합니다. 시작 구성은 변경되지 않은 채로 이전의 모든 구성이 여전히 있어야 합니다.
```
Router#sh run
Building configuration...

hostname Router
!
interface GigabitEthernet0/0
no ip address
duplex auto
speed auto

Router#sh start
!
hostname R1
!
enable secret 5 $1$mERr$J2XZHMOgpVVXdLjC9lYtE1
!
interface GigabitEthernet0/0
ip address 10.10.10.1 255.255.255.0
duplex auto
speed auto
```
11) 시작 구성을 실행 중인 구성으로 복사합니다. 이 단계를 놓치지 마세요. 그렇지 않으면 라우터를 공장 초기화하게 됩니다!
```
Router#copy start run
Destination filename [running-config]?
```
12) GigabitEthernet0/0 인터페이스의 상태를 확인합니다. 왜 다운되어 있습니까?
```
R1#show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 10.10.10.1 YES NVRAM administratively down down
GigabitEthernet0/1 unassigned YES NVRAM administratively down down
GigabitEthernet0/2 unassigned YES NVRAM administratively down down
Vlan1 unassigned YES NVRAM administratively down down

R1#show run
! truncated
interface GigabitEthernet0/0
ip address 10.10.10.1 255.255.255.0
duplex auto
speed auto
shutdown
```
라우터 인터페이스는 기본적으로 종료되어 있습니다. 인터페이스의 시작 구성에 'no shutdown'이 명시적으로 나타나지 않기 때문에, 시작 구성이 실행 중인 구성으로 복사될 때 기본값이 적용되어 인터페이스가 종료 상태가 됩니다.

13) GigabitEthernet0/0 인터페이스를 활성화합니다.
```
R1(config)#interface g0/0
R1(config-if)#no shutdown
```
14) enable secret을 제거합니다.
```
R1(config)#no enable secret
```
15) 다음 재부팅 시 라우터가 정상적으로 재부팅되고 라우터에 접근할 수 있도록 합니다.
```
R1(config)#config-register 0x2102
R1(config)#end
R1#copy run start
Destination filename [startup-config]?
Building configuration...
[OK]
```
16) 라우터를 재부팅하고 예상된 구성이 있는지 확인합니다.
```
R1#reload
Proceed with reload? [confirm]

R1>en
R1#show run
Building configuration...
hostname R1
!
interface GigabitEthernet0/0
ip address 10.10.10.1 255.255.255.0
duplex auto
speed auto

R1#sh ip int brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0 10.10.10.1 YES NVRAM up up
GigabitEthernet0/1 unassigned YES NVRAM administratively down down
GigabitEthernet0/2 unassigned YES NVRAM administratively down down
Vlan1 unassigned YES NVRAM administratively down down
```
구성 백업

중요: 파일 이름은 대소문자를 구분합니다 - 정확히 보여진 대로 입력해야 합니다(c2900은 C2900과 다릅니다).

17) R1의 실행 중인 구성을 Flash에 백업합니다. 백업 파일에 적절한 이름을 사용하세요. 구성이 백업되었는지 확인합니다.
```
R1#copy run flash
Destination filename [running-config]? Backup-1
Building configuration...
[OK]

R1#show flash

System flash directory:
File Length Name/status
5 728 Backup-1
3 33591768 c2900-universalk9-mz.SPA.151-4.M4.bin
2 28282 sigdef-category.xml
1 227537 sigdef-default.xml
[33848315 bytes used, 221895685 available, 255744000 total]
249856K bytes of processor board System flash (Read/Write)
```
18) R1 시작 구성을 TFTP 서버에 백업합니다. 백업 파일에 적절한 이름을 사용하세요. 구성이 백업되었는지 확인합니다.
```
R1#copy start tftp
Address or name of remote host []? 10.10.10.10
Destination filename [R1-confg]? Backup-2
Writing startup-config....!!
[OK - 698 bytes]
698 bytes copied in 3.007 secs (242 bytes/sec)
```
IOS 시스템 이미지 백업 및 복구

19) R1의 IOS 시스템 이미지를 TFTP 서버에 백업합니다. 구성이 백업되었는지 확인합니다.
```
R1#show flash

System flash directory:
File Length Name/status
5 728 Backup-1
3 33591768 c2900-universalk9-mz.SPA.151-4.M4.bin
2 28282 sigdef-category.xml
1 227537 sigdef-default.xml
[33848315 bytes used, 221895685 available, 255744000 total]
249856K bytes of processor board System flash (Read/Write)

R1#copy flash tftp
Source filename []? c2900-universalk9-mz.SPA.151-4.M4.bin
Address or name of remote host []? 10.10.10.10
Destination filename [c2900-universalk9-mz.SPA.151-
4.M4.bin]?

Writing c2900-universalk9-mz.SPA.151-
4.M4.bin...!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
[OK - 33591768 bytes]
```
IOS 이미지 복구

20) Flash에서 시스템 이미지를 삭제하고 재부팅합니다.

```
R1#delete flash:c2900-universalk9-mz.SPA.151-4.M4.bin
Delete filename [c2900-universalk9-mz.SPA.151-4.M4.bin]? 
Delete flash:/c2900-universalk9-mz.SPA.151-4.M4.bin? 
[confirm]

R1#reload
Proceed with reload? [confirm]
Boot process failed... 
The system is unable to boot automatically. The BOOT 
environment variable needs to be set to a bootable 
image. 
rommon 1 >
```

21) 인터넷 검색을 사용하여 라우터 모델에 대한 시스템 복구 지침을 찾습니다. TFTP 서버를 사용하여 시스템 이미지를 복구합니다.

```
http://www.cisco.com/c/en/us/td/docs/routers/access/1900/software/configuration
/guide/Software_Configuration/appendixCrommon.html은 'Cisco 2900 rommon recovery'를 검색할 때 첫 번째 결과입니다.
```

“Recovering the System Image (tftpdnld)” 섹션으로 이동합니다.

'tftpdnld' 명령에는 rommon 모드에서 명령을 입력할 때 표시되는 내장 도움말이 있습니다:

```
rommon 1 > tftpdnld

Missing or illegal ip address for variable IP_ADDRESS 
Illegal IP address.

usage: tftpdnld 
Use this command for disaster recovery only to recover an image via 
TFTP. 
Monitor variables are used to set up parameters for the transfer. 
(Syntax: "VARIABLE_NAME=value" and use "set" to show current 
variables.) 
"ctrl-c" or "break" stops the transfer before flash erase begins.

The following variables are REQUIRED to be set for tftpdnld: 
IP_ADDRESS: The IP address for this unit 
IP_SUBNET_MASK: The subnet mask for this unit 
DEFAULT_GATEWAY: The default gateway for this unit 
TFTP_SERVER: The IP address of the server to fetch from 
TFTP_FILE: The filename to fetch 

The following variables are OPTIONAL: 
TFTP_VERBOSE: Print setting. 0=quiet, 1=progress(default), 2=verbose 
TFTP_RETRY_COUNT: Retry count for ARP and TFTP (default=7) 
TFTP_TIMEOUT: Overall timeout of operation in seconds (default=7200)
```

이 구성에는 모두 대문자를 사용하세요:

```
rommon 2 > IP_ADDRESS=10.10.10.1 
rommon 3 > IP_SUBNET_MASK=255.255.255.0 
rommon 4 > DEFAULT_GATEWAY=10.10.10.1 
rommon 5 > TFTP_SERVER=10.10.10.10 
rommon 6 > TFTP_FILE=c2900-universalk9-mz.SPA.151-4.M4.bin 
rommon 7 > tftpdnld 

IP_ADDRESS: 10.10.10.1 
IP_SUBNET_MASK: 255.255.255.0 
DEFAULT_GATEWAY: 10.10.10.1 
TFTP_SERVER: 10.10.10.10 
TFTP_FILE: c2900-universalk9-mz.SPA.151-4.M4.bin 
Invoke this command for disaster recovery only.
WARNING: all existing data in all partitions on flash will be lost! 

Do you wish to continue? y/n: [n]: y
```

**IOS 이미지 업그레이드**

22) SW1이 C2960 소프트웨어(C2960-LANBASE-M), 버전 12.2(25)FX를 실행하고 있는지 확인합니다.

```
SW1#sh version
Cisco IOS Software, C2960 Software (C2960-LANBASE-M), Version 12.2(25)FX
```

23) TFTP 서버를 사용하여 c2960-lanbasek9-mz.150-2.SE4.bin으로 업그레이드합니다.

```
SW1#copy tftp flash
Address or name of remote host []? 10.10.10.10
Source filename []? c2960-lanbasek9-mz.150-2.SE4.bin
Destination filename [c2960-lanbasek9-mz.150-2.SE4.bin]? 

Accessing tftp://10.10.10.10/c2960-lanbasek9-mz.150-
2.SE4.bin.... 
Loading c2960-lanbasek9-mz.150-2.SE4.bin from 10.10.10.10:
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
[OK - 4670455 bytes] 

4670455 bytes copied in 3.086 secs (121674 bytes/sec)

SW1#show flash
Directory of flash:/ 

1 -rw- 4414921 <no date> c2960-lanbase-mz.122-25.FX.bin
3 -rw- 4670455 <no date> c2960-lanbasek9-mz.150-2.SE4.bin
2 -rw- 1054 <no date> config.text 

64016384 bytes total (54929954 bytes free) 

SW1#config t
SW1(config)#boot system c2960-lanbasek9-mz.150-2.SE4.bin
SW1(config)#end
SW1#copy run start
```

24) 재부팅하고 스위치가 새 소프트웨어 버전을 실행하고 있는지 확인합니다.

```
SW1#reload
Proceed with reload? [confirm] 

SW1#show version
Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.0(2)SE4, RELEASE SOFTWARE (fc1)
```



---

> Source: `section_15/ysj/ref_sec_94_ex_src.md`

이 실습에서는 Cisco 라우터에서 공장 초기화, 비밀번호 복구, 구성 백업, 시스템 이미지 백업 및 복구를 수행합니다. 또한 Cisco 스위치에서 IOS 업그레이드를 수행합니다.

Cisco Packet Tracer를 이 실습에 사용하세요. 토폴로지 다이어그램에 표시된 Packet Tracer의 일반 서버에는 내장된 TFTP 서버가 있습니다.

![토폴로지 다이어그램]

공장 초기화
R1의 실행 중인 구성을 확인합니다. 호스트 이름과 인터페이스가 구성되어 있음을 확인하세요.

R1을 공장 초기화하고 재부팅합니다.

라우터가 부팅되는 과정을 지켜봅니다.

라우터가 설정 마법사로 부팅되어야 합니다. 마법사를 종료하고 시작 및 실행 구성이 비어 있는지 확인합니다.

'15 Cisco Device Management Configs.zip' 파일에서 R1의 구성을 다시 붙여넣고 저장합니다.

비밀번호 복구
R1에 enable secret 'Flackbox1'을 설정하고 실행 중인 구성을 저장합니다.

적절한 명령어로 라우터가 다음 재부팅 시 rommon 프롬프트로 부팅되도록 구성하고 라우터를 재부팅합니다.

rommon 모드에서 라우터가 부팅 시 시작 구성을 무시하도록 구성하고 라우터를 재부팅합니다.

라우터가 설정 마법사로 부팅되어야 합니다. 마법사를 종료합니다.

실행 중인 구성과 시작 구성을 보면 어떤 내용이 표시될 것으로 예상하십니까? 이를 확인하세요.

시작 구성을 실행 중인 구성으로 복사합니다. 이 단계를 놓치지 마세요. 그렇지 않으면 라우터가 공장 초기화됩니다!

GigabitEthernet0/0 인터페이스의 상태를 확인합니다. 왜 다운 상태입니까?

GigabitEthernet0/0 인터페이스를 활성화합니다.

enable secret을 제거합니다.

다음 재부팅 시 라우터가 정상적으로 부팅되고 접근할 수 있도록 합니다.

라우터를 재부팅하고 예상된 구성이 있는지 확인합니다.

구성 백업
중요: 파일 이름은 대소문자를 구분합니다 - 정확히 표시된 대로 입력해야 합니다(c2900은 C2900과 다릅니다).

R1의 실행 중인 구성을 플래시에 백업합니다. 백업 파일에 적절한 이름을 사용하세요. 구성이 백업되었는지 확인합니다.

R1 시작 구성을 TFTP 서버에 백업합니다. 백업 파일에 적절한 이름을 사용하세요. 구성이 백업되었는지 확인합니다.

IOS 시스템 이미지 백업 및 복구
R1의 IOS 시스템 이미지를 TFTP 서버에 백업합니다. 구성이 백업되었는지 확인합니다.

플래시에서 시스템 이미지를 삭제하고 재부팅합니다.

인터넷 검색을 사용하여 라우터 모델에 대한 시스템 복구 지침을 찾습니다. TFTP 서버를 사용하여 시스템 이미지를 복구합니다.

IOS 이미지 업그레이드
SW1이 C2960 Software (C2960-LANBASE-M), Version 12.2(25)FX를 실행 중인지 확인합니다.

TFTP 서버를 사용하여 c2960-lanbasek9-mz.150-2.SE4.bin으로 업그레이드합니다.

재부팅하고 스위치가 새로운 소프트웨어 버전을 실행 중인지 확인합니다.

---

> Source: `section_16/ysj/note.md`

## Section 16 정리

#### GPT 요약

https://chatgpt.com/share/67205e57-bcfc-8008-8e0e-ba572645db4b 

#### 정리

- 라우터의 역할 
    1. 패킷을 보내는 최적의 경로을 결정하는 것.
    2. 네트워크로 트래픽을 전송하는 것.

- 라우터는 라우터 표를 보고 라우팅을 결정한다.
    - 각 라우터는 연결된 라우터만 볼 수 있으므로, 특정 경로를 위해서 전달해야 하는 라우터 정보를 저장해놓는다.
    - e.g. `r1 <-> r2 <-> r3` r3 입장에서 r1으로 보내려면 r2로 보내야 하므로, r3는 r1가 목적지인 경우 r2로 보내도록 표가 작성되어야 한다.
    - 라우터 표에는 효율적인 경로가 지정된다. (가능한 모든 경로가 아닌)
- [show ip route 명세](https://www.cisco.com/E-Learning/bulk/public/tac/cim/cib/using_cisco_ios_software/cmdrefs/show_ip_route.htm)
    - `ip address [라우터의 인터페이스의 식별 IP] [서브넷 마스크]`
    - `ip route [목적지 네트워크] [서브넷 마스크] [다음 홉 IP 주소]`
- 경로 유형 - Cisco 장치 기준
    - 로컬: 다른 라우터를 통할 필요 없이 본인이 처리 가능한 서브넷
    - 연결된 경로: 실제로 연결된 기기의 IP
    - 정적: 네트워크 관리자가 직접 정한 서브넷 - from, to가 명시되는 형식
    - 동적: 다음 섹션에서 다룸.
    - 그 외
- 경로 요약, 기본 경로, 부하 분산
    - 요약 경로(더 넒은 범위의 서브넷)를 사용해 관리 오버헤드와 라우터의 메모리를 아낄 수 있음. 중복의 경우 구체적인 경로를 선택하는 Longest Prefix Match가 발생한다. 
    - 기본 경로: 따로 지정되지 않은 경우, 전달되는 경로
        - 기본 게이트웨이로 나머지 트래픽을 보낼 때 유용하다. 
    - 기본 게이트웨이: 네트워크 트래픽을 처리하는 라우터
        - 할당받은 IP로 나머지 트래픽을 보내거나 인터넷으로부터 트래픽을 받는다. 
        - NAT에서 주로 사용하나, NAT에서만 사용되는 건 아님.
    - 부하 균형(Load Balancing): 전송 가능한 경로가 2개 이상인 경우, 트래픽을 나눠서 보낸다. (그러나 해싱을 사용해서 전송, 목적 호스트가 동일한 경우 연결이 끊이지 않도록한다.)
- 프로코콜
    - ping: 두 호스트 간의 연결이 정상임을 확인. 서로 패킷을 주고 받을 수 있는 (양방향) 상태 임을 확인.
        - ARP 등의 이유로 종종 실패할수도 있음.
    - trace: 패킷이 전달되는 라우터 간의 연결 경로를 확인할 수 있음.



---

> Source: `section_17/ysj/note.md`

## Section 17 정리

#### GPT

- https://chatgpt.com/share/6721aafa-7108-8008-b01e-75081fe57b39 - 105~110
- https://chatgpt.com/share/67223c0a-e678-8009-933b-75d9ad44db0b - 111~118

#### 동적 라우팅 프로토콜

라우터는 다양한 방법으로 경로를 학습합니다:
- IP 주소 설정: 관리자가 인터페이스에 IP 주소를 설정합니다.
- 정적 경로 설정: 관리자가 라우터에 정적 경로를 설정하여 특정 네트워크로의 경로를 수동으로 추가합니다.
- 라우팅 프로토콜: 이웃 라우터로부터 라우팅 프로토콜을 통해 경로를 수신합니다.
    - 라우팅 테이블을 경로로 가능 가장 효율적인 경로를 기억함. (가장 효율적인게 여러개일 수 있음.)

- 동적 라우팅 프로토콜
    - 요약 경로: 요약 경로를 사용하면 라우팅 테이블을 적게 사용하므로 메모리 효율이 좋고, 구체적인 변화에 수정이 필요하지 않으므로 CPU(및 처리자원)를 적게 씀.
    - 라우터 간 상태 변화 반응: 경로에 변화가 생기면 라우팅 테이블을 변화시킴.
    - 동적 라우팅 프로토콜 vs 정적 경로
        - 정적 경로는 관리가 따다로우므로, 일부 백업 경로, 인터넷 연결 등의 용도로 제한적으로 사용.
        - 동적으로 효율적인 구성을 유지하므로 네트워크 관리 부하가 줄어듦.

- 라우팅 프로토콜 종류
    - IGP (Internal Gateway Protocol): 조직 내부에서의 라우팅을 위해 사용됩니다.
    - EGP (External Gateway Protocol): 조직 외부, 인터넷을 통한 라우팅에 사용됩니다. EGP는 **BGP (Border Gateway Protocol)**가 유일하며, 여러 조직 간 경로를 통보하고 최적의 경로를 선택합니다.
    - IGP 종류
        - 거리 벡터 라우팅 프로토콜: RIP, EIGRP
            - 인접 라우터의 관점에서 경로 정보가 전달됩니다.
            - 제한된 범위의 정보만 제공되며, 다른 라우터들의 전체 구조를 알지 못합니다.
        - 링크 상태 라우팅 프로토콜: OSPF, IS-IS
            - 라우터는 영역 내 모든 라우터와 그들의 링크 상태 정보를 학습합니다.
            - 영역 내의 모든 라우터와 링크 정보를 확인할 수 있습니다.
    - 관련 링크
        - https://www.gns3network.com/dynamic-routing-complete-guide-for-beginner-and-expert/
        - https://community.cisco.com/t5/networking-knowledge-base/dynamic-routing-protocols-ospf-eigrp-ripv2-is-is-bgp/ta-p/4511577

- 라우팅 프로토콜 메트릭과 관리 거리
    - 메트릭
        - 같은 프로토콜에서 특정 경로까지 가는데 드는 비용
        - 라우팅 프로토콜은 주로 홉 수나 대역폭을 기준으로 메트릭 값을 사용해 최적의 경로를 선택합니다.
    - 관리 거리(Administrative Distance, AD)
        - 여러 라우팅 프로토콜이 동시에 활성화되어 동일 목적지로 향하는 경로를 제공하는 경우, 프로토콜 간 메트릭 값은 서로 비교할 수 없기 때문에 관리 거리가 필요합니다.
        - 관리 거리는 라우팅 프로토콜의 신뢰도를 나타내며, 값이 낮을수록 더 신뢰할 수 있는 프로토콜로 간주됩니다. 예를 들어, 직접 연결된 경로의 관리 거리는 0, 정적 경로는 1, OSPF는 110, RIP는 120입니다. 
        - 필요에 따라 비고정 특정 경로를 백업 경로로 설정할 수 있습니다. 예를 들어, 정적 경로의 AD 값을 라우팅 프로토콜의 AD 값보다 높게 설정하여 주 경로가 끊어졌을 때에만 백업 경로로 전환되도록 구성할 수 있습니다.

- 최적 경로 결정 기준과 등가 다중 경로
    - 최적 경로 결정 기준: - 우선순위별로
        - 가장 긴 접두사(Longest Prefix Match): 가장 구체적인 경로를 우선적으로 선택합니다.
        - 관리 거리 (Administrative Distance, AD): 값이 낮을수록 우선 순위가 높습니다.
        - 메트릭: 경로의 비용으로, 역시 낮은 값이 우선합니다.
    - 등가 다중 경로(ECMP, Equal-Cost Multi-Path) 라우팅 
        - 여러 경로가 동일한 메트릭 값을 가질 때 라우터가 이러한 경로를 라우팅 테이블에 모두 추가하여 부하를 분산시키는 방식.
        - IGP (Interior Gateway Protocol) 라우팅 프로토콜(RIP, IS-IS, EIGRP, OSPF 등)이 기본적으로 등가 다중 경로 라우팅을 지원하며, 이들 프로토콜을 통해 같은 목적지로 가는 여러 경로를 학습하게 됩니다.
        - 부하 분산: 동일한 목적지로 트래픽을 보낼 때 여러 경로로 분산합니다. 이를 통해 네트워크의 효율성을 높이고 혼잡을 줄일 수 있습니다.
        - 정적 경로 부하 분산: 두 개 이상의 정적 경로를 설정하여 부하를 분산할 수 있습니다. 단, 모든 경로가 동일한 서브넷 및 마스크를 가지면서 다른 다음 홉을 지정해야 합니다.
        - 흐름 기반 부하 분산: 동일한 트래픽 흐름은 항상 동일한 경로를 따라가며, 라운드 로빈 방식으로 패킷을 전송하지 않습니다. 이는 패킷 지연 및 순서 문제를 방지하고 안정성을 높이기 위함입니다.



- 루프백 인터페이스
    - 루프백 인터페이스는 물리적인 장애 없이 항상 활성화된 상태로, 라우터와 스위치에 IP 주소를 할당하는 논리적 인터페이스입니다.
    - 루프백 인터페이스는 소프트웨어적으로 구현된 가상 인터페이스로, 항상 활성화 상태입니다.
    - 루프백 주소는 일반적으로 /32 서브넷 마스크(255.255.255.255)로 구성되며, 고정된 관리 IP 주소를 통해 여러 경로를 사용하는 경우에도 유연성을 제공합니다. 이로 인해 관리와 트래픽 경로 다중화에 매우 유용합니다.
    - 인터페이스의 서브넷: 라우터의 각 물리적 인터페이스 (예: FastEthernet/0/1, FastEthernet/0/2 등)는 서로 다른 서브넷에 할당될 수 있습니다. 루프백 인터페이스는 이러한 물리적 인터페이스와는 다르게, 주로 장비 자체의 IP 스택과 통신할 때 사용됩니다.
    - 접근성 및 장애 대응: 루프백 인터페이스는 실제 물리적 인터페이스가 작동하지 않더라도 항상 접근 가능하다는 장점이 있습니다. 따라서 라우터의 특정 물리적 인터페이스(FE/01)가 문제가 생길 경우에도, 루프백 인터페이스를 통해 해당 라우터의 서비스를 사용할 수 있습니다. 이는 특히 네트워크 관리 및 모니터링, 그리고 원격 접속에서 유용합니다.
    - IP 주소의 일관성: 루프백 인터페이스는 항상 동일한 IP 주소를 가지므로, 애플리케이션이나 프로세스가 루프백 인터페이스를 통해 통신할 때, IP 주소가 변경되지 않아 안정적인 연결을 유지할 수 있습니다.
    - (추가) 내가 알기로는 HOST(우리 노트북 같은거)에서 자신의 장치 내에서 테스트 및 통신을 위한 용도로 사용된다고 알고 있었는데, (127.0.0.1, ::1) 네트워크 상에서는 별도 라우터와 연결된 HOST 없이, HOST처럼 사용하는 가상 IP 같은 느낌인듯? 그럼 별도 HOST없이도 바로 라우터에 뭔가 보낼 수 있게 되니까.
    - 다음과 같이 사용 가능
        - `interface loopback0`, `ip address 192.168.1.1 255.255.255.0` -> 루프백 인터페이스 loopback0에 IP 주소 192.168.1.1을 할당.
        - 루프백 인터페이스에 설정된 IP는 항상 활성화되어 있어, 네트워크 장비의 테스트 및 원격 관리에 유용하게 사용됩니다. 예를 들어, 네트워크 모니터링 도구는 루프백 인터페이스를 통해 장비의 상태를 확인하고, 문제를 진단할 수 있습니다.
    - 장점
        - 신뢰성: 루프백 인터페이스는 항상 활성 상태를 유지하므로, 물리적인 인터페이스가 다운되거나 문제가 생기더라도 루프백 IP 주소를 통해 통신이 가능해집니다. 따라서 네트워크 장비의 주소가 변경되지 않아, 안정적인 접속을 보장합니다.
        - 간편한 관리: 특정 라우터에 접속된 호스트가 아닌 루프백 인터페이스로 직접 통신할 수 있기 때문에, 관리자가 장비에 접근하는 방법이 단순해집니다. 예를 들어, 여러 개의 물리적 인터페이스가 있는 경우에도 루프백 주소를 통해 동일한 방식으로 접속할 수 있습니다.
        - 테스트 및 진단: 루프백 인터페이스는 장비의 상태를 테스트하거나 네트워크 서비스를 진단하는 데 유용합니다. 예를 들어, 라우터의 루프백 IP로 Ping을 보내면 해당 장비가 정상적으로 작동하고 있는지 확인할 수 있습니다.
        - 라우팅 프로토콜: 루프백 인터페이스는 동적 라우팅 프로토콜에서도 중요한 역할을 합니다. 예를 들어, OSPF와 같은 프로토콜에서는 루프백 인터페이스를 사용해 라우터 ID를 설정하거나, 안정적인 경로를 제공하는 데 활용할 수 있습니다.


- 인접성과 수동 인터페이스
    - 인접성(Adjacency): 인접성은 두 라우터 간의 연결 상태를 나타내며, 이들은 서로 직접적으로 통신할 수 있는 상태입니다. 인접성을 형성하려면 다음과 같은 과정이 필요합니다:
        1. 라우팅 프로토콜 활성화: 두 라우터의 인터페이스에서 동일한 라우팅 프로토콜(RIP, EIGRP, OSPF 등)이 활성화되어야 합니다.
        2. Hello 패킷 전송: 라우터는 Hello 패킷을 주기적으로 전송하여 상대 라우터를 탐색합니다.
        3. 인접성 형성: Hello 패킷을 통해 서로를 인식하고, 통신을 위한 인접성이 형성됩니다.
        4. 라우팅 정보 교환: 인접성이 형성된 후, 라우터들은 라우팅 테이블을 업데이트하기 위해 라우팅 정보를 교환합니다.
    - 수동 인터페이스 (Passive Interface): 수동 인터페이스는 특정 라우터 인터페이스에서 라우팅 프로토콜의 활성화를 막고, 해당 인터페이스를 통해 라우팅 업데이트를 전송하지 않도록 설정하는 것을 의미합니다. 수동 인터페이스의 필요성은 다음과 같습니다:
        1. 보안 강화: 수동 인터페이스를 사용하면 특정 라우터에 대한 내부 정보를 외부로 전송하지 않으므로, 보안 위협을 줄일 수 있습니다. 예를 들어, 협력사와의 연결이 필요하지만 내부 정보를 공유하고 싶지 않을 때 유용합니다.
        2. 자원 효율성: 수동 인터페이스는 Hello 패킷을 전송하지 않기 때문에 자원을 절약할 수 있습니다. 물리적으로 연결되어 있지 않은 루프백 인터페이스와 같은 논리적 인터페이스에 대해 수동으로 설정하면, 자원을 낭비하지 않고 필요한 경로 정보만 학습할 수 있습니다.
        3. 경로 학습: 수동 인터페이스를 통해 내부 라우터들은 외부로의 업데이트 없이도 경로 정보를 학습할 수 있습니다. 예를 들어, 특정 서브넷의 경로는 알리되, 그 경로로 향하는 패킷은 전송하지 않도록 할 수 있습니다.
        - 관련 링크
            - https://www.cisco.com/c/en/us/support/docs/ip/enhanced-interior-gateway-routing-protocol-eigrp/13675-16.html
            - passive-interface로 IP A를 설정하면, 외부에서 IP A를 볼 수는 있으나, 내부 경로를 알려주지는 않음.






---

> Source: `section_18/ysj/note.md`

## Section 18 정리

#### 기본 연결성 문제 해결 - GPT

- Ping: ICMP 프로토콜을 사용해 목적지의 연결성을 확인합니다. ICMP 에코 요청을 보내고 회신을 받으면, 양방향 연결이 가능함을 의미합니다. Cisco 라우터에서 핑 성공 시 느낌표가, 실패 시 마침표나 "U"(도달 불가) 등이 표시됩니다. 확장된 핑 명령어(extended ping, cisco ios만 지원)로 특정 출발지 IP 주소에서 핑을 보낼 수 있어 문제 해결 시 유용합니다.

- Traceroute: 트래픽이 네트워크를 통과하는 경로를 확인하며, TTL 값을 1씩 증가시키며 목적지까지의 각 홉을 추적합니다. 이는 루프 방지에도 유용하며, 경로 상의 문제 지점을 빠르게 파악할 수 있습니다.

- 추가 문제 해결 툴 요약:
    - 1계층: show ip interface brief, show interface 명령어로 인터페이스 상태 점검.
    - 2계층: show arp, show mac address-table 명령어로 MAC 주소 테이블 및 ARP 정보 확인.
    - 4계층: 텔넷(telnet)으로 포트 응답 확인.
    - DNS: nslookup으로 DNS 서버의 이름 변환 기능 확인.

#### 추가 정리

- ping은 ICMP 프로토콜, traceroute은 구현에 따라 UDP나 ICMP가 쓰인다고 함.
- TTL이 있는 이유는 루프 방지를 위해서임.
- Traceroute는 일반 핑처럼 동작하지만 목적지에 닿을 때까지 TTL을 1부터 늘려가면서 각 패킷의 경로(홉)를 추적하는 식으로 동작함. TTL이 0이 되는 경우, 시간 만료 응답을 보내는데, 그 요청을 통해서 해당 hop을 파악하고, 이걸 반복해서 경로를 추적함.
- 시스코 링크: https://www.cisco.com/c/ko_kr/support/docs/ios-nx-os-software/ios-software-releases-121-mainline/12778-ping-traceroute.html



---

> Source: `section_19/ysj/note.md`

## Section 19 정리

#### GPT

- https://chatgpt.com/share/6722b884-3244-8009-a3a5-b12055d9e08b

#### IGP 내부 게이트웨이 프로토콜의 기초

~~나에게는 너무 구체적이라 쓸 일 없는 내용이라 GPT로 요약하고 따로 정리 안함.~~



RIP와 EIGRP의 주요 특징과 설정을 체계적으로 비교/정리해드리겠습니다:

- **RIP (Routing Information Protocol)**
  - 특징
    - 거리 벡터 라우팅 프로토콜
    - 최대 홉 카운트 15로 제한 (확장성 제한)
    - 소규모 네트워크에 적합 - 실제론 테스트나 정말 소규모 아니면 거의 사용 안함.
  - 버전별 특징
    - RIPv1
      - 브로드캐스트 방식 (30초마다)
      - VLSM 미지원
      - 레거시 프로토콜
    - RIPv2
      - 멀티캐스트(224.0.0.9) 사용
      - VLSM 지원
      - 인증 기능 제공
  - 기본 설정
    ```
    router rip
    version 2
    network 10.0.0.0
    no auto-summary
    ```

- **EIGRP (Enhanced Interior Gateway Routing Protocol)**
  - 특징
    - Cisco 전용 프로토콜 - 현재는 개방형 표준이나, 타 사의 지원이 적음.
    - 빠른 수렴 지원
    - 제한된 업데이트로 효율적
    - 멀티캐스트 사용
    - 최대 4개 경로 부하 분산

  - AS 번호와 피어링
    - AS 번호로 구분 (같은 번호만 피어링)
    - 예: `router eigrp 100`
    - Network 명령어로 피어링 설정

  - 라우터 ID
    - 수동 설정 또는 자동 선택
    - 루프백 > 물리 인터페이스 순
    - 예: `eigrp router-id 1.1.1.1`

- **공통 검증 명령어**
  - `show ip protocols`: 프로토콜 설정 확인
  - `show ip route`: 라우팅 테이블 확인
  
- **주요 차이점**
  - 확장성: EIGRP > RIP
  - 구성 복잡도: RIP < EIGRP
  - 수렴 속도: EIGRP > RIP
  - 표준화: RIP(표준) vs EIGRP(Cisco 전용)
  - 부하 분산: EIGRP만 가능
  - 네트워크 크기: RIP(소규모), EIGRP(중대형)

---

> Source: `section_20/ysj/note.md`

## Section 20 정리

### OSPF의 특징 및 RIP, EIGRP와의 비교

1. **OSPF(Open Shortest Path First)란?**
   - **링크 상태 라우팅 프로토콜**로, 네트워크 내 모든 경로 정보를 사용하여 최적의 경로를 찾음.
   - **데이크스트라의 최단 경로 알고리즘**을 사용하여 최적 경로 산출.

2. **OSPF의 장점**
   - **확장성**: 대형 네트워크에 적합함.
   - **빠른 수렴 속도**: 네트워크 변화에 빠르게 반응.
   - **멀티캐스트 기반 메시지 전송**: 브로드캐스트가 아닌 멀티캐스트를 통해 효율적인 데이터 전송.
   - **개방형 표준**: 모든 제조업체의 장치에서 사용 가능, 다양한 장비와 호환됨.

3. **RIP과 EIGRP와의 비교**
   - **RIP**:
     - **거리 벡터 라우팅 프로토콜**로 단순하지만 확장성에 한계가 있음.
     - **소규모 네트워크**나 **테스트 환경**에 적합.
     - **프로덕션 네트워크**에는 거의 사용되지 않음.
   - **EIGRP**:
     - **Cisco 전용**으로 시작했으나 최근 **개방형 표준**이 됨.
     - **구현 및 문제 해결**이 OSPF보다 간단하지만, 여전히 Cisco 장비에 제한적으로 사용.
     - 다양한 제조업체 장치를 사용할 경우, **OSPF가 더 적합**.

4. **OSPF의 주요 작동 방식**
   1. **Hello 패킷**: 인접 라우터 식별 및 인접성 형성.
   2. **DBD (Database Description)**: 네트워크 정보 교환.
   3. **LSR (Link State Request)** & **LSA (Link State Advertisement)**: 누락된 정보 요청 및 회신.
   4. **LSU (Link State Update)**: 네트워크 변화(새 링크 추가, 링크 다운 등) 정보를 플러딩.
   5. **LSAck (Link State Acknowledgment)**: 패킷 수신 확인을 통해 신뢰성 확보.


### Cisco 라우터에서 OSPF 기본 설정 방법

1. **OSPF 활성화**
   - **명령어**: `router ospf [프로세스 ID]`
   - 예: `router ospf 1`
   - **프로세스 ID**: 로컬에서만 중요하며, 인접 라우터와 일치할 필요 없음. 하나의 라우터에서 여러 프로세스 ID 사용 가능하지만, 일반적으로 하나만 사용함.

2. **네트워크 설정**
   - **명령어 형식**: `network [네트워크 주소] [와일드카드 마스크] area [영역 번호]`
   - 예: `network 10.0.0.0 0.0.255.255 area 0`
   - **와일드카드 마스크**:
     - 서브넷 마스크와 반대로 계산됨 (예: 서브넷 마스크 255.255.0.0 ➔ 와일드카드 마스크 0.0.255.255)
     - **계산 방법**: 각 옥텟을 255에서 빼서 구함.
   - **영역**: 모든 네트워크가 작은 네트워크인 경우 `area 0`에 할당 가능. 영역은 이후 강의에서 자세히 설명.

3. **OSPF 설정 예시**
   - **목표**: R1의 일부 인터페이스에서만 OSPF 활성화
   - 설정 예:
     - `network 10.0.0.0 0.0.255.255 area 0`
   - **결과**: 10.0으로 시작하는 IP 주소를 가진 인터페이스(FastEthernet1/0, FastEthernet2/0)에만 OSPF 활성화됨. 10.1로 시작하는 FastEthernet0/0은 제외.

4. **OSPF 설정 확인**
   - `show run | section ospf`: OSPF 설정된 모든 명령어 확인.
   - `show ip protocols`: 실행 중인 라우팅 프로토콜 및 프로세스 ID 확인.
   - `show ip ospf interface brief`: OSPF 활성화된 인터페이스 목록과 관련 정보 확인.

5. **OSPF 상태 확인 및 문제 해결**
   - `show ip ospf neighbor`: 인접 라우터와 인접성이 형성되었는지 확인.
   - `show ip ospf database`: OSPF 링크 상태 데이터베이스 확인.
   - `show ip route`: 라우팅 테이블에서 OSPF 경로가 학습되었는지 확인.

OSPF의 기본 설정 절차는 위와 같습니다. OSPF 설정 후, 인접성을 확인하고 예상 경로가 라우팅 테이블에 포함되었는지 검증하는 것이 중요합니다. 

### Cisco 라우터에서 OSPF 고급 설정 방법

1. **라우터 ID 설정**
   - **기본 설정**: 라우터는 OSPF 라우터 ID로 루프백 인터페이스 중 가장 높은 IP 주소를 사용하며, 루프백이 없으면 가장 높은 IP 주소를 사용. - 수동이나 루프백 주소를 사용하는걸 권장.
   - **루프백의 장점**: 루프백은 항상 활성 상태이므로 라우터 ID가 안정적으로 유지됨.
   - **수동 설정**:
     - 명령어: `router ospf [프로세스 ID]`, 그 후 `router-id [ID]`로 라우터 ID 수동 지정.
     - **주의**: 수동 설정 후 라우터 ID를 즉시 반영하려면 OSPF 프로세스를 재시작하거나 라우터를 재부팅해야 함.
   - **확인 명령어**: `show ip protocols` 또는 `show ip ospf`로 현재 라우터 ID 확인.

2. **수동 인터페이스(Passive Interface) 설정**
   - **설명**: 수동 인터페이스는 OSPF에서 광고되지만, 인접성 형성을 시도하지 않아 보안 및 효율성 향상.
   - **적용 예시**:
     - 루프백 인터페이스: 수동으로 설정해 인접성 형성을 방지.
     - 외부와 연결된 인터페이스(예: FastEthernet2/0): 보안 목적상 수동 인터페이스로 설정.
   - **설정 방법**:
     - 개별 설정: `router ospf [프로세스 ID]` 입력 후, `passive-interface [인터페이스]`.
     - 모든 인터페이스 기본 수동 설정: `passive-interface default` 후 필요한 활성 인터페이스에 대해 `no passive-interface [인터페이스]`.
   - **확인 명령어**: `show ip ospf interface` 또는 `show ip protocols`.

3. **기본 경로(Default Route) 주입**
   - **목적**: 네트워크 전체에 기본 경로를 동적으로 배포하여, 모든 라우터가 외부 네트워크로 접근할 수 있도록 설정.
   - **구성 예시**:
     - R4에 인터넷 연결이 있는 경우: `ip route 0.0.0.0 0.0.0.0 [다음 홉 주소]`로 기본 경로 설정.
     - R4의 OSPF 프로세스에 기본 경로 주입: `default-information originate` 명령어 사용.
   - **경로 확인**: 다른 라우터에서 `show ip route`로 OSPF를 통해 기본 경로가 학습되었는지 확인. 외부 경로로 나타남.
   - **외부 경로의 의미**: 외부 경로는 조직 외부에서 유입된 것이 아닌, 다른 소스에서 OSPF로 재분배된 경로를 의미.


### OSPF 영역(OSPF Areas)
1. **OSPF 링크 상태 라우팅 프로토콜의 문제점**
   - 모든 라우터는 네트워크에 대한 전체 정보를 학습합니다.
   - 대규모 네트워크에서는 많은 경로가 라우팅 테이블에 추가되고, 과도한 메모리와 CPU 자원이 소모됩니다.
   - 네트워크 변화 시 재수렴 시간이 증가합니다.
2. **OSPF 영역을 통한 계층적 설계**
   - **목적**: 대규모 네트워크를 여러 개의 작은 영역으로 나누어 효율을 높입니다.
   - **장점**:
      - 라우팅 테이블 경로 수 감소.
      - 재수렴 시 각 영역 내에서만 영향을 미침.
      - 라우터의 자원 사용 감소.
3. **OSPF 계층 구조**
   - **백본 영역(Area 0)**:
      - 최상위 전송 영역 역할을 합니다.
      - 비백본 영역 간의 트래픽은 항상 영역 0을 통해 이동해야 합니다.
   - **비백본 영역**:
      - 최종 사용자 및 기타 네트워크 영역이 연결되는 영역.
      - 주로 목적지 트래픽을 전송하는 데 사용됩니다.

- #### OSPF 라우터 유형
1. **백본 라우터**
   - 모든 인터페이스가 영역 0에 속한 라우터입니다.
   - 영역 0의 전체 링크 상태 데이터베이스(LSDB)를 유지합니다.

2. **영역 경계 라우터(ABR)**
   - 여러 영역에 걸쳐 있는 인터페이스를 가진 라우터입니다.
   - 각 영역의 정보를 요약하여 다른 영역에 전달해 영역을 구분하고 네트워크 자원을 절약합니다.

3. **일반 영역 라우터**
   - 모든 인터페이스가 단일 영역에 속한 라우터입니다.
   - 속한 영역의 전체 링크 상태 데이터베이스를 유지하며 다른 영역의 요약 경로를 학습합니다.

4. **자율 시스템 경계 라우터(ASBR)**
   - OSPF 외부의 다른 프로토콜(EIGRP, RIP 등) 또는 정적 경로를 OSPF로 재분배하는 라우터입니다.
   - 외부 경로로 표시되어 다른 OSPF 라우터들에게 광고됩니다.


- #### 요약 및 경로 재분배 설정
  - **ABR 요약**: 여러 경로를 하나로 묶어 요약하여 다른 영역에 전달함으로써 효율성을 높입니다.
    - 예: Area 1의 여러 네트워크를 10.0.0.0/16으로 요약하여 다른 영역에 전달.
  - **ASBR 재분배**: 외부 경로를 OSPF로 가져와서 다른 OSPF 이웃에게 광고합니다.

- #### 주요 이점
  - 라우터의 자원 사용 최적화.
  - 장애의 영향을 해당 영역에 국한시켜 네트워크 안정성 증대.
  - 대규모 네트워크에서의 효율적 관리 가능.


### 네트워크 인터페이스 명령어: `speed`, `clock rate`, `bandwidth`

1. **`speed` 명령어**
   - **역할**: 이더넷 인터페이스의 물리적 전송 속도를 설정하는 명령어입니다.
   - **기본값**: 
     - GigabitEthernet: 1,000Mbps (1Gbps).
     - FastEthernet: 100Mbps.
   - **예시**:
     - `speed 10` 명령어를 입력하면 물리적 속도가 10Mbps로 변경됩니다.
     - 주의: 양쪽 링크 모두 동일하게 설정해야 문제를 방지할 수 있습니다.
   - **정리**: `speed` 명령어를 사용하여 이더넷 인터페이스의 물리적 전송 속도를 조정할 수 있습니다.
2. **`clock rate` 명령어**
   - **역할**: 직렬 인터페이스의 물리적 전송 속도를 설정하는 명령어입니다.
    - 직렬 인터페이스 설명: 주로 WAN (Wide Area Network) 환경에서 네트워크 장비 간의 장거리 연결을 위해 사용됩니다. 네트워크 장비 간에 데이터를 직렬로 전송하는 방식의 인터페이스입니다. 즉, 데이터를 하나의 비트씩 순차적으로 전송하는 구조를 가지고 있습니다. 
   - **기본값**: 1.544Mbps (T1 인터페이스 속도).
   - **예시**:
     - `clock rate 64000` 명령어를 입력하면 전송 속도가 64Kbps로 설정됩니다.
     - 마찬가지로 양쪽 링크에서 동일한 설정이 필요합니다.
   - **정리**: `clock rate` 명령어는 직렬 인터페이스의 속도를 설정할 수 있으며, T1 속도를 기준으로 사용됩니다.
3. **`bandwidth` 명령어**
   - **역할**: 인터페이스의 논리적 대역폭을 설정하여 라우터의 소프트웨어 정책에 영향을 줍니다.
   - **기본값**:
     - FastEthernet: 100Mbps.
     - 직렬 인터페이스: 1.544Mbps.
   - **특징**:
     - `bandwidth` 명령어는 물리적 전송 속도에 영향을 미치지 않으며, 라우팅 프로토콜(OSPF, EIGRP)과 QoS 정책 등에 영향을 줍니다.
   - **예시**:
     - `bandwidth 50` 명령어로 FastEthernet 인터페이스의 대역폭을 50Mbps로 설정할 수 있습니다. 이 경우 물리적 속도는 여전히 100Mbps입니다.
   - **정리**: `bandwidth` 명령어는 실제 전송 속도에는 영향을 주지 않으며, 라우팅 결정 및 QoS와 같은 소프트웨어 정책에만 영향을 줍니다.

- 정리
  - **`speed`와 `clock rate`**: 물리적 전송 속도를 직접 변경하여 링크의 전송 속도를 조정합니다.
  - **`bandwidth`**: 소프트웨어 정책에만 영향을 주며, QoS나 라우팅 프로토콜의 경로 결정에 사용됩니다.


### OSPF 메트릭 (비용) 개요

1. **OSPF 메트릭과 경로 선택**
   - **OSPF (Open Shortest Path First)**는 **링크 상태 라우팅 프로토콜**입니다.
   - 라우터는 동일한 영역 내 모든 목적지에 대한 **링크 및 비용 정보를 수집**하여 비용이 가장 낮은 경로를 선택합니다.
   - **SPF (Shortest Path First)** 알고리즘을 사용하여, 목적지까지의 **누적 비용**이 가장 낮은 경로가 **선호 경로**로 선택됩니다.

2. **다중 영역 OSPF**
   - **영역 0 (백본)**과 연결된 **일반 영역**으로 구성됩니다.
   - **ABR (Area Border Router)**가 다른 영역과 연결되어 정보를 요약해 전달합니다.
   - **영역 내 목적지**: 라우터는 영역 내 경로 중 비용이 가장 낮은 경로를 선택합니다.
   - **다른 영역 목적지**: 라우터는 ABR까지의 최적 경로를 선택한 후, ABR이 목적지까지의 경로를 계산합니다.

3. **비대칭 라우팅 방지**
   - 각 링크의 **양쪽 인터페이스**에 동일한 비용을 설정해야 **비대칭 라우팅**이 발생하지 않습니다.
   - 링크 양쪽의 비용이 다르면 **트래픽이 각 방향에서 다른 경로**로 전달될 수 있습니다.

4. **참조 대역폭과 OSPF 비용 계산**
   - **OSPF 비용**은 인터페이스 **대역폭**을 기준으로 자동 계산됩니다.
   - 기본 **참조 대역폭**은 100Mbps로 설정되어, 고속 이더넷(100Mbps)은 비용이 1입니다.
   - 그러나 **기가비트 이상의 대역폭**도 동일한 비용(1)으로 설정되어 네트워크 효율에 문제가 생길 수 있습니다.
   - 이를 해결하기 위해 **참조 대역폭을 조정**하여 OSPF가 더 높은 대역폭 경로를 선호하도록 설정할 수 있습니다.

5. **참조 대역폭 설정 방법**
   - 명령어: `auto-cost reference-bandwidth [값]`
   - 예: 참조 대역폭을 **100,000 (100Gbps)**로 설정하면, 고속 이더넷의 비용은 1000이 되고, 기가비트 이더넷은 100이 되어 기가비트 경로를 선호하게 됩니다.
   - 모든 라우터에서 동일한 참조 대역폭을 설정하여 **일관성**을 유지해야 합니다.

6. **비용과 대역폭 조정 방법**
   - **대역폭 조정**: 특정 인터페이스의 대역폭을 수동 설정하여 비용에 반영할 수 있습니다.
   - **비용 직접 설정**: `ip ospf cost [값]` 명령어로 특정 링크의 비용을 수동 설정하여 경로를 조정할 수 있습니다.
   - 대역폭 조정보다는 **비용을 직접 설정하는 방법**이 QoS(서비스 품질) 등 다른 네트워크 정책에 영향을 덜 줍니다.
  
### **OSPF 라우터 작동 요약 및 인접성 형성**

1. **OSPF 기본 동작 요약**
   - OSPF 활성화 시 라우터는 이웃을 발견하고 인접성을 형성.
   - 링크 상태 데이터베이스(LSDB)를 구축하고, 최적 경로를 계산해 라우팅 테이블에 설치.
   - 네트워크에 변화가 생기면 이를 반영해 라우팅 테이블 업데이트.

2. **OSPF 패킷 유형**
   - **Hello**: 이웃 라우터와 인접성 형성.
   - **DBD (Database Description)**: 서로 알고 있는 네트워크 정보 요약 제공.
   - **LSR (Link State Request)**: 필요한 추가 정보를 요청.
   - **LSA (Link State Advertisement)**: 네트워크 경로 광고.
   - **LSU (Link State Update)**: 경로 업데이트용.
   - **LSAck (Link State Acknowledgment)**: 정보 수신 확인.

3. **OSPF 통신 프로토콜 번호**
   - OSPF는 프로토콜 번호 89 사용.

4. **Hello 패킷 주요 구성 요소**
   - **Router ID**: 라우터를 고유하게 식별.
   - **Hello Interval/Dead Interval**: 패킷 전송 및 라우터 상태 확인 주기.
   - **이웃 목록**: 인접한 OSPF 이웃 라우터의 목록.
   - **Area ID**: 링크 수준에서의 영역 식별.
   - **라우터 우선순위**: DR(BDR) 선정을 위한 8비트 숫자.
   - **인증 플래그**: 인증 비밀번호 일치 확인.
   - **Stub 영역 플래그**: 스텁 영역 여부 표시.

5. **Hello 패킷으로 인접성 형성 요건**
   - **Hello/Dead Interval, Area ID, IP 서브넷, 인증 플래그**가 일치해야 함.
   - **Stub 영역 설정**도 일치해야 인접성 형성 가능.

6. **MTU 불일치**
   - MTU(Maximum Transmission Unit)가 불일치하면 OSPF 인접성 형성 불가.
   - 설정 확인 방법: `show interface` 및 `show IP interface` 명령어 활용.

7. **라우터 간 인접성 형성 단계**
   - **Hello 패킷 교환**: 이웃 발견 후 양방향 상태 형성.
   - **DBD 교환**: 라우터 ID가 높은 쪽이 먼저 링크 상태 데이터베이스 요약 전송.
   - **링크 상태 요청(LSR) 및 업데이트(LSU)**: 부족한 정보를 요청하고, 링크 상태 업데이트를 통해 경로를 완성.

#### OSPF 인접성 문제 해결 랩

##### 랩 환경 소개
우리는 두 대의 라우터(R1, R2)를 사용하여 간단한 네트워크 토폴로지를 설정했습니다. 각 라우터의 물리적 인터페이스는 '10.x.x.x' 네트워크에 연결되어 있으며, OSPF를 설정하여 이들 라우터 간 인접성을 형성할 예정입니다.

##### R2 설정 확인
먼저, R2의 설정을 확인해보겠습니다. 이미 OSPF 설정이 되어 있으므로, `show run | section ospf` 명령어로 구성 내용을 확인할 수 있습니다. 여기서 `router ospf 1`이 설정되어 있고, 네트워크 명령문도 추가되어 있어 라우터가 Area Border Router(ABR) 역할을 하고 있음을 알 수 있습니다. `sh ip interface brief` 명령어를 통해 루프백 인터페이스도 구성된 것을 확인할 수 있습니다.

##### R1 설정
R1을 Area 1의 내부 라우터로 설정하기 위해 템플릿을 사용하겠습니다. R2 설정에서 필요 없는 부분을 제거한 뒤, `sh ip proto` 명령어로 현재 OSPF가 설정되지 않았음을 확인합니다. 디버그 모드를 활성화하여 OSPF 인접성 형성을 확인하기 위해 `debug ip ospf adj` 명령어를 사용합니다. 설정을 입력하면 R2와 인접성이 형성되고, 디버그 출력에서 DOWN 상태에서 시작해 2WAY, EXCHANGE, 그리고 FULL 상태로 전환되는 과정을 볼 수 있습니다.

##### OSPF 인접성 문제 해결
OSPF 인접성 문제를 고의로 발생시켜 해결 방법을 살펴보겠습니다. R2의 `g0/0` 인터페이스에서 Hello 타이머를 5초로 설정하고 MTU를 1460 바이트로 변경하여 인접성을 방해할 것입니다. 이 경우 `show ip ospf interface` 명령어로 Hello 타이머와 MTU 설정을 확인할 수 있습니다.

R1에서 `sh ip ospf nei`를 실행하면 Hello 타이머 불일치 문제로 인해 이웃 관계가 형성되지 않은 것을 확인할 수 있습니다. `debug ip ospf hello` 명령어를 통해 Hello 타이머가 불일치함을 디버깅할 수 있습니다. 문제를 해결하기 위해, 양쪽의 Hello 타이머를 일치시키고 다시 인접성을 확인합니다.

또한, MTU 설정 불일치로 인한 EXCHANGE 상태 문제도 발생시켜 `debug ip ospf adj`로 이를 확인한 후, IP MTU를 일치시켜 문제를 해결합니다. 최종적으로 `show ip ospf nei`에서 인접성이 FULL 상태로 정상적으로 형성된 것을 확인할 수 있습니다.

### OSPF에서 DR(지정 라우터)과 BDR(백업 지정 라우터)의 개념 및 역할

1. **OSPF 인접성 형성 과정**
   - OSPF를 활성화한 라우터는 **Hello 패킷**을 통해 다른 OSPF 라우터를 탐색.
   - 인접 라우터들이 서로를 발견하면 **양방향 상태**가 되고, 이후 **교환 → 로딩 → 완전 상태**로 발전.
   - 완전 상태에서는 모든 라우팅 정보를 공유하며, 지점 간 링크에서는 항상 완전 인접성을 형성.

2. **다중 액세스 세그먼트의 비효율성 문제**
   - 다중 액세스 세그먼트(예: 이더넷)에서는 여러 라우터가 연결될 수 있음.
   - 모든 라우터가 서로 완전 인접성을 형성하면 **중복된 정보 전송**이 발생하여 비효율적임.

3. **DR(지정 라우터)과 BDR(백업 지정 라우터)의 역할**
   - OSPF는 **DR**을 선출하여 해당 네트워크에서 라우팅 정보를 대표로 관리하게 함.
   - DR의 장애에 대비해 **BDR**도 함께 선출하여, DR에 문제가 발생할 경우 BDR이 DR 역할을 대신함.

4. **DR과 BDR 선출 과정**
   - DR과 BDR은 **각 다중 액세스 세그먼트**에서 인터페이스 수준에서 선출됨.
   - **우선 순위 값**이 가장 높은 라우터가 DR, 그다음이 BDR이 됨.
   - 기본 우선 순위는 1이며, 우선 순위가 같을 경우 **라우터 ID**가 더 높은 라우터가 선출됨.
   - 우선 순위를 0으로 설정하면 해당 라우터는 DR 또는 BDR로 선출되지 않음.

5. **DR과 BDR 수동 설정 방법**
   - **수동 설정 명령어 예시**:
     ```plaintext
     interface FastEthernet 0/0
     ip ospf priority 100  # DR 우선 순위 설정 (우선 순위 1보다 높은 값 설정)
     ```
   - DR과 BDR을 모두 설정하고자 할 경우, DR은 100, BDR은 50 등으로 각각 우선 순위를 다르게 지정할 수 있음.
   - 우선 순위를 변경한 후 OSPF 프로세스를 재시작해야 반영됨.

6. **DR과 BDR의 라우팅 정보 전달 방식**
   - DR과 BDR은 다중 액세스 세그먼트의 모든 라우터와 **완전 이웃 상태**를 형성.
   - DR은 다른 라우터들과의 정보를 **멀티캐스트 주소 224.0.0.5**를 통해 전달.
   - DR과 BDR만이 **224.0.0.6** 주소로 전송된 링크 상태 업데이트 패킷을 수신하여, 필요한 라우팅 정보만 효율적으로 공유.
    - 나지는 2WAY 상태를 유지함. (LSU를 보내지 않음.)

7. **실무 및 시험에서의 중요성**
   - CCNA 시험에서는 DR과 BDR 선출 및 우선 순위 설정을 다루므로, OSPF 작동 방식을 숙지하는 것이 중요함.
   - 실무에서는 보통 라우터가 자체적으로 DR을 선출하도록 설정하지만, 특정 라우터를 DR로 설정해야 하는 상황도 있음.

#### OSPF DR/BDR 랩 데모 요약

이번 강의에서는 OSPF에서 지정 라우터(DR)와 백업 지정 라우터(BDR)가 어떻게 선출되고 동작하는지를 실습으로 확인해 보겠습니다.

1. 랩 토폴로지 개요
- **라우터 구성**: R6, R7, R8, R9의 네 라우터가 연결됨.
- **루프백 인터페이스**:
  - R6: 192.168.0.6/32
  - R7: 192.168.0.7/32
  - R8: 192.168.0.8/32
  - R9: 192.168.0.9/32
- **이더넷 세그먼트**:
  - R6, R7, R8, R9 모두 172.16.0.0/24 네트워크에 연결됨.
- **OSPF 설정 상태**: 현재 OSPF가 활성화되어 있지만, 루프백 인터페이스만 네트워크에 포함되어 있고 이더넷 인터페이스는 OSPF가 활성화되지 않은 상태입니다.

2. DR/BDR 선출 예상
- OSPF 우선 순위를 변경하지 않았기 때문에 기본 우선 순위는 모두 1입니다.
- 가장 높은 라우터 ID(루프백 주소)를 가진 라우터가 DR이 되고, 그다음으로 높은 라우터가 BDR이 됩니다.
- 따라서 DR은 R9(192.168.0.9), BDR은 R8(192.168.0.8)으로 예상됩니다.

3. OSPF 활성화 및 DR/BDR 확인
1. 각 라우터의 이더넷 인터페이스에서 OSPF를 활성화.
2. **명령어**: `show ip ospf neighbor`를 통해 인접 상태를 확인.
   - R9: DR (192.168.0.9)
   - R8: BDR (192.168.0.8)
   - R6, R7: DROTHER (DR, BDR가 아님)

3. **완전 상태 형성**:
   - DR과 BDR은 네트워크 내 모든 라우터와 완전 상태를 형성.
   - DROTHER는 DR과 BDR과만 완전 상태를 형성하며 서로 간에는 2WAY 상태를 유지.

4. DR 선출 변경 실습
1. **R7을 DR로 선출 설정**:
   - R7의 이더넷 인터페이스에서 `ip ospf priority 100`으로 우선 순위를 변경.
   - **DR 재선출**: `clear ip ospf process` 명령어로 OSPF 프로세스를 재시작.
   - DR이 R7(192.168.0.7)로 변경되고, 기존 BDR(R8)은 그대로 유지.

2. **DR 장애 시 BDR 동작 확인**:
   - R7의 전원을 꺼서 DR 역할을 중지.
   - BDR이었던 R8이 자동으로 DR 역할을 대체하며, R9가 새로운 BDR로 선출됨.

5. 요약 및 결론
- OSPF 다중 액세스 네트워크에서 DR과 BDR 선출은 라우터 우선 순위와 라우터 ID에 따라 결정됨.
- DR 장애 시, BDR이 자동으로 DR로 승격되며 네트워크 안정성을 유지.
- `show ip ospf interface` 명령어를 사용해 DR과 BDR 상태를 쉽게 확인 가능.


---

> Source: `section_21/ysj/note.md`

## Section 21 정리

### LAN 설계

이번 강의에서는 로컬 영역 네트워크(LAN)의 설계에 대해 학습합니다. 

1. 로컬 영역 네트워크(LAN) 범위
- **단일 건물** 또는 **로컬 캠퍼스 내 여러 건물**을 대상으로 하는 네트워크 설계에 집중.
- **광역 네트워크(WAN)**(예: 뉴욕, 휴스턴, 싱가포르에 걸친 네트워크)는 이후 섹션에서 다룸.

2. LAN 설계 고려 사항
- **확장성**과 **성능**, **보안**을 고려한 설계 필요.
- 네트워크 토폴로지를 **액세스층**, **분배층**, **코어층**으로 나누어 설계.

3. 계층별 설계 원칙
1. **액세스층**
   - 캠퍼스 본관과 별도 건물의 각 층에 여러 액세스 스위치 설치.
   - 종단 호스트(데스크톱, 서버, IP 전화 등)가 연결되는 계층.
   - 저비용으로 높은 포트 개수를 제공해 다수의 호스트 지원.
   - 포트 보안 등 클라이언트 액세스 보안 활성화.
   
2. **분배층**
   - 액세스층 스위치가 분배층 스위치로 업링크.
   - 액세스층 스위치들 간 연결은 없으며, 분배층 스위치로 집성됨.
   - 분배층 스위치는 다중 쌍으로 구성되어 단일 장애 지점을 방지.
   - **서비스 품질(QoS) 정책** 등 주요 소프트웨어 정책 활성화.

3. **코어층**
   - 분배층 스위치가 코어층 스위치로 업링크.
   - 모든 빌딩의 분배층 스위치를 연결해 속도와 복원성 중심으로 설계.
   - 소프트웨어 정책은 속도 저하를 방지하기 위해 최소화.

4. 소규모 네트워크 설계
- 소규모 캠퍼스의 경우, **분배층과 코어층을 통합**하여 설계.
- 단일 하드웨어 장치에서 분배 및 코어 역할을 수행.

요약
- **액세스층**: 종단 호스트 연결, 높은 포트 개수, 보안 정책 구현.
- **분배층**: 액세스층 집성, 다중성 확보, QoS 등 소프트웨어 정책 적용.
- **코어층**: 속도와 복원성 중점, 분배층 연결, 소프트웨어 정책 최소화.

### 스파인-리프 데이터 센터 네트워크 설계

1. 전통적인 캠퍼스 네트워크 설계
- **코어층, 분배층, 액세스층**으로 구성된 계층형 설계.
- **북쪽-남쪽(North-South)** 트래픽 흐름에 최적화된 방식.
  - 예: 데이터 센터 내에서 데이터가 코어층으로 올라갔다가 다시 내려가 클라이언트에게 전달되는 방식.
- 이 구조는 클라이언트가 데이터 센터와 주로 통신할 때 적합.

2. 현대적 데이터 센터의 동-서(East-West) 트래픽 증가
- **동쪽-서쪽(East-West)** 트래픽은 데이터 센터 내 서버들 간의 트래픽 흐름을 의미.
  - 예: 서버 간 통신(프론트엔드 서버와 백엔드 데이터베이스 간 데이터 전송).
- **가상화**와 **서버 클러스터링** 증가로 인해 동쪽-서쪽 트래픽 비중이 높아짐.
- 전통적 네트워크 설계는 동쪽-서쪽 트래픽이 많은 경우 성능 저하가 발생할 수 있음.

3. 스파인-리프 데이터 센터 설계
- **스파인(Spine)** 스위치와 **리프(Leaf)** 스위치로 구성된 설계.
- 리프 스위치들은 각 서버에 연결되며, 각 리프 스위치는 모든 스파인 스위치와 **그물망 형태의 연결**을 가짐.
- **확장성과 성능**을 극대화하기 위해 동쪽-서쪽 트래픽에 최적화.
  - 리프 스위치를 추가하는 방식으로 손쉽게 확장 가능.
  - 최대 두 개 홉(1 홉: 리프 → 스파인, 2 홉: 스파인 → 리프)으로 서버 간 통신 가능.
  
4. 스파인-리프 설계의 장점
- **확장성**: 네트워크 크기를 쉽게 확장할 수 있음.
- **성능**: 동쪽-서쪽 트래픽이 많을 때도 높은 성능 유지.
- 북쪽-남쪽 트래픽도 여전히 잘 작동하지만, 동쪽-서쪽 트래픽에 대한 추가 이점이 있음.

### VLAN 사용의 필요성과 이점

1. VLAN을 사용하는 이유
- VLAN은 **스위치**에서 **2계층** 기능으로 구현됩니다.
- VLAN이 필요한 이유를 이해하려면, VLAN이 해결해주는 문제점에 대해 먼저 알아야 합니다.

2. 라우터와 스위치 운용 방식 비교
- **라우터**는 **3계층** 장비로, 여러 IP 서브넷 간의 트래픽을 라우팅하고, **보안 규칙**을 통해 서브넷 간 트래픽을 제어할 수 있습니다.
  - 예: 엔지니어링 서브넷(10.10.10.0/24)과 회계 서브넷(10.10.20.0/24) 간의 트래픽을 제한.
- **스위치**는 **2계층** 장비로, 기본적으로 브로드캐스트 트래픽을 전송하여 모든 포트로 전파합니다. 이로 인해 **보안 문제**와 **성능 저하**가 발생할 수 있습니다.
  - 유니캐스트의 경우 효율적으로 처리함.
  - 스위치는 IP를 모르므로, 특정 서브넷에만 요청을 전송할 수 없음. 스위치에 연결된 모든 HOST에 브로드캐스트를 보내게 됨.

3. 스위치 기반 네트워크의 문제점
- **브로드캐스트 도메인**: 스위치는 기본적으로 모든 IP 서브넷에 브로드캐스트 트래픽을 전송합니다.
- 이로 인해 불필요한 트래픽이 전체 네트워크에 전파되며, 보안 위험과 성능 저하를 유발할 수 있습니다.
- 예를 들어, 영업 팀의 PC가 브로드캐스트 트래픽(예: ARP 트래픽)을 전송하면 엔지니어링 팀과 회계 팀 모두 이 트래픽을 수신하게 됩니다.

4. VLAN의 역할과 장점
- VLAN을 이용하면 스위치를 통해 네트워크를 **여러 개의 브로드캐스트 도메인**으로 분할할 수 있습니다.
- **IP 서브넷과 VLAN 간 일대일 관계**를 설정하여 네트워크 성능과 보안을 향상시킵니다.
- 메모: 물리적인 LAN보다 더 작은 규모의 LAN이 존재하는 것처럼 사용할 수 있음. (브로드캐스트 범위 제한 등, VLAN 단위를 IP 서브넷 단위로 설정 등)

5. VLAN을 적용한 네트워크 예시
- VLAN을 적용하여 스위치 내에 **엔지니어링 VLAN**과 **영업 팀 VLAN**을 구분할 수 있습니다.
- 동일 VLAN 내의 장치들만 트래픽을 주고받을 수 있도록 구성하여 브로드캐스트 트래픽이 필요한 곳으로만 전송되도록 합니다.
- 예를 들어, 영업 팀 PC가 브로드캐스트 트래픽을 전송할 경우, 영업 팀 VLAN에 속한 장치들로만 트래픽이 전달되어 성능과 보안이 강화됩니다.

6. VLAN을 통한 보안과 성능 향상
- **보안**: VLAN을 통해 트래픽이 특정 VLAN에 속한 장치로만 전달되므로, 네트워크 세그먼트 간 불필요한 트래픽이 줄어들고 보안성이 강화됩니다.
- **성능**: 브로드캐스트 트래픽이 제한됨으로써 네트워크 성능 저하를 방지할 수 있습니다.

### VLAN 액세스 포트와 구성 방법 강의 요약

1. VLAN 액세스 포트의 정의와 역할
- **액세스 포트**는 **종단 호스트**(PC, 프린터 등)가 연결된 스위치의 인터페이스로, **특정 VLAN**에 할당됩니다.
  - 예: 엔지니어링 팀의 PC가 연결된 포트를 엔지니어링 VLAN의 액세스 포트로 구성.
- **종단 호스트는 VLAN을 인식하지 않으며** 스위치에서만 VLAN 트래픽을 관리합니다.
- **VLAN**을 통해 캠퍼스 LAN을 작은 **브로드캐스트 도메인**으로 나누어 성능과 보안을 향상시킬 수 있습니다.

2. VLAN 구성의 중요성
- VLAN을 잘못 구성하면 같은 IP 서브넷에 속하는 장치들이 통신할 수 없게 됩니다.
  - 예: 영업 팀 PC를 잘못된 VLAN에 할당하면 영업 팀 VLAN 내의 다른 장치와 통신할 수 없습니다.
- **같은 IP 서브넷의 호스트는 동일한 VLAN에 속해야** 하며, 서로 다른 IP 서브넷은 각기 다른 VLAN에 속해야 합니다.

3. VLAN 구성 기본 단계
1. **VLAN 생성**
   - 글로벌 구성 모드에서 `vlan [번호]` 명령어로 VLAN을 생성.
   - VLAN에 **이름**을 지정할 수 있습니다 (`name [이름]`).

2. **스위치 포트를 VLAN에 할당**
   - 액세스 포트로 설정: `switchport mode access`
   - 특정 VLAN에 할당: `switchport access vlan [번호]`
   - 여러 포트를 한 번에 설정할 경우 `interface range` 명령어 사용: `interface range FastEthernet 0/3 - 5`

4. VLAN 구성 예제
- **엔지니어링 VLAN** (VLAN 10)
   ```plaintext
   vlan 10
   name Eng
   interface FastEthernet 0/1
   switchport mode access
   switchport access vlan 10
   interface range FastEthernet 0/3 - 5
   switchport mode access
   switchport access vlan 10
   ```
  
- **영업 VLAN** (VLAN 20)
   ```plaintext
   vlan 20
   name Sales
   interface FastEthernet 0/2
   switchport mode access
   switchport access vlan 20
   interface range FastEthernet 0/6 - 7
   switchport mode access
   switchport access vlan 20
   ```

5. VLAN 검증 명령어
- **show vlan brief**: 현재 스위치의 모든 VLAN 및 각 포트의 VLAN 할당 상태를 확인.
- **show interface [인터페이스] switchport**: 특정 포트의 VLAN 정보 확인.

이렇게 해서 **VLAN 액세스 포트를 설정**하고 **구성을 검증**하는 방법을 배웠습니다.

### VLAN 트렁크 포트

1. **액세스 포트와 VLAN 통신**
   - **액세스 포트**: 하나의 VLAN에 연결된 PC가 스위치로 통신하는 기본 포트
   - **브로드캐스트 도메인 분할**: VLAN을 통해 브로드캐스트 범위를 제한하여 성능과 보안을 향상

2. **스위치 간 VLAN 트래픽 전달 문제**
   - 여러 스위치를 사용하는 환경에서 같은 VLAN에 속한 PC가 서로 다른 스위치에 연결되면, 기본 설정만으로는 서로 통신 불가
   - **해결책**: 스위치 간 링크를 트렁크 포트로 구성하여 여러 VLAN 트래픽이 통과할 수 있도록 함

3. **트렁크 포트와 Dot1Q 트렁킹 프로토콜**
   - **Dot1Q 프로토콜**: 트래픽에 VLAN 태그를 추가하여 목적지 스위치가 VLAN을 구분 가능하게 함
   - **트렁크 포트**: 스위치 간 연결을 통해 여러 VLAN 트래픽을 전송하도록 설정한 포트

4. **트렁크 포트 구성 예시**
   - 설정 명령어:
      ```plaintext
      interface GigabitEthernet 0/1
      description Trunk to SW2
      switchport trunk encapsulation dot1q
      switchport mode trunk
      ```

5. **특수 환경의 트렁킹**
   - **가상 호스트** (VMware, HyperV): 여러 VLAN의 가상 머신 트래픽을 분리해야 하므로 트렁크 포트 필요
   - **IP 전화와 PC 연결**: 음성 트래픽과 데이터 트래픽을 분리하여 우선 처리 및 보안 확보
      ```plaintext
      interface FastEthernet 0/10
      switchport mode access
      switchport access vlan 10
      switchport voice vlan 20
      ```

6. **native VLAN과 보안**
   - **native VLAN**: 태그가 없는 트래픽이 전달될 기본 VLAN (기본값: VLAN 1)
   - **보안 권장사항**: 보안상의 이유로 VLAN 1을 피하고 사용되지 않는 VLAN으로 native VLAN을 변경
      ```plaintext
      vlan 199
      name Native
      interface GigabitEthernet 0/1
      switchport trunk native vlan 199
      ```

7. **허용 VLAN 제한**
   - **허용 VLAN 설정**: 필요한 VLAN만 트렁크 포트에서 허용하여 성능 최적화 및 보안 강화
      ```plaintext
      interface GigabitEthernet 0/1
      switchport trunk allowed vlan 10,30
      ```
8. 메모
- https://en.wikipedia.org/wiki/IEEE_802.1Q 를 보면, 어떤 식으로 구현되는지 알 수 있는데, 프레임에 표준 형식의 해더가 추가되고, 그걸 스위치에서 지원하는 식. 해당 프로토콜을 사용하는지 식별하기 위한 필드 + VLAN 식별자 + 기타 정보를 포함함.

### 동적 트렁킹 프로토콜(DTP) 개요

Cisco 스위치 간 연결 시, **동적 트렁킹 프로토콜(DTP)**를 통해 자동으로 트렁크를 설정할 수 있습니다. 그러나 보안과 안정성 측면에서 **포트를 수동으로 직접 설정**하는 것이 권장됩니다.  

포트 수동 설정 명령어:
- **액세스 포트**: `switchport mode access`
- **트렁크 포트**: `switchport mode trunk`

DTP 명령어

1. **switchport mode dynamic auto**
   - 포트가 `trunk`나 `desirable`로 설정된 인접 스위치에 연결 시 트렁크를 형성합니다.
   - 양쪽 포트가 모두 `auto`로 설정되어 있을 경우 트렁크가 형성되지 않습니다.
   - 신형 스위치의 기본 설정입니다.

2. **switchport mode dynamic desirable**
   - 인접 포트가 `trunk`, `desirable`, 또는 `auto`일 때 트렁크가 형성됩니다.
   - 구형 스위치에서는 이 설정이 기본값입니다.

3. **switchport nonegotiate**
   - DTP를 비활성화하여 자동 협상을 방지합니다. 포트를 `access`나 `trunk`로 명시적으로 설정해야 합니다.

**권장 방법**: 호스트 연결 시 `switchport mode access`, 스위치 연결 시 `switchport mode trunk` 설정을 권장합니다. (= DTP 사용하지 않고, 수동으로 설정하는 것을 권장한다는 말.)



### VTP(VLAN Trunking Protocol) 개요

**VTP**는 네트워크 내 여러 스위치에 걸쳐 **VLAN 설정을 중앙에서 관리하고 동기화**하는 Cisco 프로토콜입니다. VTP를 사용하면 **VLAN 추가, 편집, 삭제**가 VTP 서버에서 한 번 이루어지면 클라이언트 스위치들이 자동으로 동기화합니다.

- **VTP 서버**에서 VLAN을 생성하거나 삭제하면, 해당 VLAN 정보가 **VTP 클라이언트**로 구성된 스위치에 자동으로 전달됩니다.
- VTP는 **대형 네트워크**에서 일일이 VLAN을 생성할 필요 없이 중앙에서 관리할 수 있는 장점이 있습니다.
- **주의**: VTP 개정 번호가 높은 스위치가 연결되면 기존 VLAN 정보가 의도치 않게 삭제되거나 덮어씌워질 수 있으므로 VTP 사용 시 주의가 필요합니다.

메모1: 특정 스위치가 마스터가 되서 VLAN 정보를 저장하는 일종의 데이터베이스 역할을 한다고 보면 됨.
메모2: VLAN 이름이랑 id를 관리해줄 뿐, 각 스위치의 어떤 포트가 어떤 VLAN에 속하는지는 직접 설정해줘야 함.

VTP 모드 종류

1. **VTP 서버 모드**
   - VLAN을 **추가, 편집, 삭제**할 수 있으며, 클라이언트와 트랜스패런트 스위치로 VLAN 정보를 전파합니다.
   - 여러 서버를 둘 수 있지만, **가장 높은 개정 번호를 가진 서버**가 나머지 스위치를 동기화합니다.

2. **VTP 클라이언트 모드**
   - VLAN을 직접 추가하거나 삭제할 수 없고, 서버로부터 정보를 받아 동기화합니다.

3. **VTP 트랜스패런트 모드**
   - VTP 도메인에 참여하지 않으며, **VLAN 정보를 전달**만 합니다.
   - 로컬 VLAN만 관리하며, 서버 또는 클라이언트의 VLAN 변경 사항을 반영하지 않습니다.

VTP 실습 예제

1. **VTP 서버 구성**
   - 서버에서 `vtp domain Flackbox`와 `vtp mode server`로 VTP 도메인과 모드를 설정합니다.
   - 필요한 VLAN을 생성합니다. 예를 들어, `vlan 10`, `name Eng`와 `vlan 20`, `name Sales`를 입력해 VLAN Eng와 Sales를 구성합니다.

2. **VTP 클라이언트 구성**
   - 클라이언트 스위치에서 `vtp domain Flackbox`와 `vtp mode client`를 설정합니다.
   - 서버로부터 VLAN 정보를 받아 동기화합니다.

3. **VTP 트랜스패런트 구성**
   - 트랜스패런트 스위치에서 `vtp mode transparent`를 설정하고 VLAN 10과 VLAN 20을 로컬에서 수동으로 추가합니다.
   - 트랜스패런트 스위치는 VTP 도메인에 속하지 않지만, 서버와 클라이언트 사이에서 VLAN 정보를 전달합니다.

VTP 사용 시 주의사항

- VTP 도메인에 있는 모든 스위치의 **도메인 이름이 일치**해야 합니다.
- VTP 개정 번호가 더 높은 스위치가 네트워크에 추가되면, 기존 VLAN 데이터베이스가 덮어씌워질 수 있습니다.
- 실수로 과거 개정 번호가 높은 스위치를 연결해 기존 VLAN 정보가 삭제되지 않도록 **개정 번호와 설정 상태를 주의**해야 합니다.


VTP 구성 및 확인 명령어

- VTP 도메인 설정: `vtp domain <도메인 이름>`
- VTP 모드 설정: `vtp mode <server | client | transparent>`
- VLAN 생성 예시: `vlan 20`, `name Sales`

VTP 설정 확인:
- `show vtp status` 명령으로 **VTP 도메인 이름, 모드, 개정 번호** 등을 확인합니다.



---

> Source: `section_22/ysj/note.md`

## Section 22 정리

### VLAN 간 라우팅 - 개별 인터페이스를 가진 라우터

VLAN과 IP 서브넷의 연관성

- **IP 서브넷과 VLAN의 관계**:
  - LAN 캠퍼스에서 IP 서브넷과 VLAN은 일반적으로 **일대일 관계**를 형성합니다.
  - 예를 들어, **엔지니어링 팀**의 호스트가 **10.10.10.0/24 서브넷**에 속해 있다면 **VLAN 10**과 연결됩니다.
  - **영업 팀**은 **10.10.20.0/24 서브넷**에 있으며 **VLAN 20**과 연결됩니다.

- **분리된 네트워크 구성**:
  - **IP 서브넷**으로 각 호스트는 **3계층에서 분리**됩니다.
  - **VLAN**으로 각 호스트는 **2계층에서 분리**되어 **별도의 브로드캐스트 도메인**을 형성합니다.
  - 서로 다른 IP 서브넷의 호스트는 **라우터를 통해** 트래픽을 주고받아야 통신할 수 있습니다.


첫 번째 VLAN 간 라우팅 옵션: 개별 인터페이스를 가진 라우터

- **라우터의 개별 인터페이스 사용**:
  - 각 VLAN에 대해 **별도의 물리적 인터페이스**가 있는 라우터를 사용해 라우팅합니다.
  - 예시에서는 **FastEthernet 0/1**이 **엔지니어링 VLAN**의 기본 게이트웨이로, **IP 10.10.10.1**을 할당합니다.
  - **FastEthernet 0/2**는 **영업 VLAN**의 기본 게이트웨이로, **IP 10.10.20.1**을 할당합니다.

- **라우터와 스위치 구성**:
  - 각 라우터 인터페이스를 각 VLAN과 매칭하여 스위치의 액세스 포트를 구성합니다.
  - 예시에서 **FastEthernet 0/1**은 VLAN 10(엔지니어링)에, **FastEthernet 0/2**는 VLAN 20(영업)에 연결됩니다.

외부 네트워크 연결과 기본 경로 설정

- **외부 네트워크 연결**:
  - 예시 라우터에서 **FastEthernet 0/3**은 광역망과 연결되어 있으며, IP는 **203.0.113.1**입니다.
  - **정적 기본 경로**를 사용하여, **203.0.113.2**를 다음 홉으로 설정합니다.

구성 명령어

1. **라우터 구성**:
   ```plaintext
   interface FastEthernet 0/1
   ip address 10.10.10.1 255.255.255.0
   no shutdown
   
   interface FastEthernet 0/2
   ip address 10.10.20.1 255.255.255.0
   no shutdown
   
   ip route 0.0.0.0 0.0.0.0 203.0.113.2
   ```

2. **스위치 구성**:
   ```plaintext
   interface FastEthernet 0/1
   switchport mode access
   switchport access vlan 10
   
   interface FastEthernet 0/2
   switchport mode access
   switchport access vlan 20
   ```

라우팅 확인 및 검증

- **핑 테스트**:
  - 엔지니어링 VLAN의 PC에서 같은 VLAN 내 다른 PC로 **핑** 테스트.
  - 영업 VLAN의 PC로 **핑**을 시도하면 **라우팅 설정 전**에는 실패합니다.
  - 라우팅 구성 후 다시 핑을 시도하여 **성공 여부 확인**.

- **라우터 인터페이스 확인**:
  - `show ip int brief` 명령어로 인터페이스 상태를 확인하여 **Up** 상태인지 검증.

첫 번째 옵션의 한계

- **인터페이스 부족 문제**:
  - 각 VLAN에 물리적 인터페이스가 필요해, VLAN 수가 많을 경우 **인터페이스 부족 문제**가 발생할 수 있습니다.
  
- **트래픽 지연 문제**:
  - 트래픽이 물리적 케이블을 따라 라우터로 이동하여 **지연**이 발생할 수 있습니다.

### VLAN 간 라우팅 - Router on a Stick

토폴로지 구성

- 가운데 스위치가 있으며, 엔지니어링 VLAN과 영업 VLAN용 PC들이 스위치에 연결된 상태입니다. 이전에 다룬 물리적 인터페이스 방식에서는 각 VLAN에 별도의 라우터 인터페이스가 필요했습니다. 하지만 이 방식은 **라우터의 서브 인터페이스**를 활용해 동일한 물리적 인터페이스로 여러 VLAN을 연결할 수 있습니다.

1. **물리적 인터페이스 설정**  
   - 라우터의 인터페이스 **F0/1**을 사용하여 스위치와 연결합니다.  
   - IP 주소 설정은 필요 없으며, 인터페이스를 활성화하려면 `no shutdown` 명령어를 실행합니다.

2. **서브 인터페이스 생성**  
   - **F0/1.10**: 엔지니어링 VLAN (VLAN 10)에 대한 서브 인터페이스 생성
      - 명령어: `interface FastEthernet 0/1.10`
      - VLAN 태그 설정: `encapsulation dot1q 10`
      - IP 주소: `ip address 10.10.10.1 255.255.255.0`  
      - 엔지니어링 VLAN의 기본 게이트웨이 역할을 합니다.
   - **F0/1.20**: 영업 VLAN (VLAN 20)에 대한 서브 인터페이스 생성
      - 명령어: `interface FastEthernet 0/1.20`
      - VLAN 태그 설정: `encapsulation dot1q 20`
      - IP 주소: `ip address 10.10.20.1 255.255.255.0`  
      - 영업 VLAN의 기본 게이트웨이 역할을 합니다.

동작 원리

- 스위치는 라우터와의 인터페이스를 트렁크 포트로 설정하고, VLAN 태그를 붙여 라우터로 트래픽을 전송합니다. 라우터는 **Dot1q 태그**를 확인하여 각 서브 인터페이스로 트래픽을 라우팅합니다.

WAN 연결 및 정적 경로 설정

- WAN 연결을 위해 F0/2 인터페이스에 IP 주소 **203.0.113.1**을 할당하고, **203.0.113.2**를 다음 홉으로 설정합니다.
- 명령어: `ip route 0.0.0.0 0.0.0.0 203.0.113.2`

스위치 구성

- 라우터와 연결된 스위치 인터페이스도 트렁크 포트로 설정합니다.
- 명령어:
  ```plaintext
  interface FastEthernet 0/1
  switchport trunk encapsulation dot1q
  switchport mode trunk
  ```

검증 및 테스트

- 구성이 완료되면, 각 VLAN의 PC들이 서로 통신할 수 있는지 핑 테스트를 진행합니다. 라우팅 구성이 완료되면 정상적으로 통신이 이루어져야 합니다.

### VLAN 간 라우팅 - 3계층 스위치

이번 강의에서는 세 가지 VLAN 간 라우팅 방법 중 마지막인 **3계층 스위치**를 활용한 방법을 살펴봅니다. 이는 실무에서 가장 일반적으로 사용되며, 외부 라우터 없이 스위치 자체에서 라우팅을 수행할 수 있는 방식입니다.

1. 네트워크 구성과 VLAN 구분
- **토폴로지**: 엔지니어링 VLAN과 영업 VLAN에 각각의 PC가 할당된 스위치가 있습니다. 
- **VLAN 할당**:
  - 엔지니어링 VLAN(10) – 서브넷: 10.10.10.0/24
  - 영업 VLAN(20) – 서브넷: 10.10.20.0/24

두 VLAN은 서로 다른 서브넷을 사용하여 VLAN 내 통신만 가능합니다. 두 서브넷 간 통신을 위해 라우팅이 필요합니다.

2. 3계층 스위치의 역할과 SVI 설정
- **라우터 없이 스위치에서 라우팅**:
  - 3계층 스위치에서 가상 인터페이스(SVI)를 통해 라우팅을 수행할 수 있습니다.
  - VLAN 10 및 VLAN 20에 대해 각각의 SVI를 설정합니다.
- **SVI 설정 명령어**:
  - `interface vlan 10` 
    - IP 주소: `10.10.10.1` /24
  - `interface vlan 20`
    - IP 주소: `10.10.20.1` /24
  
이러한 설정을 통해 각각의 SVI가 VLAN 10과 VLAN 20의 기본 게이트웨이 역할을 수행하여, 다른 VLAN 간 트래픽을 스위치에서 직접 라우팅할 수 있습니다.

3. WAN 연결 구성과 외부 라우터의 필요성
- **WAN 라우팅을 위한 외부 라우터 필요성**:
  - 스위치에 WAN 연결을 위해 별도의 라우터가 연결됩니다. WAN 연결의 물리적 요구 사항이나 특정 기능이 스위치에서 지원되지 않을 경우, 전용 라우터를 사용해야 합니다.
  - 스위치에서 3계층 인터페이스를 통해 WAN 라우터와의 통신을 설정합니다.

- **WAN 설정 예시**:
  - 스위치에서 WAN 라우터로 연결된 인터페이스(FastEthernet0/1)에 `no switchport`를 설정해 3계층 인터페이스로 전환하고, IP 주소를 할당합니다 (`ip address 10.10.100.1 255.255.255.0`).
  - 기본 경로로 WAN 라우터 IP인 `10.10.100.2`를 지정합니다: `ip route 0.0.0.0 0.0.0.0 10.10.100.2`.

4. 라우터 설정
- **내부와 외부 인터페이스 설정**:
  - 내부 인터페이스: `FastEthernet0/1`에 `10.10.100.2` 할당
  - 외부 인터페이스: `FastEthernet0/2`에 `203.0.113.1` 할당

- **경로 설정**:
  - LAN 트래픽: `10.10.0.0 255.255.0.0` 경로를 스위치 다음 홉 `10.10.100.1`로 설정해 두 VLAN을 포함하는 단일 요약 경로 구성
  - WAN 기본 경로: `ip route 0.0.0.0 0.0.0.0 203.0.113.2` 설정

주요 고려 사항
- **성능 최적화**: 외부 라우터가 아닌 3계층 스위치 백플레인(backplane)에서 라우팅을 수행하므로 성능이 향상됩니다. 물리적 케이블을 통해 상하로 트래픽이 이동할 필요가 없습니다.
- **WAN 기능의 한계**: 스위치에서 지원하지 않는 WAN 서비스가 필요할 경우, 외부 라우터를 통해 보완할 수 있습니다.

### 궁금증

- 3계층 스위치가 여러개가 연결되어 있으면 VLAN + IP주소에 따라 라우터처럼 사용될 것 같음.
  - 이러면 라우터랑 무슨 차이가 있을까? 
  - GPT 검색 결과로는 라우터에서 WAN 연결, 다양한 포트 타입 지원, 고급 라우팅 프로토콜, 다양한 라우팅 특화 기능 등이 있어서 대체는 어렵다고 함.

---

> Source: `section_23/ysj/note.md`

## Section 23 정리

## DHCP

### DHCP 개요

**DHCP**(Dynamic Host Configuration Protocol)에 대해 다루겠습니다. DHCP는 **클라이언트/서버 프로토콜**로, 호스트에 **IP 주소**, **서브넷 마스크**, **기본 게이트웨이**와 같은 네트워크 구성 정보를 자동으로 제공합니다. 

DHCP는 네트워크에 연결된 호스트가 수동 설정 없이 DHCP 서버로부터 **자동으로 IP 주소를 할당받는 방식**입니다. 이는 네트워크 관리의 번거로움을 크게 줄여줍니다.

1. **DHCP 클라이언트 설정 확인**  
   예를 들어 Windows PC의 경우 **제어판 > 네트워크 설정**에서 네트워크 어댑터 속성으로 들어가 **자동으로 IP 주소 받기**가 선택되어 있으면 해당 호스트는 DHCP 클라이언트로 설정된 상태입니다. 

2. **DHCP 작동 방식**  
   - **DHCP 탐색 (Discover):** 클라이언트가 DHCP 서버를 찾기 위해 브로드캐스트로 메시지를 보냅니다.
   - **DHCP 제안 (Offer):** 서버가 IP 주소를 포함한 정보를 제안합니다.
   - **DHCP 요청 (Request):** 클라이언트가 제안받은 IP 주소를 요청합니다.
   - **DHCP 수취 확인 (Acknowledge):** 서버가 최종적으로 확인 메시지를 보내며, 클라이언트는 IP 주소를 사용하게 됩니다.

이러한 과정을 통해 클라이언트는 필요한 네트워크 구성 정보를 자동으로 받게 됩니다.

DHCP의 장점

DHCP의 주요 이점은 **자동화**와 **오류 감소**입니다.

- **대규모 네트워크 관리**: 여러 개의 호스트에 수동으로 IP를 할당하는 대신, DHCP 서버에서 중앙 집중적으로 관리할 수 있습니다.  
- **오류 방지**: 수동 설정 시 발생할 수 있는 오타나 **IP 주소 중복** 문제를 방지할 수 있습니다.
- **DHCP 옵션 제공**: IP 주소 외에 TFTP 서버 위치와 같은 추가 정보를 DHCP 옵션으로 제공할 수 있습니다.  
- **유동적인 IP 주소 업데이트**: 무선 네트워크나 이동이 잦은 장치의 경우, 이동할 때마다 자동으로 IP 주소가 갱신되어 편리합니다.  

또한 **DHCP 릴레이 에이전트**를 통해 **다중 서브넷**을 지원할 수 있습니다. 각 서브넷에 서버를 둘 필요 없이 중앙의 DHCP 서버가 모든 서브넷에 IP 주소를 할당할 수 있게 됩니다.

DHCP 클라이언트와 고정 IP 설정

일반적으로, **데스크톱 PC나 노트북**과 같은 장치는 DHCP 클라이언트로 설정할 수 있습니다. 네트워크 상에서 IP 주소가 바뀌어도 문제가 없으므로 DHCP로 설정해도 무방합니다.

반면, **라우터**나 **스위치**, **방화벽**과 같은 네트워크 장비는 IP 주소가 **고정되어야** 하므로 DHCP 클라이언트로 설정하지 않습니다. 이 장비들은 네트워크 관리와 외부 서비스 제공에 필수적이기 때문에, IP가 변경되지 않도록 수동으로 설정합니다.

### DHCP 서버 구성: Cisco 라우터 사용법

**Cisco 라우터를 DHCP 서버로 구성**하는 방법을 소개합니다. 이 방법은 **지점 사무실** 등 소규모 네트워크에서, 추가 비용 없이 **기존 라우터를 DHCP 서버로 활용**하는 데 유용합니다.


구성 시나리오

- **네트워크 환경**: R1 라우터 (IP: 10.10.10.1/24), 서브넷 10.10.10.0/24
- **DNS 서버**: 10.10.20.10
- **DHCP 제외 주소**: 10.10.10.1~10.10.10.10


DHCP 구성 단계

1. **주소 제외 설정**
   - 일부 장치에 고정 IP를 할당하기 위해 **DHCP 범위에서 제외할 주소**를 설정합니다.
   ```plaintext
   ip dhcp excluded-address 10.10.10.1 10.10.10.10
   ```
  메모: 주로 네트워크 기반 장치인 프린터나 라우터가 해당됨. 프린터는 아마 무선 출력 기능 때문에 그런듯?

2. **DHCP 풀 구성**
   - **IP 범위 및 서브넷**을 지정하고, **기본 게이트웨이와 DNS 서버 주소**를 설정합니다.
   ```plaintext
   ip dhcp pool <이름>
   network 10.10.10.0 255.255.255.0 - dhcp 풀
   default-router 10.10.10.1  - 기본 게이트웨이
   dns-server 10.10.20.10  - dns 서버
   ```

구성 예시

1. **주소 제외** (10.10.10.1~10.10.10.10)
   ```plaintext
   config t
   ip dhcp excluded-address 10.10.10.1 10.10.10.10
   ```

2. **DHCP 풀 생성** (`Demo`라는 이름으로 구성)
   ```plaintext
   ip dhcp pool Demo
   network 10.10.10.0 255.255.255.0
   default-router 10.10.10.1
   dns-server 10.10.20.10
   ```

검증 명령어

메모: 클라이언트는 따로 지정을 안해줘도, 알아서 브로드캐스트를 통해 IP를 요청하고 할당받는다.

- **DHCP 풀 확인**: `show ip dhcp pool`  
- **할당된 IP 확인**: `show ip dhcp binding`

예를 들어, **10.10.10.11**이 **MAC 주소 D116** 클라이언트에 할당된 것을 확인할 수 있습니다.

### Cisco 라우터의 외부 DHCP 서버 지원 설정

이번 강의에서는 **Cisco 라우터가 외부 DHCP 서버를 지원**하도록 설정하는 방법을 살펴보겠습니다. 이 설정은 **다수의 서브넷을 가진 대규모 네트워크**에서 주로 사용되며, 네트워크의 중심에 **외부 DHCP 서버**를 두어 IP 할당을 관리하는 방식입니다.

시나리오 개요

- **네트워크 구성**:
  - **라우터**: R1 (인터페이스 F0/1, 10.10.10.1/24)
  - **외부 DHCP 서버**: 10.10.20.10 (DNS 서버로도 사용)
- **PC 구성**: DHCP 클라이언트로 구성된 PC2

문제점 및 해결 방안

1. **문제점**:
   - PC2가 DHCP 요청(브로드캐스트 트래픽)을 보내면, 라우터는 이 요청을 외부 서브넷으로 전달하지 않습니다. 따라서 PC2는 DHCP 서버에 도달하지 못해 IP 주소를 할당받을 수 없습니다.

2. **해결 방안**:
   - 라우터의 클라이언트 측 인터페이스에 **DHCP 릴레이 에이전트** 설정을 추가합니다.
   - **ip helper-address 명령어**를 사용하여 라우터가 DHCP 요청을 외부 서버(10.10.20.10)로 전달하게 구성합니다.

설정 절차

1. **ip helper-address 설정**:
   - 라우터에서 클라이언트와 연결된 인터페이스(F0/1)로 이동하여 다음 명령어를 입력합니다:
   ```plaintext
   config t
   interface f0/1
   ip helper-address 10.10.20.10
   ```

2. **DHCP 서버 설정**:
   - DHCP 서버에서 10.10.10.0 서브넷에 대한 IP 범위, 서브넷 마스크, 기본 게이트웨이, 그리고 DNS 서버를 설정합니다.
   - 예시 설정:
     - **IP 범위**: 10.10.10.100부터
     - **서브넷 마스크**: /24
     - **기본 게이트웨이**: 10.10.10.1
     - **DNS 서버**: 10.10.20.10


### 윈도우 / 맥 / 리눅스에서 설정하는 법 설명

별로 중요하지 않고, GUI라서 쉽게 찾을 수 있으므로 생략

### Cisco 라우터를 DHCP 클라이언트로 구성하기

이번 강의에서는 **Cisco 라우터를 DHCP 클라이언트로 구성**하는 방법을 알아보겠습니다. 보통 라우터는 **수동으로 IP 주소**를 설정하지만, **인터넷에 연결된 지점 사무실** 등에서는 외부 서비스 제공자(ISP)로부터 IP 주소를 DHCP로 할당받아야 할 때가 있습니다.

DHCP 클라이언트로 구성하는 이유

- **고정 IP 비용 절감**: 사무실에 외부에서 접근해야 하는 서버가 없고, 고정된 공인 IP 주소가 필요하지 않은 경우입니다.
- **NAT 구성**: 지점 사무실에서 내부 호스트가 인터넷에 접속할 수 있도록 **단 하나의 공인 IP 주소**만 있으면 됩니다. 이때, ISP의 DHCP 서버로부터 동적 IP 주소를 받아 NAT를 통해 인터넷에 연결하게 됩니다.

구성 절차

1. **외부 인터페이스 DHCP 설정**:
   - 라우터의 **ISP를 마주하는 외부 인터페이스**를 DHCP 클라이언트로 구성해야 합니다.
   - 예시 명령어:
     ```plaintext
     config t
     interface f0/0
     ip address dhcp
     no shutdown
     ```

2. **DHCP 임대 정보 확인**:
   - DHCP 설정 후에는 **show dhcp lease** 명령어로 할당된 IP 주소 및 임대 정보를 확인할 수 있습니다.
구성 예시

1. **인터페이스 설정**:
   - **외부 인터페이스(F0/0)**에 DHCP 주소를 할당하고 인터페이스를 활성화합니다.
     ```plaintext
     config t
     interface f0/0
     ip address dhcp
     no shutdown
     ```

2. **IP 주소 임대 확인**:
   - 설정 후 약간의 시간이 지나면 DHCP 서버에서 IP 주소가 할당됩니다.
   - `show dhcp lease` 명령어로 할당된 IP 주소와 DHCP 서버 주소를 확인합니다.
     - 할당된 IP 주소 예시: `203.0.113.2`
     - DHCP 서버 주소 예시: `203.0.113.1`

3. **인터페이스 상태 확인**:
   - `show ip int brief` 명령어로 인터페이스 상태 및 IP 할당을 다시 한번 확인할 수 있습니다.
     - F0/0 인터페이스에 할당된 DHCP IP 주소가 `203.0.113.2`임을 확인합니다.

메모: 추가 설명

회사 사무실의 컴퓨터가 DHCP 클라이언트로서 사내 DHCP 서버로부터 IP 주소를 할당받아 인터넷을 사용할 수 있는 것처럼, 
지점 사무실의 라우터도 ISP의 DHCP 서버로부터 공인 IP 주소를 할당받아 외부 인터넷과 연결될 수 있다.

외부에서 이 IP에 접근할 필요가 없는 경우에 사용된다. 

회사의 경우에는 IP를 제한해야 하니까 고정 IP를 사용하고, 비용이 들겠지만 가정용의 경우 굳이 고정 IP를 구매할 이유가 없다.

구글에서 "통신사 dhcp 임대시간" 같은 걸 검색하면 공유기 설정에 들어가서 [DHCP 설정을 변경하는 방법을 알려주는 글](https://sealplay.com/bbs/board.php?bo_table=tip&wr_id=10042)이 많다.

### 느낀점.

이제 브로드캐스트, 유니캐스트, 스위치나 라우터의 동작이 별로 낯설지 않다. 4계층 아래의 일을 공부하고 있지만, 나중에 4계층 위의(소켓 통신) 작업을 할때도 도움이 될 것이라 느낌.

사람들 IP를 서로 바꿔서 할당되다 보니까 여러 인터넷 글에서 "이미 추천된 글입니다." 같은 일이 발생하는 듯? 물론 그거만 있는건 아니겠지만, 왜 같은 집에 살지도 않는 사람들이 같은 IP를 사용할 수 있는지 이유를 알게됨.

윈도우나 맥 설정에서 DHCP 관련한거 보기만 했지, 뭐하는건지는 하나도 몰랐는데 이제 이해감.



---

> Source: `section_24/ysj/note.md`

## Section 24 정리

### 강의 요약: 네트워크 다중화

1. 네트워크 다중화 개요
- **다중화**란 단일 장애 지점을 제거하여 네트워크의 신뢰성을 높이는 방법입니다.
- 예시 네트워크는 전혀 다중화가 되지 않은 상태로, 단일 장애 지점이 존재합니다.

2. 네트워크 구성
- **구성 요소**:
  - **SP 라우터**: 서비스 제공자 라우터
  - **R1**: 기업 WAN 에지 라우터
  - **코어 분배층 스위치 및 액세스 스위치**: 각각 하나씩 존재

- **문제점**: 
  - R1, 코어 스위치, 액세스 스위치 중 하나라도 꺼지면 PC는 연결성을 잃습니다.

3. 다중화 필요성
- 소규모 사무실에서는 다중화를 위한 추가 장치 설치로 인해 비용이 증가할 수 있지만, 대규모 사무실에서는 운영 중지 비용이 더 크기 때문에 다중화가 필요합니다.

4. 다중화 구현
- **예시 네트워크**:
  - R1과 R2 두 개의 WAN 에지 라우터가 각각 SP1과 SP2에 연결.
  - 코어 분배층 스위치와 액세스층 스위치가 다중화됨.

- **장점**:
  - 서비스 제공자 라우터, WAN 에지 라우터, 코어 스위치 중 하나의 연결이 끊어져도 연결성이 유지됩니다.

5. 백업 경로 설정
- **R1의 경로 설정**:
  - 기본 정적 경로: `ip route 0.0.0.0 0.0.0.0 203.0.113.1`
  - 백업 경로: `ip route 0.0.0.0 0.0.0.0 10.10.20.2` (관리 거리 5)

- **트래픽 처리**:
  - R1에서의 트래픽은 SP1으로 우선 전송되며, SP1이 꺼질 경우 R2를 통해 SP2로 전송됩니다.

6. **FHRP(게이트웨이 다중화 프로토콜)**
- **FHRP의 역할**: 다중 게이트웨이를 통해 자동으로 대체 라우터로 전환하여 PC의 재구성을 방지합니다.
- **가상 IP 주소**: R1과 R2는 가상의 IP 주소를 협의하여 사용합니다 (예: 10.10.10.1).

7. FHRP 프로토콜 종류
- **HSRP** (핫 스탠바이 라우터 프로토콜): Cisco 전용, 활성/대기 구성.
- **VRRP** (가상 라우터 다중화 프로토콜): 공개 표준, HSRP와 유사한 기능.
- **GLBP** (게이트웨이 부하 균형 프로토콜): 활성/활성 부하 분배 지원.

### HSRP (Hot Standby Router Protocol)

이번 강의에서는 Cisco의 **핫 스탠바이 라우터 프로토콜(HSRP)**에 대해 배웁니다. HSRP는 자동으로 게이트웨이를 대체할 수 있도록 가상 IP(VIP)와 MAC 주소를 사용하는 프로토콜입니다.

HSRP 개요
- **HSRP의 목적**: 다중 기본 게이트웨이 구성.
- **구성 라우터**:
  - R1: 물리적 IP 10.10.10.2
  - R2: 물리적 IP 10.10.10.3
- **가상 IP**: 10.10.10.1

작동 원리
- R1과 R2는 HSRP를 통해 하나는 활성(active) 라우터, 다른 하나는 대기(standby) 라우터로 설정됩니다.
- 활성 라우터는 가상 IP 주소(10.10.10.1)와 관련된 가상 MAC 주소를 소유합니다.
- 두 라우터는 주기적으로 Hello 신호를 주고받으며, 대기 라우터는 활성 라우터의 Hello 신호를 받지 못하면 활성 상태로 전환됩니다.
- PC는 기본 게이트웨이로 10.10.10.1을 사용하며, HSRP의 작동을 인식하지 못합니다.

구성 및 검증
1. **R1 구성**:
   - `interface gigabitEthernet0/1`
   - `ip address 10.10.10.2 255.255.255.0`
   - `no shutdown`
   - `standby 1 ip 10.10.10.1`
2. **R2 구성**:
   - `interface gigabitEthernet0/1`
   - `ip address 10.10.10.3 255.255.255.0`
   - `no shutdown`
   - `standby 1 ip 10.10.10.1`
   
구성 후 `show standby` 명령어로 HSRP 상태를 확인합니다.

HSRP 고급 주제
1. **우선순위(priority)**:
   - 기본값: 100. 
   - 우선순위가 높은 라우터가 활성 상태가 됨.
   - 선점을 활성화하면, 우선순위가 높은 라우터가 장애 후 복구 시 활성 상태로 돌아옴.
   
2. **버전 관리**:
   - HSRP 버전 2는 개선 사항을 포함.
   - 두 라우터 모두 동일한 버전을 실행해야 함.

부하 분산

1. **HSRP 그룹을 사용한 부하 분산**:
   - 두 개의 HSRP 그룹을 설정하여 서로 다른 가상 IP를 사용할 수 있습니다.
   - 예시: R1은 10.10.10.1, R2는 10.10.10.254를 가상 IP로 설정.
   
2. **서브넷을 통한 부하 분산**:
   - 각 서브넷을 다른 라우터에 매핑하여 부하를 분산할 수 있습니다.
   - 예: R1은 10.10.10.0 서브넷, R2는 10.10.20.0 서브넷의 활성 라우터로 설정.



---

> Source: `section_25/ysj/note.md`

## Section 25 정리

## 네트워크 토폴로지와 스패닝 트리 및 중복 장치 구성을 통한 이중화 복습 - 3계층의 루프

### 1. **네트워크의 3계층 복습**
   - **라우팅과 경로 선택**: 3계층에서는 라우터가 경로 선택을 담당하며, 정적 경로나 동적 라우팅 프로토콜을 통해 트래픽을 최적화합니다. 
   - **HSRP (Hot Standby Router Protocol)**: 라우터 R1과 R2에 HSRP를 설정하여 장애 발생 시 자동으로 경로를 전환하게 했습니다. HSRP는 가상 IP(VIP)를 제공하여 기본 게이트웨이를 동적으로 대체합니다.

### 2. **이중화 및 장애 조치**
   - **주 경로와 백업 경로**: R1에서 SP1로 향하는 기본 경로와, SP1 장애 시 SP2를 통한 백업 경로를 설정하여 이중화했습니다. 이 경우, 관리 거리를 통해 우선순위를 설정해 더 나은 경로가 먼저 선택되도록 하였습니다.
   - **라우팅 루프 방지**: 정적 경로로 잘못 구성하면 라우팅 루프가 발생할 수 있습니다. 예를 들어, R1에서 10.10.50.0 네트워크로 가는 경로를 SP1으로 지정하고, SP1에서 SP2, SP2에서 다시 R2로 전달되는 경로를 구성할 때 루프가 생길 수 있습니다. 이를 방지하기 위해 TTL(Time To Live) 필드를 사용하여 패킷이 특정 횟수만큼 라우터를 통과하면 버려지도록 설정했습니다.
    - 패킷이 실패하면 처음 전송된 출발지에 ICMP 시간 초과 메시지를 보낸다.

### 3. **2계층 스위치 네트워크에서의 루프 방지**
   - **스패닝 트리 프로토콜(STP)**: 2계층에서는 라우팅이 아닌 스패닝 트리를 통해 네트워크 루프를 방지합니다. STP는 2계층에서 루프 방지와 경로 선택을 자동화하여 네트워크 안정성을 유지합니다.

이번 강의는 3계층 라우팅과 중복성 설정에 대한 기초와, 의도치 않게 발생할 수 있는 라우팅 루프를 방지하는 TTL 필드의 역할에 대해 자세히 설명하였습니다.

## 스패닝 트리 프로토콜(STP)의 존재 이유

이번 강의는 **스패닝 트리 프로토콜**(STP)의 필요성을 이해하는 데 집중합니다.

1. **이더넷 경로 설정 개념**
   - 네트워크에서 각 스위치가 MAC 주소 테이블을 통해 경로를 설정합니다.
   - 예시로 PC1이 R1의 IP 주소(10.10.10.2)로 트래픽을 보내려는 상황을 사용합니다.
   - PC1이 R1과 통신 기록이 없을 경우, **ARP 요청**을 통해 네트워크 전체에 브로드캐스트 트래픽을 발생시킵니다.

2. **스패닝 트리 프로토콜의 필요성**
   - **브로드캐스트 트래픽의 무한 루프** 문제: 스패닝 트리가 없으면 브로드캐스트 트래픽이 계속 순환하며 루프가 발생하게 됩니다.
   - 이때, 스위치들이 계속해서 트래픽을 재전송하여 **브로드캐스트 스톰**이 발생하고 네트워크가 과부하되어 작동이 멈출 수 있습니다.
   - 제2계층 네트워크의 이더넷 헤더에는 **TTL(Time to Live)** 값이 없어, 루프가 멈추지 않고 계속됩니다.

3. **스패닝 트리의 역할**
   - STP는 **루프 방지**를 위해 스위치 포트를 차단하여, 물리적 경로가 연결되어 있어도 논리적으로 네트워크 루프를 차단합니다.
   - 이를 통해 브로드캐스트 스톰을 방지하고 네트워크를 안정적으로 유지합니다.
   - 예시에서, STP는 CD1과 CD2 사이, Acc3와 Acc4 사이의 루프를 방지하기 위해 특정 포트를 비활성화했습니다. 이를 통해, 필요할 때는 포트를 활성화하여 장애 발생 시 대체 경로를 제공합니다.

4. **스패닝 트리의 한계**
   - **대역폭 제한**: 일부 포트를 비활성화함으로써 이용 가능한 물리적 대역폭을 줄이게 됩니다.
   - **느린 수렴 시간**: 장애 감지 후 복구가 이루어질 때 최대 50초가 소요될 수 있습니다.
   - STP의 단점은 물리적으로 연결된 인터페이스를 비활성화하여 대역폭을 감소시킨다는 점과 수렴 속도가 느리다는 것입니다. STP가 네트워크의 모든 경로를 확인하고 안정적인 상태로 수렴하는 데 최대 50초까지 소요될 수 있습니다.

5. **스패닝 트리와 장애 조치**
   - STP는 자동으로 장애를 감지하고 차단된 포트를 활성화해 대체 경로를 제공합니다.

이로써 STP는 이더넷 네트워크에서 발생할 수 있는 루프를 방지하는 데 필수적임을 알 수 있습니다.

## 허브, 브리지, 스위치

#### 1. 허브 (Legacy)
- **정의**: 제1계층 장치로 가장 기본적인 네트워크 연결 장비
- **특징**:
  - MAC 주소 학습 불가
  - 모든 트래픽을 모든 포트로 전송 (송신 포트 제외)
  - 브로드캐스트/유니캐스트/멀티캐스트 트래픽 모두 전체 전송
  - 현재는 완전히 단종됨

#### 2. 브리지 (Bridge)
- **정의**: 제2계층 장치로 허브와 스위치의 중간 단계
- **주요 특징**:
  - 2개의 포트 구성
  - MAC 주소 학습 가능
  - 충돌 도메인 분할 기능
- **역할**:
  - 대형 충돌 도메인을 2개의 작은 도메인으로 분할
  - 필요한 트래픽만 선별적으로 전달

#### 3. 스위치 (현재 표준)
- **정의**: 브리지의 현대화 버전
- **특징**:
  - 다중 포트 지원
  - 향상된 성능과 보안
  - 스마트한 트래픽 관리

#### 용어 사용의 실제
- **스패닝 트리 관련**: 브리지 시대의 용어 계승
  - 루트 브리지
  - BPDU (Bridge Protocol Data Unit)
- **현대적 사용**:
  - 일반적 상황: '스위치' 사용
  - 기술 문서/프로토콜: '브리지' 용어 잔존 - 스패닝 트리 프로토콜을 학습할 때 '브리지'라는 용어가 자주 등장함.

## 스패닝 트리 작동 방식 요약

#### 1. **스패닝 트리 개요**
   - **스패닝 트리 프로토콜 (STP)**: 모든 벤더의 스위치에 기본적으로 활성화된 네트워크 루프 방지 표준.
   - **목적**: 브로드캐스트 폭풍과 같은 네트워크 루프 문제를 방지함으로써 안정적인 LAN 환경을 유지.

#### 2. **BPDU의 역할**
   - **BPDU (Bridge Protocol Data Unit)**: 스위치가 루프를 감지하고 트래픽을 전달할 준비가 될 때까지 사용.
   - **과정**: 스위치가 루프가 없는지를 확인하는 동안 트래픽은 차단 상태가 되며, 루프가 없다고 확정되면 전달 상태로 전환.

#### 3. **루트 브리지 선출**
   - **루트 브리지**: 네트워크 상에서 트래픽 경로를 결정하는 기준이 되는 스위치.
   - **선출 기준**:
     - **브리지 우선순위 값** (기본값 32768, 낮을수록 우선).
     - 우선순위가 같다면 **MAC 주소**가 낮은 스위치가 선택.

#### 4. **스패닝 트리 경로 비용 계산**
   - **비용 계산**: 스위치가 루트 브리지까지의 경로 중 가장 낮은 비용 경로를 선택.
   - **인터페이스 대역폭 선호**: 더 높은 대역폭의 인터페이스가 비용이 낮음. 예: 기가비트 이더넷(비용 4) > 고속 이더넷(비용 19).
   - **숏 모드 vs 롱 모드**:
     - **숏 모드**: 원래 방식으로 20Gbps까지 지원.
     - **롱 모드**: 더 세분화된 32비트 값으로 최신 고속 네트워크 지원.

#### 5. **루트 포트와 지정 포트**
   - **루트 포트**: 각 스위치가 루트 브리지로 도달하기 위한 최저 비용 경로에 해당하는 포트.
   - **지정 포트**: 루트 포트와 반대편에 위치하며 네트워크 트래픽을 전달하는 경로 역할을 함.
   - 루트 브리지에서 멀어지는 모든 포트는 **지정 포트**가 된다.

#### 6. **트래픽 경로 설정과 루프 방지**
   - **최적 경로**: 스위치가 루트 브리지로의 최적 경로를 계산하고, 해당 경로로 트래픽을 전달.
   - **루프 방지**: 잠재적인 루프 경로는 스패닝 트리에 의해 차단되어, 네트워크가 안정적으로 유지됨.

#### 7. **장애 조치(Failover)와 비용 조정**
   - 스패닝 트리가 링크 장애를 감지하면 다른 경로로 장애 조치하여 네트워크 연속성 유지.
   - **비용 조정**: 인터페이스 비용을 조정하여 경로를 변경 가능.

### 좀 더 구체적인 버전

### 스패닝 트리 프로토콜(STP)의 작동 원리: 스위치 네트워크의 안정성을 위한 핵심 기법

이번 강의에서는 네트워크 상의 루프를 방지하기 위한 **스패닝 트리 프로토콜(STP)**의 작동 방식에 대해 자세히 살펴보겠습니다. STP는 여러 스위치가 상호 연결된 복잡한 네트워크 환경에서 루프를 방지하고, 네트워크의 안정성을 유지하기 위해 모든 스위치에서 기본적으로 활성화되어 있는 산업 표준 프로토콜입니다.

#### 1. 스패닝 트리 프로토콜(STP)의 중요성

로컬 영역 네트워크(LAN)에서 루프가 발생하게 되면, 데이터 패킷이 끝없이 순환하게 되어 **브로드캐스트 폭풍**이라는 심각한 문제를 야기할 수 있습니다. 브로드캐스트 폭풍은 네트워크의 가용성을 저하시킬 뿐만 아니라, 모든 장비에 부담을 주어 전체 네트워크의 성능을 저하시키게 됩니다. **STP**는 이러한 루프를 방지하고 네트워크 상의 안정성을 보장하기 위해 사용됩니다. 

#### 2. BPDU(Bridge Protocol Data Unit)와 스위치 네트워크 구성

스위치가 온라인 상태로 전환되면 **BPDU**라는 메시지를 전송하여 인접 스위치와의 상호 연결 상태를 확인하고, 잠재적인 루프를 감지합니다. 스위치의 각 포트는 루프가 발생할 가능성이 없다는 것이 확실해질 때까지 트래픽을 전달하지 않으며, 초기에는 차단 상태에 있게 됩니다. 스위치 간에 BPDU 메시지를 통해 상호 간의 브리지 ID를 공유하게 되며, 브리지 ID는 해당 스위치를 식별하는 고유한 값입니다.

#### 3. 브리지 ID(Bridge ID)와 루트 브리지 선정

BPDU에는 스위치의 **브리지 ID**가 포함되며, 이는 스위치의 고유 MAC 주소와 관리자가 정의한 **브리지 우선순위** 값으로 구성됩니다. 브리지 우선순위는 0에서 65535 사이의 값을 가지며, 기본값은 32768입니다. STP는 네트워크에서 가장 낮은 브리지 ID 값을 가진 스위치를 **루트 브리지**로 선정합니다. 브리지 우선순위가 같을 경우에는 MAC 주소가 가장 낮은 스위치가 루트 브리지로 선택됩니다. 루트 브리지는 네트워크의 중심 역할을 하며, 모든 스위치들은 루트 브리지에 도달하기 위한 최적의 경로를 계산하고 해당 경로를 통해 트래픽을 전달하게 됩니다.

#### 4. 루트 브리지에 도달하는 경로 결정

각 스위치는 루트 브리지로의 최적 경로를 계산하기 위해 링크의 대역폭을 고려하여 비용을 산정합니다. STP에서는 **링크의 대역폭이 높을수록 비용이 낮아지며**, 스위치는 비용이 가장 낮은 경로를 선택하여 루트 브리지로의 최적 경로를 설정하게 됩니다. 네트워크 상의 모든 스위치들은 루트 브리지에 도달하기 위한 루트 포트를 설정하고, 가장 적절한 경로만 트래픽을 전달하게 되므로 루프가 방지됩니다.

#### 5. 스패닝 트리 모드의 종류: Short Mode와 Long Mode

STP는 **Short Mode**와 **Long Mode**라는 두 가지 모드를 가지고 있으며, 기본적으로 **Short Mode**가 활성화되어 있습니다. **Short Mode**에서는 1기가비트 이상의 인터페이스에 대해 고정 비용을 할당하여 속도 차이에 따른 추가적인 분류가 어렵습니다. 그러나 현대 네트워크에서는 1기가비트 이상의 대역폭을 가진 링크가 일반적이므로, **Long Mode**를 사용하여 더 높은 대역폭을 가진 링크를 선호하게 설정할 수 있습니다.

#### 6. STP의 작업 절차: 루트 브리지 선정과 트래픽 경로 최적화

스위치들이 서로 연결되면, 스위치들은 **BPDU**를 주고받으며 자신들의 **브리지 ID**를 광고합니다. STP는 다음과 같은 단계로 작동합니다:

1. **루트 브리지 선출**: BPDU 메시지를 통해 각 스위치는 가장 낮은 브리지 ID를 가진 스위치를 **루트 브리지**로 선정하게 됩니다.
2. **루트 포트 설정**: 각 스위치는 루트 브리지에 도달하기 위한 최적 경로를 찾아 **루트 포트**로 설정하고, 그 경로를 통해 트래픽을 전달합니다.
3. **지정 포트 설정**: 각 링크의 반대쪽 포트는 지정 포트로 설정됩니다. 루트 포트는 루트 브리지로의 최적 경로를 의미하고, 지정 포트는 해당 링크를 통해 트래픽이 전달될 수 있는지를 나타냅니다.
   
STP가 모든 루프를 방지할 수 있도록 설정이 완료되면 네트워크에서 루프가 형성될 가능성이 있는 포트들은 차단 상태로 전환됩니다. 예를 들어, 네트워크 상에서 두 개의 스위치가 루트 브리지로 가기 위한 동일한 비용의 경로를 가지고 있다면, STP는 가장 낮은 브리지 ID를 가진 스위치와 연결된 경로를 통해 트래픽을 전송하도록 선택하고, 나머지 경로는 차단하게 됩니다.

#### 7. 링크 실패 시의 장애 조치

STP는 장애 조치 기능도 제공합니다. 만약 루트 브리지로의 주요 경로가 실패할 경우, STP는 차단된 예비 경로를 활성화하여 트래픽을 우회시킵니다. 예를 들어, 루트 브리지와의 연결이 단절되면 스위치들은 자동으로 예비 경로를 탐지하고, 그 경로를 통해 트래픽을 전송하게 됩니다.

#### 8. 경로 조작: 인터페이스 비용 변경

관리자는 각 링크의 비용을 수동으로 변경하여 트래픽 경로를 조정할 수 있지만, 이 경우 모든 스위치에 동일한 설정을 적용해야 네트워크 혼란을 방지할 수 있습니다. 예를 들어, 특정 링크의 비용을 낮게 설정하면 스위치는 해당 경로를 선호하게 되고, 트래픽이 그 경로로 유입되게 됩니다.

#### 9. STP와 부하 분산의 제한

스패닝 트리 프로토콜은 **동일 비용 부하 분산**을 지원하지 않습니다. 이는 STP가 네트워크 상의 단일 경로를 통해서만 트래픽을 전달하도록 설계되었기 때문입니다. 네트워크 상의 모든 스위치는 루트 브리지로의 최적 경로만 선택하게 되며, 동일한 비용을 가진 다수의 경로가 존재하더라도 하나의 경로만 활성화됩니다. 이로 인해 네트워크 상에서 다중 경로를 활용한 부하 분산에는 한계가 있습니다.

#### 10. 결론: 스패닝 트리 프로토콜의 역할과 한계

스패닝 트리 프로토콜(STP)은 네트워크 상의 루프를 방지하고, 스위치 네트워크의 안정성을 유지하기 위한 필수적인 프로토콜입니다. STP는 루트 브리지를 중심으로 모든 스위치가 최적 경로를 통해 트래픽을 전달하게 하며, 링크 실패 시에 자동으로 대체 경로를 설정하여 네트워크의 연속성을 보장합니다. 그러나 STP는 다중 경로 부하 분산을 지원하지 않기 때문에, 고도화된 네트워크 환경에서는 스패닝 트리와 함께 다중 경로 프로토콜(Multipath Protocol)과 같은 부하 분산 기능을 갖춘 네트워크 프로토콜을 결합하여 사용해야 할 필요가 있습니다.

---

#### 포트의 종류

맞습니다. 스패닝 트리 프로토콜(STP)에서는 포트의 종류가 **3가지**로 구분됩니다. 각 포트는 스패닝 트리의 작동 과정에서 중요한 역할을 담당하며, 아래와 같은 세 가지 종류로 나뉩니다.

1. **루트 포트 (Root Port)**  
   - 각 스위치에서 **루트 브리지로 가는 최단 경로**를 담당하는 포트입니다.
   - 루트 포트는 모든 스위치에 하나씩만 존재하며, 루트 브리지에서는 루트 포트가 없습니다. 
   - 루트 포트는 루트 브리지에 연결되는 경로 중 비용이 가장 낮은 경로를 따라 트래픽을 전달합니다.

2. **지정 포트 (Designated Port)**  
   - 네트워크 세그먼트에서 루트 브리지로의 트래픽을 전송할 **대표 포트**입니다.
   - 지정 포트는 특정 네트워크 세그먼트에서 루트 브리지로 가는 가장 비용이 낮은 경로를 책임지며, 여러 스위치가 같은 네트워크 세그먼트에 연결된 경우 **하나의 지정 포트만 활성화**됩니다.
   - 루트 포트와 반대로 지정 포트는 네트워크 세그먼트마다 하나씩 존재합니다.

3. **차단 포트 (Blocking Port)**  
   - 루프를 방지하기 위해 트래픽을 전송하지 않도록 **차단된 상태**로 유지되는 포트입니다.
   - 차단 포트는 루프를 방지하고 네트워크 안정성을 확보하기 위해 지정되며, 활성화된 루트 포트와 지정 포트 이외의 모든 포트가 차단 포트가 됩니다.
   - 차단 포트는 BPDU 메시지만 수신하고 데이터 트래픽을 전송하지 않습니다.

#### 추가 설명: 포트 상태와 장애 복구

각 포트는 STP의 동작 상태에 따라 **포트 상태**가 변할 수 있습니다. 예를 들어, 링크에 문제가 생기면 차단된 포트가 루트 포트나 지정 포트로 전환될 수 있습니다. 이 경우 네트워크는 자동으로 장애 복구가 이루어져 데이터 전송이 재개됩니다.


## 1. 스패닝 트리 프로토콜(STP) 표준

이번 강의는 스패닝 트리의 다양한 버전에 대해 설명하며, 개방형 표준과 Cisco 독점 버전을 비교하고 각 버전의 특징과 차이점을 소개합니다. 

스패닝 트리의 최초 구현은 **IEEE 802.1D**로, 이는 하나의 스패닝 트리 인스턴스를 사용하여 LAN의 모든 VLAN을 관리합니다. 그러나 802.1D는 최대 50초의 느린 수렴 시간을 가져 네트워크 루프 방지에 시간이 오래 걸리는 단점이 있습니다. 이를 해결한 개선 버전인 **IEEE 802.1w**는 **Rapid Spanning Tree Protocol (RSTP)**로, 수렴 시간을 크게 단축시켜 보통 몇 초 만에 네트워크 구성을 완료합니다. 하지만 RSTP 역시 모든 VLAN에 대해 하나의 스패닝 트리 인스턴스만을 사용하여 부하 분산에는 한계가 있습니다. 

산업 표준의 최신 버전인 **IEEE 802.1s**, 즉 **Multiple Spanning Tree Protocol (MSTP)**은 VLAN을 그룹화하여 여러 스패닝 트리 인스턴스로 분리할 수 있습니다. 이를 통해 VLAN을 네트워크에서 다른 경로로 분산하여 부하 분산을 지원할 수 있습니다. 
- 즉, VLAN별로 다른 루트 브릿지를 설정할 수 있음. 이후에 HSRP를 사용하여 VLAN 부하 분산 + 백업 루트 브릿지를 설정할 때 사용됨.
  - 백업 자체는 그룹이 없어도 상관 없는데, VLAN 그룹 단위로 부하분산을 하는데 유용함.

### 2. Cisco 독점 버전

Cisco는 독점적으로 **Per VLAN Spanning Tree Plus (PVST+)**와 **Rapid PVST+**를 제공합니다. PVST+는 802.1D와 유사하지만 각 VLAN에 대해 별도의 스패닝 트리 인스턴스를 만들어 부하 분산을 가능하게 합니다. 그러나 802.1D와 마찬가지로 느린 수렴 시간의 한계가 있습니다. 이를 개선한 Rapid PVST+는 **802.1w**의 RSTP와 유사하며, 빠른 수렴 시간을 지원합니다. 

Cisco의 PVST+와 Rapid PVST+는 MSTP와의 주요 차이점이 각 VLAN마다 독립적인 스패닝 트리 인스턴스를 사용하는 점입니다. MSTP에서는 여러 VLAN을 하나의 그룹으로 묶을 수 있어 스위치에 가해지는 부하를 줄일 수 있는 반면, Cisco의 PVST+ 및 Rapid PVST+에서는 VLAN 단위로 별도의 인스턴스를 계산하기 때문에 스위치에 더 많은 부하를 가하게 됩니다.

### 3. 부하 분산 예시

부하 분산의 예를 들어 보면, 액세스 계층 스위치가 두 개의 코어 분배 스위치(CD1, CD2)에 연결된 상황에서 VLAN을 활용해 트래픽을 분산합니다. 예를 들어 CD1을 VLAN 10~19의 루트 브리지로 설정하고, CD2를 VLAN 20~29의 루트 브리지로 설정하여 트래픽이 각 루트 브리지로 향하는 경로를 다르게 설정합니다. MSTP나 PVST+를 통해 장애 발생 시 트래픽이 자동으로 다른 링크로 페일오버되어 안정성을 보장합니다.

### 4. 스패닝 트리 버전 선택과 명령어

스패닝 트리 버전은 네트워크의 특정 요구 사항과 스위치의 모델에 따라 선택할 수 있습니다. **`spanning-tree mode`** 명령어로 스위치에서 사용할 스패닝 트리 모드를 선택할 수 있으며, 일반적으로 Cisco 스위치는 PVST+와 Rapid PVST+, MST를 지원합니다. 실행 중인 스패닝 트리 모드를 확인하기 위해 **`show spanning-tree summary`** 명령어를 사용하며, PVST+에서 Rapid PVST+로 전환할 때 기존 구성을 유지하고 빠른 수렴 속도의 이점을 누릴 수 있습니다.

### 5. 주의 사항: 스패닝 트리 용어와 버전 구분

스패닝 트리 용어 중에서 **차단 포트**는 Cisco에서는 **대체 포트**로 표기되며, 이는 현재는 차단 상태이지만, 장애 발생 시 활성화될 수 있는 포트를 의미합니다. 

강의에서는 표준 버전별 명확한 구분을 위해 용어의 혼동을 피하도록 강조합니다.

## 스패닝 트리 프로토콜(STP) 검증 명령어 정리

#### 1. 기본 검증 명령어
```
show spanning-tree vlan [VLAN번호]
```
- VLAN을 지정하지 않으면 모든 VLAN의 스패닝 트리 정보 표시
- 많은 VLAN이 있을 경우 출력이 길어지므로 특정 VLAN 지정 권장

#### 2. 명령어 출력 구조

(생략함)

#### 3. 포트 상태 확인
- **포워딩(Forwarding)**: 트래픽 전송 가능
- **차단(Blocking)**: 루프 방지를 위해 비활성화
- **지정(Designated)**: 세그먼트에 대한 지정 포트
- **루트(Root)**: 루트 브리지로 가는 최적 경로 포트

#### 4. 비용 계산
- FastEthernet 링크 비용: 19
- 총 경로 비용 = 경로상의 모든 링크 비용의 합
- 예시: 
  ```
  스위치A → FastEthernet → 스위치B → FastEthernet → 루트
  총 비용 = 19 + 19 = 38
  ```

#### 5. 실제 사용 팁
- 스패닝 트리 토폴로지 파악을 위해서는 각 스위치별로 명령어 실행 필요
- 토폴로지 매핑을 위해 연필과 종이 사용 권장
- 루트 브리지 확인 후 각 스위치의 포트 상태 순차적 확인


# MAC 주소 테이블을 이용한 트래픽 경로 검증

#### 1. 기본 명령어
```cisco
# MAC 주소 테이블 확인
show mac address-table

# 인터페이스 정보 확인 (MAC 주소 포함)
show interface [interface-id]
```

#### 2. 트래픽 경로 검증 절차

1. 목적지 장치의 MAC 주소 확인
```cisco
show interface gigabitethernet 0/1
```

2. ARP 캐시 초기화 및 트래픽 생성
```cisco
clear arp-cache
ping [destination-ip]
```

3. 각 스위치에서 MAC 주소 테이블 확인
```cisco
show mac address-table | include [MAC주소]
```

#### 3. 검증 단계별 확인사항

1. **출발지 스위치**
   - MAC 주소가 학습된 출력 포트 확인
   - 예상 경로와 일치 여부 검증

2. **중간 스위치들**
   - 각 스위치에서 MAC 주소 테이블 확인
   - 트래픽 전달 포트 확인

3. **최종 목적지 스위치**
   - 목적지 장치로 연결된 포트 확인

#### 4. 트래픽 경로 분석 시 주의사항
- 최단 경로가 아닐 수 있음
- STP(스패닝 트리 프로토콜) 구성에 따라 경로가 결정됨
- 실제 네트워크에서는 최적화된 경로 설정 필요

#### 5. 문제 해결 팁
- MAC 주소 테이블이 비어있다면 트래픽 생성 필요
- 각 홉(hop)별로 순차적 확인
- 예상 경로와 실제 경로 비교 분석

## 스패닝 트리 루트 브리지 문제와 해결방안

#### 1. 문제 상황
- **기본 설정의 위험성**
  - 모든 스위치가 기본 우선순위(32768) 사용
  - MAC 주소가 가장 낮은 스위치가 루트 브리지가 됨
  - 주로 가장 오래된 스위치가 선택됨

- **문제점**
  - 오래된 스위치: CPU/메모리 제한적
  - 낮은 대역폭 링크 사용
  - 비효율적인 트래픽 경로
  - 과도한 홉 수로 인한 지연 발생

#### 2. 해결방안
##### 기본 전략
- 코어 스위치를 루트 브리지로 설정
- 백업 코어 스위치를 보조 루트로 설정

##### 구성 방법
1. **주 루트 브리지 설정**
   ```cisco
   spanning-tree vlan 1 root primary
   ```
   - 우선순위: 24576
   - 중앙 집중화된 경로 확보
   - 홉 수 감소

2. **보조 루트 브리지 설정**
   ```cisco
   spanning-tree vlan 1 root secondary
   ```
   - 우선순위: 28672
   - 주 루트 실패 시 백업 역할
   - 중앙 집중화된 경로 유지

#### 3. 기대 효과
- 트래픽 경로 최적화
- 네트워크 성능 향상
- 안정적인 백업 경로 확보
- 코어 스위치의 고성능 활용


## HSRP와 스패닝 트리 정렬 구성 가이드

#### 1. 목적
- 트래픽 경로 최적화
- 불필요한 홉 제거
- HSRP와 STP 경로 일치
- 효율적인 부하 분산

#### 2. 기본 구성 전략
##### VLAN 10 구성
```cisco
# R1 설정 (주 게이트웨이)
interface g0/1.10
 encap dot1q 10
 ip address 10.10.10.2 255.255.255.0
 standby 1 ip 10.10.10.1
 standby 1 priority 110
 standby 1 preempt

# CD1 설정 (주 스위치)
spanning-tree vlan 10 root primary
```

##### VLAN 20 구성
```cisco
# R2 설정 (주 게이트웨이)
interface g0/1.20
 ip address 10.10.20.3 255.255.255.0
 standby 1 ip 10.10.20.1
 standby 1 priority 110
 standby 1 preempt

# CD2 설정 (주 스위치)
spanning-tree vlan 20 root primary
```

#### 3. 부하 분산 효과
- VLAN 10 트래픽: PC → CD1 → R1
- VLAN 20 트래픽: PC → CD2 → R2
- 트래픽이 두 경로로 균등하게 분산

#### 4. 장애 대비
##### VLAN 10
- CD1 장애 시: CD2가 root secondary로 대체
- R1 장애 시: R2가 HSRP standby로 대체

##### VLAN 20
- CD2 장애 시: CD1이 root secondary로 대체
- R2 장애 시: R1이 HSRP standby로 대체

#### 5. 이점
- 최적화된 트래픽 경로
- 자동 페일오버 지원
- 효율적인 네트워크 리소스 활용
- 단일 장애 지점 제거

## 스패닝 트리와 관련된 네트워크 보호 기능

이 강의에서는 **스패닝 트리와 관련된 네트워크 보호 기능**들에 대해 설명합니다. 주요 기능으로는 **포트패스트(PortFast)**, **BPDU 가드** 및 **루트 가드**가 있으며, 이들은 네트워크 루프와 의도치 않은 루트 브리지 설정을 방지하여 네트워크 안정성을 유지하는 데 중요한 역할을 합니다.

### 1. 포트패스트 (PortFast)
- **문제**: 스위치 포트가 활성화될 때 스패닝 트리 프로토콜은 기본적으로 루프 방지를 위해 30초 동안 포트를 지연 상태로 둡니다. 하지만, PC 등 단일 연결을 갖는 엔드 장치는 루프를 형성할 가능성이 없기 때문에 이 지연이 불필요할 수 있습니다.
- **해결방법**: **포트패스트**를 활성화하면 엔드 호스트에 연결된 포트는 즉시 포워딩 상태로 전환되어, 장치가 빠르게 네트워크에 접속할 수 있게 됩니다.
- **설정 방법**: `spanning-tree portfast` 명령어를 사용하여 설정하며, 트렁크 포트가 아닌 액세스 포트에서만 사용해야 합니다. 특수한 경우에 트렁크 포트에서 포트패스트가 필요한 경우 `spanning-tree portfast trunk` 명령어를 사용하여 설정할 수 있습니다.
- 포트패스트 엣지: 포트패스트 엣지는 포트패스트의 기본 기능을 확장하여, 포트가 활성화된 후 즉시 포워딩 상태로 전환하도록 보장하는 동시에 보다 강력한 보안을 제공합니다. 스위치가 아닌 장비가 연결될 경우 해당 포트를 자동으로 비활성화하여 루프를 방지하는 추가적인 보안 기능을 제공하며, 이는 **"엣지 포트"**에서 주로 사용.


### 2. BPDU 가드 (BPDU Guard)
- **문제**: 포트패스트가 설정된 포트에 사용자가 스위치를 잘못 연결하면, 해당 포트에서 루프가 형성될 수 있으며, 이는 브로드캐스트 폭풍을 일으켜 네트워크 장애를 유발할 수 있습니다.
  - Host가 연결될 것이라 가정한 포트에서 스위치가 연결되고, 그게 다른 스위치랑 연결되면 루프가 발생할 수 있음. 따라서 포트패스트에서 BPDU가 오면 해당 포트를 비활성화
- **해결방법**: 포트패스트 포트에서 **BPDU 가드**를 활성화하면, BPDU (Bridge Protocol Data Unit)를 수신하는 순간 포트가 오류 비활성화 상태로 전환되어, 즉시 포트를 셧다운하고 루프를 방지합니다.
- **설정 방법**: 포트에 `spanning-tree bpduguard enable` 명령어를 추가하여 BPDU 가드를 활성화합니다. 자동 오류 복구 기능을 설정하지 않는 것이 좋습니다.

### 3. 루트 가드 (Root Guard)
- **문제**: 잘못된 스위치가 루트 브리지로 설정될 경우, 네트워크 트래픽 흐름이 의도치 않게 변경될 수 있습니다. 이는 구형 스위치를 새 네트워크에 연결하거나 공격자가 의도적으로 루트 브리지 변경을 시도할 때 발생할 수 있습니다.
- **해결방법**: **루트 가드**를 활성화하면, 루트 가드가 설정된 포트에서 더 우수한 BPDU를 수신할 경우, 해당 포트를 root-inconsistent 상태로 전환하여 트래픽이 전달되지 않도록 막습니다.
- **설정 방법**: `spanning-tree guard root` 명령어를 사용하여 특정 포트에 루트 가드를 설정합니다.

## BPDU 필터 vs BPDU 가드

- BPDU 가드: BPDU 수신 시 포트를 오류 비활성화
  - 권장 구성: 엔드호스트 포트에 포트패스트 + BPDU 가드
- BPDU 필터: BPDU를 필터링하지만 포트는 활성 상태 유지 
  - 일반적으로 사용 비권장 - 추가 연결 시 루프 발생 가능성 있음.
  - 예외적 사용: 구형 스위치와의 단일 하향 연결 시

## 루프 가드(Loop Guard) 정리

#### 1. 목적
- 단방향 링크 장애 방지
- 스패닝 트리 루프 방지
- 주로 광섬유 연결에서 발생하는 문제 해결

#### 2. 작동 방식
- 루트/차단 포트에서 BPDU 미수신 시 포트를 루프 불일치 상태로 전환
- BPDU 수신 재개 시 자동 복구
- 지정 포트에서는 작동하지 않음

#### 3. 설정 명령어
```cisco
# 전역 설정
Switch(config)# spanning-tree loopguard default

# 인터페이스별 설정
Switch(config-if)# spanning-tree guard loop
```

#### 4. 확인 명령어
```cisco
# 전체 상태 확인
show spanning-tree summary

# 특정 인터페이스 확인
show spanning-tree interface [interface-name] detail
```

#### 5. 주요 특징
- PVST+, RPVST+, MST 모두 지원
- 루트 가드와 동시 사용 불가
- 자동 복구 지원
- 단방향 링크 문제 예방

#### 6. 적용 지침
- 코어/디스트리뷰션 스위치 간 연결에 권장
- 엔드 호스트 연결 포트에는 불필요
- 루트 가드와 함께 사용 시 인터페이스 레벨에서 구성

## 191. CCNA v1.1: PVST+ versus RPVST+ Convergence - 생략 - 강의도 넘김.
## 192. CCNA v1.1: RPVST+ and Hub Interoperability - 생략 - 강의도 넘김.

# 요약 겸 리뷰

- STP: 2계층의 루프 방지 목적
  - 루트 브리지를 정하고, 루트 브리지를 기준으로 경로를 계산하고 네트워크 내 트리 구조를 생성.
    - 트리 구조에서 유추 가능하듯, 루프가 발생할 수 없음.
      - 이거랑 관련해서 생각난게, DFS, BFS에서는 접근한 노드를 기록해야 하지만, 트리는 구조 특성 상 그런거 없어도 알고리즘 문제 푸는데 지장 없었음.
    - 이 과정에서 스위치들은 BPDU를 주고 받음.
    - 연결된 인터페이스더라도, 루프 발생 가능성 때문에 Blocked인 경우 통신에 사용되지 않음.
    - 스위치가 차단되면 BPDU를 주고받아서 다시 경로를 설정함. (= 트리 구조가 깨짐. 트리 구조가 되도록 수정)
  - 최신 STP 프로토콜은 VLAN 그룹화가 가능해서 부하분산 + HSRP를 사용하여 SPOF 방지가 가능.
  - PortFast, BPDU Guard, Root Guard 등의 네트워크 보호 기능을 지원함.



---

> Source: `section_26/ysj/note.md`

## Section 26 정리

## EtherChannel의 개요와 구성

이 강의에서는 EtherChannel의 역할과 목적에 대해 설명합니다.

1. **캠퍼스 네트워크 구조**: 
   - PC 등 종단 호스트는 액세스층 스위치에 연결됩니다. 액세스층 스위치는 상위 분배층 스위치로 업링크되고, 분배층 스위치는 코어층 스위치로 연결됩니다. 
   - 종단 호스트는 네트워크 대역폭을 항상 사용하지 않으므로, 적은 수의 업링크로도 충분한 네트워크 성능을 유지할 수 있습니다.
   - 액세스층과 분배층의 초과 가입 비율은 보통 20:1이며, 분배층과 코어층은 4:1이 추천됩니다.

2. **대역폭 관리의 문제점**: 
   - 스패닝 트리는 루프 방지를 위해 다중화된 링크 중 하나만 활성화하고 나머지는 차단합니다. 따라서, 다중 링크 연결 시 대역폭 활용이 비효율적일 수 있습니다.
   - 예를 들어, 두 개의 10Gbps 링크를 연결하더라도 스패닝 트리가 하나를 막아 10Gbps만 사용하게 됩니다.

3. **EtherChannel의 활용**:
   - EtherChannel은 여러 물리적 링크를 하나의 논리적 인터페이스로 묶어 스패닝 트리가 차단하지 않고 모든 링크를 활용하게 합니다.
   - 이를 통해 20Gbps 등의 높은 대역폭을 확보하고 부하 분산과 다중화 기능을 제공합니다.

4. **EtherChannel의 작동 방식**:
   - EtherChannel은 하나의 흐름에 대해 특정 인터페이스를 할당하여 패킷을 부하 분산시키며, 라운드 로빈 방식이 아닌 흐름 단위로 부하를 분산합니다. 이는 패킷의 순서를 유지하여 안정적인 연결을 보장합니다.

5. **EtherChannel 프로토콜 종류**:
   - **LACP** (Link Aggregation Control Protocol): 개방형 표준으로 모든 스위치에서 지원되며, 가장 선호되는 프로토콜입니다.
   - **PAgP** (Port Aggregation Protocol): Cisco 전용으로 사용이 권장되지는 않습니다.
   - **Static**: 정적 프로토콜로 협상이 없으나 설정이 맞으면 포트 채널이 생성됩니다.

6. **EtherChannel 구성 명령어**:
   - `channel-group` 명령어를 통해 각 프로토콜을 지정하며 설정을 합니다.
   - 예를 들어, LACP는 `channel-group 1 mode active`로 설정하고, PAgP는 `channel-group 1 mode desirable`, 정적 프로토콜은 `channel-group 1 mode on`으로 설정합니다.

7. **구성 확인 방법**:
   - `show EtherChannel summary` 명령어로 EtherChannel의 상태를 확인합니다.

## 다중 섀시 EtherChannel 옵션

이 강의는 Cisco 스위치에서 다중 섀시 EtherChannel 옵션에 대해 설명하고 있습니다. Cisco StackWise, Virtual Port Channel(vPC), Virtual Switching System(VSS)과 같은 기술을 사용하여 스위치들 간의 연결을 향상하고 대역폭 활용을 극대화하는 방법을 다룹니다.

강의 요점을 정리해보면 다음과 같습니다:

1. **EtherChannel 개요**: EtherChannel은 다중 물리적 링크를 하나의 논리적 링크로 묶어 대역폭을 늘리고 링크의 안정성을 높이는 기술입니다. 하지만 일반 EtherChannel 설정에서는 스패닝 트리가 일부 링크를 차단하여 대역폭 활용에 제한이 생길 수 있습니다.

2. **다중 섀시(multi-chassis) EtherChannel(MEC)**: 여러 스위치가 연결된 환경에서 단일 포트 채널로 운영하여 스패닝 트리의 루프 차단 문제를 해결합니다. 이로 인해 모든 물리적 링크를 사용 가능하며, 전체 대역폭을 활용할 수 있습니다.

3. **Cisco의 MEC 옵션**:
   - **StackWise**: Catalyst 3750, 3850, 9000 등의 Catalyst 스위치 플랫폼에서 지원되며, 전용 케이블로 여러 스위치를 하나로 스택하여 하나의 스위치처럼 운영합니다.
   - **Virtual Switching System(VSS)**: Catalyst 4500, 6500 스위치에서 지원되며, 스위치를 논리적으로 하나로 통합하여 작동합니다.
   - **Virtual Port Channel(vPC)**: Nexus 스위치에서 지원되며, 독립된 두 스위치를 하나의 포트 채널로 묶어 대역폭 활용을 최적화합니다.

4. **기타 주의 사항**: MEC 설정은 CCNA 시험에서는 기본적인 개념만 다루지만, CCNP 또는 CCNA 트랙의 데이터 센터 과정에서는 구성과 모니터링 방법까지 배웁니다.

이 강의는 Cisco 네트워크의 효율성을 높이기 위한 방법들을 강조하며, 다양한 스위치 플랫폼에서의 MEC 옵션을 비교 설명하고 있습니다.

# 요약 및 리뷰

- EtherChannel은 여러 물리적 링크를 하나의 논리적 링크로 묶어 스패닝 트리가 차단하지 않고 모든 링크를 활용하게 함.

- 엔터프라이즈급 네트워크 스위치는 보통 모듈형 섀시 방식으로 만들어짐.
    - 전원 공급 장치, 팬, 제어 모듈, 라인카드 등을 하나의 큰 케이스에 장착
    - 이 물리적인 케이스를 "섀시"라고 부름
- 여러 개의 물리적 섀시를 하나의 논리적 시스템으로 묶는다는 의미로 Multi-Chassis EtherChannel 이라고 부름



---

> Source: `section_27/ysj/note.md`

## Section 27 정리

## 스위치 보안 - 액세스 스위치 관련

이 강의는 네트워크 보안을 강화하기 위해 액세스 스위치에서 사용되는 주요 보안 메커니즘 세 가지—DHCP 스누핑, 동적 ARP 검사 (DAI), 802.1x 인증—에 대해 설명합니다.

### 1. DHCP 스누핑

**문제**  
네트워크에 비인가 DHCP 서버가 존재할 때, 잘못된 IP 주소 및 설정이 사용자 기기에 할당되어 네트워크 연결이 방해될 수 있습니다. 이는 실수로 발생하기도 하고, 악의적인 공격자에 의해 의도적으로 발생할 수도 있습니다.

**해결 방법**  
DHCP 스누핑을 통해 스위치 포트 중 신뢰할 수 있는 포트를 지정하여, 비인가 DHCP 서버로부터 오는 트래픽을 차단할 수 있습니다.
- **구성 방법**  
  1. 스위치에서 `ip dhcp snooping` 명령어를 입력하여 DHCP 스누핑 활성화
  2. 특정 VLAN에서 스누핑을 활성화하려면 `ip dhcp snooping vlan [VLAN 번호]` 입력
  3. 신뢰할 수 있는 포트에서 `ip dhcp snooping trust` 명령어로 설정

### 2. 동적 ARP 검사 (DAI)

**문제**  
공격자가 중간자 공격을 수행하기 위해 ARP 스푸핑을 사용하여, 네트워크 상의 트래픽을 감청하거나 특정 트래픽을 차단하는 상황이 발생할 수 있습니다.

**해결 방법**  
DAI는 ARP 패킷의 유효성을 검사하여 ARP 스푸핑을 방지합니다. 이는 DHCP 스누핑 정보 기반으로 작동합니다.
- **구성 방법**  
  1. DHCP 스누핑을 활성화하고, DAI 구성 전제 조건을 만족시킵니다.
  2. 스위치에서 `ip arp inspection vlan [VLAN 번호]` 명령어로 특정 VLAN에서 DAI 활성화
  3. 신뢰할 수 있는 포트에서 `ip arp inspection trust` 설정

### 3. 802.1x 인증

**문제**  
네트워크 자원에 대한 비인가 접근을 방지해야 할 때, 802.1x 인증을 통해 인증된 사용자만 네트워크에 접속할 수 있도록 할 필요가 있습니다.

**해결 방법**  
802.1x 인증을 통해 사용자가 유효한 ID와 비밀번호로 인증되기 전까지 네트워크 접근을 제한합니다.
- **구성 방법**  
  1. 사용자 기기(요청자)가 802.1x 인증을 지원해야 하며, 스위치(인증자)가 이를 처리할 수 있도록 설정합니다.
  2. 인증 서버(예: Cisco ISE)를 통해 사용자 인증을 수행
  3. 인증 성공 시 VLAN에 매핑되어 일반적인 네트워크 접근이 허용됩니다.

이 외에도 포트 보안 등 다양한 보안 메커니즘이 있으며, 이는 다음 강의에서 다루어질 예정입니다.

## 스위치 보안 - 포트 보안

#### 문제 정의
1. **불필요한 포트 활성화**: 사용되지 않는 포트가 활성화된 경우, 인증되지 않은 사용자가 네트워크에 접근할 수 있음.
2. **무선 액세스 포인트(Access Point, AP) 및 기타 장치 연결**: 인증되지 않은 사용자가 임의로 AP나 스위치를 네트워크에 연결하면 외부 접근 위험이 커짐.
3. **MAC 주소 스푸핑**: 공격자가 허용된 MAC 주소를 모방하여 보안이 무력화될 수 있음.
4. **다수의 MAC 주소 사용 시도**: 하나의 포트에 여러 장치가 연결되어 다수의 MAC 주소가 감지되면 네트워크에 혼선이 발생.

#### 해결 방법
1. **불필요한 포트 비활성화**: 사용되지 않는 포트는 비활성화하여 접근을 차단.
2. **포트 보안 설정**:
   - **MAC 주소 기반 제한**: 포트에 특정 MAC 주소만 허용하도록 설정하여 특정 장치만 네트워크에 접속 가능하게 함.
   - **최대 MAC 주소 수 제한**: 포트에서 허용할 수 있는 최대 MAC 주소 수를 설정하여 다수의 장치 연결 시도를 방지.
3. **위반 모드 설정**:
   - **Shutdown**: 위반 발생 시 포트를 비활성화하여 차단.
   - **Protect**: 위반 트래픽만 폐기하고, 허용된 장치의 트래픽은 유지.
   - **Restrict**: 위반 트래픽을 폐기하고 위반 기록을 남김.
4. **위반 후 인터페이스 복구**:
   - 수동으로 **shutdown 및 no shutdown** 명령어를 사용해 포트를 다시 활성화.
   - 자동 복구 시간 설정으로 error-disabled 상태의 포트를 자동으로 재활성화.
5. **특정 MAC 주소 수동 설정**: 허용된 MAC 주소를 수동으로 추가해 특정 장치에 포트를 고정.

#### 결과
이러한 포트 보안 설정을 통해 네트워크에 대한 무단 접근을 방지하고, 네트워크의 보안과 안정성을 높임.


---

> Source: `section_28/ysj/note.md`

## Section 28 정리

---

## **ACL 액세스 제어 목록

이번 섹션에서는 네트워크 보안과 트래픽 관리에서 중요한 역할을 하는 ACL(Access Control List, 액세스 제어 목록)에 대해 다룹니다. ACL은 네트워크 트래픽을 식별하고 이를 제어하기 위한 정책입니다. 이를 통해 ACL은 특정 출발지와 도착지 IP 주소, 포트 번호 등을 기반으로 트래픽이 라우터를 통과할지 여부를 결정하는 역할을 합니다. 

## **1. ACL의 주요 역할과 적용 사례**

### **트래픽 식별 및 차단**
ACL은 라우터가 통과하는 트래픽을 식별하고 제어하기 위해 사용됩니다. 출발지 IP, 목적지 IP, 포트 번호 등을 기반으로 트래픽의 허용 또는 차단이 이루어지며, 라우터나 스위치와 같은 네트워크 장치에 적용할 수 있습니다.

### **보안 관리**
예를 들어, 영업팀과 회계팀이 서로 다른 서브넷에 속해 있을 때, 영업팀 PC에서 회계팀으로 트래픽이 이동하지 않도록 ACL을 설정해 보안 문제를 방지할 수 있습니다.

### **트래픽 제어 (QoS 및 NAT)**
ACL은 보안뿐 아니라 네트워크 품질(QoS) 보장을 위해 트래픽 우선순위를 지정하거나, NAT(Network Address Translation) 규칙을 설정하는 데에도 사용됩니다. QoS 정책을 위해서는 음성 트래픽을 식별해 우선순위를 설정할 수 있고, NAT를 통해 사설 IP 주소를 공인 IP 주소로 변환하는 작업에도 ACL을 사용할 수 있습니다.

---

## **2. ACL의 종류**

### **표준 ACL**
표준 ACL은 출발지 IP 주소만을 기반으로 트래픽을 제어하는 방식입니다. 보통 번호가 1~99 사이로 부여됩니다.
- **예시**:
  ```plaintext
  access-list 1 deny 10.10.10.10 0.0.0.0
  access-list 1 permit 10.10.10.0 0.0.0.255
  ```
  첫 번째 줄에서는 특정 IP(10.10.10.10)의 접근을 차단하고, 두 번째 줄에서는 나머지 IP(10.10.10.0/24)를 허용하는 규칙입니다.

### **확장 ACL**
확장 ACL은 출발지 및 목적지 IP 주소뿐만 아니라 포트와 프로토콜(TCP, UDP)까지 세부적으로 제어할 수 있습니다. 확장 ACL은 보통 번호가 100~199 사이로 부여됩니다.
- **예시**:
  ```plaintext
  access-list 100 deny tcp 10.10.10.10 0.0.0.0 10.10.50.10 0.0.0.0 eq 23
  access-list 100 permit tcp 10.10.10.0 0.0.0.255 10.10.50.10 eq telnet
  ```
  여기서는 특정 출발지에서 특정 목적지로의 텔넷(Telnet) 트래픽만을 차단하거나 허용하는 식으로 더 세부적으로 제어할 수 있습니다.

### **이름 지정 ACL**
이름 지정 ACL은 표준 및 확장 ACL에서 번호 대신 명칭을 지정하여 좀 더 이해하기 쉽게 관리할 수 있습니다.
- **예시**:
  ```plaintext
  ip access-list extended Flackbox-Demo
  deny 10.10.10.10 0.0.0.0
  permit 10.10.10.0 0.0.0.255
  ```
  이름 지정 ACL을 사용하면 ACL을 직관적으로 구분하고 관리하기 쉽습니다.

---

## **3. ACL의 구조와 구문 이해**

ACL 구문은 다음과 같은 순서로 작성됩니다:
1. **access-list** 명령어로 시작
2. ACL 번호 또는 이름을 지정
3. 허용(`permit`) 또는 차단(`deny`)을 지정
4. 프로토콜(TCP, UDP 등)을 지정
5. 출발지와 목적지 IP 주소 및 포트 번호를 지정

---

## **4. ACL 설정 예시와 주의사항**

- **주석 사용**: ACL에는 주석을 추가하는 기능이 있으며, 향후 ACL을 관리하거나 업데이트할 때 주석은 큰 도움이 됩니다. 특히 후임자가 ACL의 규칙을 이해할 수 있도록 설정한 이유를 설명하는 것이 좋습니다.
- **와일드카드 마스크**: 와일드카드 마스크는 ACL 규칙에서 서브넷 범위를 지정할 때 사용됩니다. `0.0.0.0`은 개별 호스트를, `0.0.0.255`는 특정 서브넷을 나타냅니다.
- **포트 번호**: 특히 Windows와 같은 최신 OS에서 출발지 포트 번호가 임의로 지정되므로 출발지 포트 설정을 주의해야 합니다.

---

## **5. ACL 적용 및 관리**

### **기본 설정과 규칙 관리**
ACL은 여러 개의 ACE(Access Control Entry)로 구성됩니다. 각 ACE는 하나의 트래픽 규칙을 나타내며, ACL은 다수의 ACE로 구성될 수 있습니다. 예를 들어, 다음과 같은 ACL을 사용할 수 있습니다:
  ```plaintext
  access-list 100 deny tcp any any eq 80
  access-list 100 permit ip any any
  ```
  이 예시에서는 HTTP 트래픽을 차단하고 그 외 모든 트래픽을 허용합니다.

### **주요 명령어 및 오류 방지**
ACL을 설정할 때 특정 항목을 누락할 경우 오류가 발생할 수 있습니다. 특히 와일드카드 마스크나 포트 번호를 지정하지 않으면 명령어가 제대로 작동하지 않을 수 있습니다.

### **번호 vs. 이름 지정 ACL 선택**
ACL을 관리할 때는 이름 지정 ACL이 번호 지정 ACL보다 더 유연하고 가독성이 높으므로, 특히 큰 네트워크에서는 이름 지정 ACL을 사용하는 것이 좋습니다.

---

## **결론**

ACL은 네트워크 트래픽을 식별하고 보안을 강화하기 위한 핵심적인 도구입니다. 표준, 확장, 이름 지정 ACL을 사용하여 다양한 정책을 설정할 수 있으며, QoS나 NAT 정책에 필요한 트래픽 식별에도 ACL이 사용됩니다. 이번 섹션에서 ACL의 기본 개념과 구조를 이해한 만큼, 다음 단계에서는 ACL을 실제 환경에 적용하고 구체적인 명령어 사용법을 더 깊이 다뤄보겠습니다.

# 리뷰

- 내용도 중요하긴 한데, 강의에서 관리하면서 사람들 간의 협업 관점에서 네이밍이나 주석 사용 예시를 가볍게 설명하고 넘어가는데, 인상깊어서 관련한 내 생각을 적어봄.
    - 네이밍은 다른 사람들이 봐도 이해하기 쉽게
        - 경우에 따라 기술적인거나 도메인 관련 용어일 수 있을듯.
            - 기술적: f0 Ethernet 인바운트 트래픽 이름: f0E_in
                - 이 경우 물리적이거나 실제 연결을 바로 확인해야 하기 때문에, 기술적인 내용이 들어감.
                    - 사실 이 관점에서 보면 이게 도메인 관련 용어라고 볼 수도 있을 듯.
            - 도메인 관련: BE 개발에서 도메인 관련 부분.
    - 주석은 구현으로만 제공할 수 없는 정보를 쓰면 좋을듯.
        - e.g. 다른 회사와 연결이 필요헀는데, 파트너쉽이 끊어지면서 레거시로 남아있는 상황.
            - 주석을 해놓았으면 레거시 개선이 쉬웠을 것.
        - 기술적인 부분으로는 이해하기 어렵거나, 이상해보이는게 들어간 이유, (너무 기술적인 것보다 사용 상황이나 맥락 제공) 추상적인 기능 등이 괜찮아 보임.


- AWS의 NACL과 거의 동일한 느낌? 
- 뭐 이름부터가 Network ACL이니까 당연할지도
- Stateless 하다는 점이나 역할은 비슷한데, 구체적으로 따지면 다르긴 한듯.
    - 물리 네트워크, 가상 네트워크
    - 인터페이스 단위, 서브넷 단위

- 시스코에서 작성한 ACL 관련 문서: https://www.cisco.com/c/ko_kr/support/docs/security/ios-firewall/23602-confaccesslists.html

---

> Source: `section_29/ysj/note.md`

## Section 29 정리

## NAT(Network Address Translation)

### 1. IPv4 주소 고갈 문제

##### IPv4의 한계
- IPv4는 32비트 주소 체계로 약 43억 개의 IP 주소 제공
- 초기 설계 시 이정도면 충분할 것으로 예상했으나 실제로는 부족
- 개인당 여러 기기(노트북, 모바일, 태블릿 등) 사용으로 수요 급증
- 프로토콜의 비효율적인 주소 공간 사용으로 실제 사용 가능한 주소 수는 더 적음

##### 해결 방안
1. **IPv6 개발**
   - 128비트 주소 체계 사용 (IPv4의 4배)
   - IPv4보다 28배 많은 주소 공간 제공
   - 주소 공간 고갈 문제 근본적 해결
   - 문제점: IPv4와 역호환되지 않아 전환이 어려움

2. **NAT 도입**
   - IPv6로의 전환 전까지 임시 해결책으로 도입
   - 실제로는 장기적인 해결책이 됨
   - 내부 네트워크에서 사설 IP 사용, 외부 통신 시 공인 IP로 변환

#### 2. 사설 IP 주소 (RFC1918)

##### 사설 IP 주소 범위
- **Class A**: 10.0.0.0 - 10.255.255.255 (10.0.0.0/8)
- **Class B**: 172.16.0.0 - 172.31.255.255 (172.16.0.0/12)
- **Class C**: 192.168.0.0 - 192.168.255.255 (192.168.0.0/16)

##### 특징
- 인터넷에서 라우팅 불가
- 내부 네트워크에서만 사용
- 공인 IP 주소 비용 절감
- 보안상 이점 제공 (외부에서 직접 접근 불가)

#### 3. NAT 유형

##### 1. 정적 NAT (Static NAT)
- 공인 IP와 사설 IP 간 1:1 영구 매핑
- 주요 용도: 웹 서버, 메일 서버 등 외부 접속이 필요한 서버
- 양방향 통신 지원

##### 2. 동적 NAT (Dynamic NAT)
- 공인 IP 주소 풀 사용
- 선착순으로 IP 주소 할당
- 풀의 주소가 모두 사용되면 새로운 연결 불가
- 일반적으로 수신 연결을 허용하지 않는 내부 호스트용

##### 3. PAT (Port Address Translation)
- 하나의 공인 IP로 다수의 내부 호스트 지원
- IP 주소와 포트 번호로 변환 추적
- 가장 널리 사용되는 방식
- 필요에 따라 공인 IP가 아니라 풀을 인터페이스로 매핑할수도 있음. PAT도 풀을 사용하므로 동일하게 적용 가능하며, 주로 DHCP를 사용해서 IP가 바뀌는 소규모 사무실에서 사용함.
- 특징:
  - 포트 번호로 각 연결 구분
  - 공인 IP 주소 절약
  - DHCP 환경에서도 사용 가능

#### 4. NAT 구성 요소

##### 주소 종류
1. **내부 로컬 주소**: 내부 호스트의 실제 IP 주소
2. **내부 전역 주소**: 외부에서 보는 내부 호스트의 변환된 주소
3. **외부 로컬 주소**: 내부에서 보는 외부 호스트의 주소
4. **외부 전역 주소**: 외부 호스트의 실제 IP 주소

##### 기본 구성 명령어
```
ip nat inside source static [내부IP] [외부IP]
ip nat inside source list [ACL번호] pool [풀이름]
ip nat pool [풀이름] [시작IP] [끝IP] netmask [넷마스크]
ip nat inside source list [ACL번호] interface [인터페이스] overload
```

### NAT 데모 랩

#### 1. 정적 NAT (Static NAT) 구성

##### 시나리오
- 내부 웹서버(10.0.1.10)를 외부에서 접근 가능하도록 공인 IP(203.0.113.3)로 매핑
- 양방향 통신 필요 (외부→내부, 내부→외부)

##### 구성 단계
```bash
# 1. NAT 인터페이스 지정
Router(config)# interface f0/0
Router(config-if)# ip nat outside    # 외부 인터페이스 지정

Router(config)# interface f1/0
Router(config-if)# ip nat inside     # 내부 인터페이스 지정

# 2. 정적 NAT 매핑 설정
Router(config)# ip nat inside source static 10.0.1.10 203.0.113.3
```

##### 확인 명령어
```bash
# NAT 변환 테이블 확인
Router# show ip nat translations

# NAT 동작 실시간 모니터링
Router# debug ip nat
```

#### 2. 동적 NAT (Dynamic NAT) 구성

##### 시나리오
- 내부 네트워크(10.0.2.0/24)의 호스트들이 인터넷 접근
- 공인 IP 풀 사용 (203.0.113.4 - 203.0.113.14)

##### 구성 단계
```bash
# 1. NAT 인터페이스 지정
Router(config)# interface f0/0
Router(config-if)# ip nat outside

Router(config)# interface f2/0
Router(config-if)# ip nat inside

# 2. NAT 풀 생성
Router(config)# ip nat pool Flackbox 203.0.113.4 203.0.113.14 netmask 255.255.255.240

# 3. 변환 대상 네트워크 정의 (ACL)
Router(config)# access-list 1 permit 10.0.2.0 0.0.0.255

# 4. NAT 풀과 ACL 연결
Router(config)# ip nat inside source list 1 pool Flackbox
```

#### 3. PAT (Port Address Translation) 구성

##### 시나리오 1: NAT 풀 사용
- 다수의 내부 호스트가 소수의 공인 IP 공유
- 포트 번호로 각 호스트 구분

##### 구성 단계
```bash
# 1. NAT 인터페이스 지정
Router(config)# interface f0/0
Router(config-if)# ip nat outside

Router(config)# interface f2/0
Router(config-if)# ip nat inside

# 2. NAT 풀 생성
Router(config)# ip nat pool Flackbox 203.0.113.4 203.0.113.6 netmask 255.255.255.240

# 3. 변환 대상 네트워크 정의
Router(config)# access-list 1 permit 10.0.2.0 0.0.0.255

# 4. PAT 설정 (overload 키워드 추가)
Router(config)# ip nat inside source list 1 pool Flackbox overload
```

##### 시나리오 2: 단일 공인 IP (DHCP) 사용
- 소규모 사무실에서 자주 사용
- DHCP로 할당받은 인터페이스 IP 사용

##### 구성 단계
```bash
# 1. NAT 인터페이스 지정
Router(config)# interface f0/0
Router(config-if)# ip address dhcp
Router(config-if)# ip nat outside

Router(config)# interface f2/0
Router(config-if)# ip nat inside

# 2. 변환 대상 네트워크 정의
Router(config)# access-list 1 permit 10.0.2.0 0.0.0.255

# 3. 인터페이스 기반 PAT 설정
Router(config)# ip nat inside source list 1 interface f0/0 overload
```

#### 공통 확인 및 문제해결 명령어

##### 기본 확인
```bash
# NAT 변환 테이블 확인
Router# show ip nat translations

# NAT 통계 확인
Router# show ip nat statistics

# 인터페이스 상태 확인
Router# show ip interface brief
```

##### 문제해결
```bash
# NAT 동작 실시간 모니터링
Router# debug ip nat

# NAT 변환 테이블 초기화
Router# clear ip nat translation *      # 모든 동적 변환 삭제
Router# clear ip nat translation inside [로컬IP] [전역IP] # 특정 변환 삭제
```

##### 작동 확인 테스트
```bash
# 내부→외부 연결 테스트
Host> ping 203.0.113.20

# 외부→내부 연결 테스트 (Static NAT의 경우)
Host> telnet 203.0.113.3 80
```

#### 주의사항
1. 정적 NAT 구성 시 양방향 통신 자동 지원
2. 동적 NAT는 풀의 주소가 모두 사용되면 새로운 연결 불가
3. PAT 사용 시 반드시 overload 키워드 추가
4. DHCP 환경에서는 인터페이스 기반 PAT 권장
5. 변환 테이블 확인 시 빠르게 확인 (엔트리 시간 초과 가능)

---

## show ip nat translations 명령어

#### 1. 명령어의 기본 역할
- NAT 라우터의 현재 활성화된 주소 변환 테이블을 표시
- 모든 NAT 매핑(정적, 동적, PAT)의 실시간 상태 확인 가능
- 문제 해결 시 가장 먼저 확인해야 하는 명령어

#### 2. 출력 결과의 주요 구성 요소

##### 기본 필드 설명
```
Pro  Inside global     Inside local       Outside local    Outside global
---  --------------   ---------------    --------------   ---------------
---  203.0.113.3:4096 10.0.1.10:49165   203.0.113.20:80  203.0.113.20:80
```

- **Pro(Protocol)**: 사용된 프로토콜 (tcp, udp, icmp 등)
- **Inside global**: 외부에 노출되는 내부 호스트의 변환된 주소:포트
- **Inside local**: 내부 호스트의 실제 사설 주소:포트
- **Outside local**: 내부 네트워크에서 보이는 외부 호스트 주소:포트
- **Outside global**: 외부 호스트의 실제 공인 주소:포트

#### 3. NAT 유형별 출력 예시

##### 정적 NAT의 경우
```bash
Router# show ip nat translations
Pro Inside global      Inside local       Outside local     Outside global
--- 203.0.113.3       10.0.1.10          ---               ---
```
- 포트 정보 없음
- 영구적인 1:1 매핑
- Outside 필드는 비어있을 수 있음

##### 동적 NAT의 경우
```bash
Router# show ip nat translations
Pro Inside global      Inside local       Outside local     Outside global
--- 203.0.113.4       10.0.2.10          ---               ---
--- 203.0.113.5       10.0.2.11          ---               ---
```
- 풀에서 할당된 주소 표시
- 일시적인 매핑
- 시간 초과 후 엔트리 자동 삭제

##### PAT의 경우
```bash
Router# show ip nat translations
Pro Inside global         Inside local          Outside local     Outside global
tcp 203.0.113.3:4096     10.0.2.10:49165      203.0.113.20:80   203.0.113.20:80
tcp 203.0.113.3:4097     10.0.2.11:49158      203.0.113.20:80   203.0.113.20:80
```
- 포트 번호까지 표시
- 같은 Inside global 주소에 여러 Inside local 주소 매핑
- 프로토콜 정보 포함

#### 4. 세부 주소 의미 설명

##### Inside Addresses
- **Inside local**: 내부 네트워크에서 실제로 구성된 호스트의 IP 주소
  - 예: `10.0.1.10` - 실제 호스트에 설정된 사설 IP
- **Inside global**: 외부에서 보는 내부 호스트의 변환된 공인 IP 주소
  - 예: `203.0.113.3` - NAT 후 외부에서 보이는 공인 IP

##### Outside Addresses
- **Outside local**: 내부 네트워크에서 보이는 외부 호스트의 주소
  - 일반적으로 Outside global과 동일
- **Outside global**: 외부 호스트의 실제 공인 IP 주소
  - 인터넷상의 실제 목적지 주소

#### 5. 실용적 활용 방법

##### 문제 해결 시나리오
1. **연결 문제 확인**
```bash
Router# show ip nat translations
```
- 예상된 변환이 테이블에 있는지 확인
- 포트 번호가 정상적으로 할당되었는지 검증

2. **변환 상태 초기화**
```bash
Router# clear ip nat translation *
Router# show ip nat translations
```
- 변환 테이블 초기화 후 새로운 연결 시도
- 문제 원인 파악에 도움

3. **실시간 모니터링과 함께 사용**
```bash
Router# debug ip nat
Router# show ip nat translations
```
- 실시간 NAT 동작과 변환 테이블 대조
- 변환 과정의 문제점 파악

#### 6. 주의사항
1. 명령어 실행 시점의 NAT 테이블 상태만 보여줌
2. 동적 변환은 매우 빠르게 시간 초과되어 사라질 수 있음
3. 실제 변환 과정이나 문제를 놓칠 수 있음

## 리뷰

영어로 NAT를 엔 에이 티 라고도 읽고 그냥 보이는 발음 그대로 낱 이라고도 읽는듯.

패킷에 헤더가 있고 그걸 다른 곳에서 지원하는게 아니라, 내부 IP를 외부 IP + 포트로 매핑해서 처리하는 방식임.

즉, 4계층이라고 볼 수 있을 듯?

- 뜬금없지만 기록해두면 좋을거 같아서
   - 3계층: 
      - OS 커널의 네트워크 스택에서 대부분의 3계층 기능 처리
      - 하드웨어(NIC)와 밀접한 연관 - NIC는 1~2계층
   - 4계층: 
      - 전적으로 소프트웨어/OS 수준에서 처리
      - 프로그래밍 가능한 영역
      - 포트 관리, 연결 상태 추적, 세션 관리 등

이전에 본 책에서 인상깊은 부분. 강의에서도 IPv6는 절대 다 소모되지 않는다고 했는데, 이정도면 그렇게 말할만 하지.
> IPv6는 주소당 128비트를 사용해. 따라서 IPv6로 만들 수 있는 주소의 개수는 무려 2의 128제곱인 340, 282,366,920,938,463,463,374,60 7,431,768,211,456개야. 단위로 치면억,조,경,해를 가볍게 넘어 약 ‘340간 2,823구’ 만큼의주소를 사용할 수 있어.
> 얼마나 많은지 감이 잘 오지 않지? 이 숫자가 얼마나 많은 양이냐면, 지구 표면 전체를 1mm^2로 산산이 쪼갰을 때 모든 조각마다 665,570,793,348,866,944개의 주소를 제공할 수 있을 정도야. 엄청나지?
> ref. 읽자마자 IT 전문가가 되는 네트워크 교과서




---

> Source: `section_30/ysj/note.md`

## Section 30 정리


IPv6 기초 (1/16)

1. IPv6 도입 배경

1.1 IPv4 주소 고갈
- 32비트 체계의 한계
- 전세계 IP 주소 부족 문제
- NAT로 일시적 해결 시도

1.2 NAT의 문제점
- IP 표준 모델 위반으로 보안 문제
- 특정 애플리케이션 동작 오류
- 멀티미디어 통신 제한
- Note: 상위 계층에서는 NAT를 모르므로, 내부와 외부의 통신이 발생할 때 동작이 정상적으로 수행되지 않을 수 있다.

1.3 NAT 사용의 구체적 문제
- IP 전화 시스템 예시 상황:
  - 두 회사 간 IP 전화 통신 시도
  - 내부 주소/외부 주소 변환 필요
  - 음성 트래픽 전달 실패
  - 사설 IP 사용으로 인한 통신 제한

IPv6 주소 체계 (2/16)

2. IPv6 주소 형식

2.1 기본 구조
- 128비트 주소 체계 (IPv4는 32비트)
- X:X:X:X:X:X:X:X 형식
- 각 X는 16비트의 16진수 필드
- 필드 값: 0-9, A-F 사용

2.2 주소 단축 규칙
- 필드 앞의 0 생략 가능
  예) 0DB8 → DB8
- 연속된 0 필드는 :: 로 대체
  예) 2001:0DB8:0000:0001:0000:0000:0000:0001
      → 2001:DB8:0:1::1
- :: 는 주소당 한 번만 사용 가능

2.3 잘못된 단축 예시
- 2001::1::B (잘못된 예)
  - 원래 주소 추측 불가
  - :: 중복 사용으로 혼란 야기
    - Note: 둘 곳에 0이 얼마나 쓰이는 알 수 없기 때문이다.

IPv6 주소 유형 (3/16)

3. 글로벌 유니캐스트 주소

3.1 특징
- IPv4 공인 주소와 동일한 개념
- 2000::/3 범위 사용
- 전역적으로 라우팅 가능

3.2 할당 체계
- 일반 기업: /48 블록
- 가정: /64 블록 
- 모든 호스트 인터페이스: /64 마스크

- Note: ipv6는 할당 주소가 많으므로 관리 편의 상의 이유로 `/64`를 사용한다. 심지어 `end-to-end`에서도 `/64`를 사용한다.

3.3 서브넷 구성 예시
- 기업이 2001:10::/48 할당받음
- 16비트 서브넷 공간 사용 가능
- 최대 65,536개 서브넷
- 각 서브넷은 2001:10:10:0/64 ~ 2001:10:10:FFFF::/64

라우터 구성 기본 (4/16)

4. IPv6 라우터 기본 설정

4.1 필수 구성 요소
- ipv6 unicast-routing 활성화
- 인터페이스별 IPv6 주소 할당
- no shutdown으로 인터페이스 활성화

4.2 기본 명령어
```
Router(config)# ipv6 unicast-routing
Router(config)# interface f0/0
Router(config-if)# ipv6 address 2001:DB8:0:1::1/64
Router(config-if)# no shutdown
```

4.3 구성 확인
- show ipv6 interface brief
- show ipv6 route
- ping ipv6 [address]

EUI-64 주소 설정 (5/16)

5. EUI-64 자동 주소 생성

- Note: EUI-64는 Mac 주소를 기반으로 하므로 보안 상의 문제가 있으므로, 여러 OS는 대신 SLAAC를 사용한다.

5.1 작동 원리
- MAC 주소 기반 호스트 ID 생성
- MAC 주소 중간에 FFFE 삽입
- 7번째 비트 반전

5.2 구성 방법
```
Router(config-if)# ipv6 address 2001:DB8:0:1::/64 eui-64
```

5.3 사용 제한사항
- 라우터보다 종단 호스트에 적합
- 문제해결 어려움
- 관리상 직접 주소 할당 선호

링크 로컬 주소 (6/16)

6. 링크 로컬 주소 - ipv6의 여러 주소 유형의 구체적인 설명을 더 아래 해둠.

6.1 특징
- FE80::/10 범위 사용
- 같은 링크 내에서만 통신
- IPv6 활성화시 자동 생성

6.2 용도
- 라우터 간 통신
- 라우팅 프로토콜용
- 인접 라우터 검색

6.3 구성 예시
```
Router(config-if)# ipv6 address FE80::1 link-local
```

유니크 로컬 주소 (7/16)

7. 유니크 로컬 주소

7.1 특성
- FC00::/7 범위 사용
- IPv4 사설주소와 유사
- 조직 내부 통신용

7.2 주요 특징
- 인터넷 라우팅 불가
- /64 마스크 사용
- 자동/수동 구성 가능

멀티캐스트 주소 (8/16)

8. IPv6 멀티캐스트

8.1 브로드캐스트 대체
- IPv6는 브로드캐스트 미지원
- 멀티캐스트로 대체
- 더 효율적인 그룹 통신

8.2 주요 주소
- FF02::1 (모든 노드)
- FF05::1:3 (DHCP 서버)

SLAAC(Stateless Address Auto-configuration) (9/16)

9. 무상태 주소 자동 구성

9.1 기본 개념
- 호스트 자동 주소 구성
- 라우터 광고 기반
- DHCP 불필요

9.2 작동 과정
- 라우터가 prefix 광고
- 호스트가 주소 자동 생성
- EUI-64 또는 랜덤 ID 사용

9.3 제한사항
- DNS 정보 제공 불가 - (Note: 여전히 DHCP 필요, DHCP의 기능을 더 대체하는 기능은 아직 발전 중 or 반영이 안됨.)
- 추가 정보(DNS 등)는 여전히 DHCP 필요
  - 그러나 IP 주소 구성 자체는 Stateless 함.

IPv6 라우팅 (10/16)

10. 라우팅 구성

- Note: 기존 ipv4랑 거의 동일하다. 로컬, static, 라우팅 프로토콜 등... 서브넷 마스크를 CIDR(`/`)를 써서 축약 표현을 사용함.

10.1 기본 요구사항
- ipv6 unicast-routing 활성화
- 인터페이스 주소 설정
- 라우팅 경로 구성

10.2 정적 라우팅 예시
```
Router(config)# ipv6 route 2001:DB8:0:2::/64 2001:DB8:0:1::2
Router(config)# ipv6 route ::/0 2001:DB8:0:1::1
```

10.3 경로 확인
- show ipv6 route
- show ipv6 neighbors
- ping ipv6

---

### **IPv6 주소 유형 상세 정리**

1. **글로벌 유니캐스트 주소 (Global Unicast Address)**  
   - **정의**: 인터넷 상에서 전역적으로 유효한 공개 IPv6 주소. IPv4의 공인 주소와 유사.  
   - **범위**: `2000::/3` (주소 공간의 상위 1/8 할당).  
   - **할당 체계**:  
     - **기업**: 일반적으로 `/48` 블록.  
     - **가정**: 보통 `/56` 또는 `/64`.  
     - **호스트**: 항상 **/64** 서브넷 마스크를 사용 (인터페이스 ID는 SLAAC에 의존).  
   - **구조**:  
     ```
     | Global Routing Prefix | Subnet ID | Interface ID |
     |         n bits         |  m bits   |    128-n-m   |
     ```
     - 예: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`  
       - `2001:0db8:85a3` → 글로벌 라우팅 프리픽스.   = (네트워크 ID)
       - `0000` → 서브넷 ID.  
       - `0000:8a2e:0370:7334` → 인터페이스 ID.  

2. **링크 로컬 주소 (Link-Local Address)** - 아래 추가 설명 있음.
   - **정의**: 동일 링크(Local Network Segment) 내에서만 사용 가능한 자동 생성 주소.  
   - **범위**: `FE80::/10` (즉, `FE80::`부터 `FEBF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF`까지).  
   - **특징**:  
     - 각 인터페이스에서 **자동 생성** (프리픽스 `FE80` + 인터페이스 ID).  
     - 네트워크 연결 여부와 관계없이 항상 사용 가능.  
     - 링크 외부로의 라우팅 불가.  
   - **용도**:  
     - 라우터 간 연결 및 통신.  
     - 네이버 디스커버리 (Neighbor Discovery Protocol, NDP).  
     - 기본 게이트웨이 설정.  

3. **유니크 로컬 주소 (Unique Local Address)**  
   - **정의**: 조직 내부에서만 사용되는 사설 IPv6 주소. IPv4의 사설 주소(`192.168.x.x`, `10.x.x.x`)와 유사.  
   - **범위**: `FC00::/7`  
     - **FD00::/8**: 현재 일반적으로 사용되는 서브셋.  
   - **특징**:  
     - 인터넷에서 라우팅 불가 (주소의 고유성 보장을 위해 랜덤 생성 가능).  
     - `/64` 서브넷 마스크 필수 (SLAAC 호환성).  
     - 조직 내부에서 라우팅에 사용.  

4. **멀티캐스트 주소 (Multicast Address)**  - 아래 추가 설명 있음.
   - **정의**: 특정 그룹에 메시지를 전송하기 위한 IPv6 주소.  
   - **범위**: `FF00::/8`  
   - **주요 주소**:  
     - `FF02::1`: 모든 노드.  
     - `FF02::2`: 모든 라우터.  
     - `FF05::1:3`: DHCP 서버.  
   - **특징**:  
     - IPv4의 브로드캐스트 대신 사용됨.  
     - 효율적인 그룹 통신 및 서비스 간 주소 분리를 지원.  
     - 특정 기능(예: OSPF, DHCP)별로 멀티캐스트 주소 지정 가능.  

5. **브로드캐스트**  
   - **IPv6에서의 변경 사항**:  
     - IPv4의 브로드캐스트 개념이 제거됨.  
     - 대신 멀티캐스트 주소를 사용하여 특정 그룹에 데이터 전송.  
   - **장점**:  
     - 네트워크 부하 감소.  
     - 트래픽이 필요 없는 장치로 전달되지 않음.  
     - 효율적이고 서비스 중심의 데이터 분배 가능.  

### **추가 설명**  
1. **글로벌 유니캐스트 주소와 서브넷**  
   - `/64`는 SLAAC와 호환성을 위해 기본적으로 사용되며, **2^64**개의 주소를 가질 수 있음. (대충 10^18 × 18.4 정도)
   - `/48`은 ISP가 고객에게 제공하는 기본 할당 크기. `/48`에서 65,536개의 `/64` 서브넷 생성 가능.

2. **링크 로컬 주소**  
   - 기본적으로 모든 IPv6 인터페이스에 생성되므로, IPv6 활성화 시 라우터 설정 없이도 라우터 간 통신 가능.  

3. **멀티캐스트와 브로드캐스트 비교**  
   - 브로드캐스트는 모든 노드로 데이터 전송, 네트워크 자원 낭비.  
   - 멀티캐스트는 필요한 그룹에게만 전송, 효율성 증가.  


### **요약**  
- **글로벌 유니캐스트**: 전역 유효 주소, 주로 `/64` 사용.  
- **링크 로컬**: 링크 내 자동 생성, 기본적으로 `FE80::/10`.  
- **유니크 로컬**: 조직 내부 사설 주소, `FC00::/7`.  
- **멀티캐스트**: 그룹 통신용, `FF00::/8`.  
- **브로드캐스트**: IPv6에서 제거, 멀티캐스트로 대체.  

IPv6는 설계상 주소 공간이 매우 크며, 각 유형은 명확한 용도와 효율성을 제공하도록 설계되었습니다.


---

ipv6 관련 RFC 문서

RFC 3177과 RFC 6177은 IPv6 주소 할당에 관한 권장사항을 다루고 있는 문서입니다. 두 문서의 주요 내용과 차이점은 다음과 같습니다:

RFC 3177 (2001년 발표)

- 대부분의 경우 최종 사이트에 /48 블록을 할당할 것을 권장했습니다[1][3].

- 구체적으로 /48, /64, /128의 고정된 프리픽스 길이를 권장했습니다[4].

- 단일 크기의 할당 정책(one-size-fits-all)을 제안했습니다[4].

RFC 6177 (2011년 발표)

- RFC 3177의 권장사항을 폐기하고 업데이트했습니다[2][4].

- 모든 최종 사이트에 단일 기본 할당 크기(/48 등)를 적용하는 것은 적절하지 않다고 판단했습니다[4].

- 최종 사이트의 규모와 특성에 따라 유연하게 주소 공간을 할당할 것을 권장했습니다[4].

- 고정된 경계(/48, /64, /128 등)만을 인식하는 "클래스풀 주소 지정" 방식으로의 회귀를 경계했습니다[4].

- CIDR(Classless Inter-Domain Routing)이 라우팅 프리픽스의 모든 비트에 계속 적용되어야 한다고 강조했습니다[4].

- 최종 사이트가 실제 및 계획된 사용에 맞는 충분한 주소 공간을 얻을 수 있어야 한다는 RFC 3177의 기본 원칙은 재확인했습니다[4].

요약하면, RFC 6177은 RFC 3177의 경직된 할당 정책을 수정하여 보다 유연하고 효율적인 IPv6 주소 할당을 권장하고 있습니다.

Citations:
[1] https://datatracker.ietf.org/doc/html/rfc3177
[2] https://www.rfc-editor.org/info/rfc6177
[3] https://www.rfc-editor.org/info/rfc3177
[4] https://tex2e.github.io/rfc-translater/html/rfc6177.html

---

IPv6와 관련된 주요 RFC 문서들을 다음과 같이 정리할 수 있습니다:

## 기본 사양

- RFC 8200: IPv6의 기본 사양을 정의한 문서로, RFC 2460을 대체합니다[4].

## 주소 체계

- RFC 4291: IPv6 주소 아키텍처를 정의합니다[5].
- RFC 3513: IPv6 주소 지정 아키텍처의 이전 버전입니다[5].
- RFC 3879: IPv6 주소 체계에 대한 업데이트를 포함합니다[5].

## 자동 설정

- RFC 2462: IPv6 무상태 주소 자동 설정(SLAAC)을 정의합니다[3][5].
- RFC 4862: RFC 2462를 대체하는 업데이트된 SLAAC 사양입니다[3].

## 이웃 탐색

- RFC 2461: IPv6 이웃 탐색 프로토콜을 정의합니다[3].
- RFC 4861: RFC 2461을 대체하는 업데이트된 이웃 탐색 프로토콜 사양입니다[3].

## ICMPv6

- RFC 2463: IPv6용 인터넷 제어 메시지 프로토콜(ICMPv6)을 정의합니다[3].
- RFC 4443: RFC 2463을 대체하는 업데이트된 ICMPv6 사양입니다[3][4].

## 전환 메커니즘

- RFC 4213: IPv6 호스트 및 라우터를 위한 기본 전환 메커니즘을 정의합니다[5][6].

## 모바일 IPv6

- RFC 3775: 모바일 IPv6 사양을 정의합니다[5].

## 보안

- RFC 4302: 인증 헤더(AH)를 정의합니다[5].
- RFC 4303: 캡슐화 보안 페이로드(ESP)를 정의합니다[5].
- RFC 4305: ESP와 AH를 위한 암호화 알고리즘 구현 요구사항을 명시합니다[5].

## 노드 요구사항

- RFC 6434: IPv6 노드의 요구사항을 정의하는 최신 문서입니다[6].
- RFC 4294: IPv6 노드 요구사항의 이전 버전입니다[5].

이 외에도 다양한 링크 계층 기술에 대한 IPv6 사양(이더넷, PPP, ATM 등)과 DNS, DHCPv6 등 관련 프로토콜에 대한 RFC들이 존재합니다[5][6].

Citations:
[1] https://datatracker.ietf.org/doc/html/rfc2460
[2] https://www.rfc-editor.org/rfc/rfc9637.html
[3] https://www.system.de/ipv6-rfc/
[4] https://datatracker.ietf.org/doc/html/rfc8200
[5] https://www.rfc-editor.org/rfc/rfc4294
[6] https://www.rfc-editor.org/rfc/rfc6434

---

IPv6 서브넷 마스크와 관련된 RFC 문서는 다음과 같습니다. 이들 문서에서는 IPv6 주소 할당과 서브넷 설계에 대한 세부 정보를 다룹니다.

---

### **관련 RFC 문서**

1. **[RFC 4291: IPv6 Addressing Architecture](https://www.rfc-editor.org/rfc/rfc4291)**
   - IPv6 주소 구조와 서브넷 설계에 대한 기본 정보를 제공합니다.
   - 주요 내용:
     - IPv6 주소는 128비트 길이로 구성됩니다.
     - 주소는 네트워크 부분과 인터페이스 식별자로 나뉘며, 일반적으로 `/64` 서브넷 마스크를 사용합니다.
     - 인터페이스 ID는 EUI-64 형식이나 수동 설정으로 지정됩니다.
     - `/128`은 단일 호스트를 식별할 때 사용됩니다.

2. **[RFC 6177: IPv6 Address Assignment to End Sites](https://www.rfc-editor.org/rfc/rfc6177)**
   - 최종 사용자에게 할당되는 IPv6 주소 범위에 대해 논의합니다.
   - 주요 내용:
     - 기존 권고인 `/48` 주소 블록이 너무 과할 수 있다고 지적하며, `/56`이나 `/64` 할당도 적합할 수 있다고 언급.
     - 네트워크 설계 요구에 따라 유연한 주소 할당을 권장.

3. **[RFC 5952: A Recommendation for IPv6 Address Text Representation](https://www.rfc-editor.org/rfc/rfc5952)**
   - IPv6 주소 표현 방식에 대해 설명합니다.
   - 주요 내용:
     - 서브넷 접두사 표기법 (CIDR)은 IPv6 주소에서 네트워크 크기를 지정하는 데 사용됩니다. 예: `2001:db8::/32`.
     - 불필요한 `0`은 생략 가능하며, 연속된 `0`은 `::`로 압축 가능.


### **서브넷 마스크 설명**

1. **/64**
   - **주요 용도**: 대부분의 IPv6 네트워크에서 표준 서브넷 크기로 사용됩니다.
   - 하위 64비트는 호스트 ID로 사용되며, SLAAC(Stateless Address Autoconfiguration)와 호환됩니다.
   - 한 서브넷에 약 `2^64`개의 주소 가능.

2. **/48**
   - **주요 용도**: 조직 단위로 IPv6 주소를 할당할 때 권장.
   - 한 조직에 `/48` 블록이 주어지면 65,536개의 `/64` 서브넷을 생성할 수 있음.
   - ISP가 고객에게 네트워크 블록을 제공할 때도 사용.

3. **/128**
   - **주요 용도**: 단일 인터페이스 또는 장치 식별.
   - 주로 루프백 주소나 특정 장치의 식별에 사용.


### **IPv6 서브넷 선택 고려사항**
- **/64**: 가장 일반적으로 사용되며 SLAAC와 같은 자동화 기능을 지원.
- **/48**: 대규모 네트워크 설계 시 사용.
- **/128**: 고정된 주소가 필요한 특정 장치에서 사용.

이 RFC 문서들은 인터넷 주소 구조 및 서브넷 설계와 관련된 정책 및 기술적 기준을 제공합니다. RFC 문서는 [RFC Editor 웹사이트](https://www.rfc-editor.org/)에서 무료로 열람할 수 있습니다.

---

Link-Local Address(LLA)는 동일한 물리적 링크/서브넷 내에서만 통신이 가능합니다.

구체적인 예시와 함께 설명하겠습니다:

1. 라우터 직접 연결 시나리오
```
R1 [f0/0] --- [f0/1] R2
fe80::1        fe80::2
```
- R1과 R2는 서로 LLA로 통신 가능
- 같은 물리적 링크에 연결되어 있기 때문

2. 스위치를 통한 연결 시나리오
```
R1 --- SW1 --- R2
fe80::1        fe80::2
```
- R1과 R2는 같은 브로드캐스트 도메인에 있어 LLA로 통신 가능
- Layer 2 스위치는 링크의 범위를 확장

3. 라우터를 통한 통신 시나리오
```
R1 --- R2 --- R3
fe80::1  fe80::2  fe80::3
```
- R1은 R2와 LLA 통신 가능
- R2는 R3와 LLA 통신 가능
- R1은 R3와 LLA 통신 불가능 (다른 링크)

실제 사용 사례:
1. 라우팅 프로토콜
```
R1(config)# ipv6 ospf neighbor fe80::2
```
- OSPF, EIGRP 등이 LLA로 인접 라우터와 통신

2. 기본 게이트웨이 설정
```
Host# ipv6 route ::/0 fe80::1
```
- 호스트가 기본 게이트웨이를 LLA로 참조

3. 라우터 간 직접 핑 테스트
```
R1# ping ipv6 fe80::2 source f0/0
```
- 출력 인터페이스 지정 필수
- 같은 링크의 라우터로만 핑 가능

주의사항:
- 다른 링크로는 라우팅 불가
- 인터페이스 지정 필요
- 동일한 LLA 주소를 다른 링크에서 사용 가능

---

IPv6 Multicast Address의 주요 사용 예시:

1. 모든 노드 멀티캐스트 (FF02::1)
```
R1(config)# ping FF02::1
```
- 해당 링크의 모든 IPv6 호스트에 도달
- 네트워크 장비 검색에 사용
- IPv4의 브로드캐스트 대체

2. 모든 라우터 멀티캐스트 (FF02::2)
```
R1(config)# ping FF02::2
```
- 해당 링크의 모든 라우터에 도달
- 라우터 검색에 사용
- 라우팅 프로토콜 정보 교환

3. DHCP 관련 멀티캐스트
- All DHCP Servers: FF05::1:3
- All DHCP Relay Agents: FF02::1:2
```
Client -> FF05::1:3 (DHCP 요청)
Server -> Client (응답)
```

4. 라우팅 프로토콜용 멀티캐스트
- RIPng: FF02::9
- OSPFv3: FF02::5 (모든 OSPF 라우터)
- OSPFv3: FF02::6 (DR/BDR 라우터)
```
R1(config)# ipv6 router ospf 1
R1(config-rtr)# neighbor FF02::5
```

5. Solicited-Node 멀티캐스트 (FF02:0:0:0:0:1:FF00::/104)
```
예: 주소가 2001:db8::1234면
Solicited-Node MC: FF02::1:FF00:1234
```
- IPv6 neighbor discovery에 사용
- MAC 주소 해석 (ARP 대체)
- 마지막 24비트만 사용

6. MLD (Multicast Listener Discovery)
```
FF02::16 - MLDv2 멀티캐스트
```
- 멀티캐스트 그룹 관리
- 호스트의 멀티캐스트 참여/이탈 처리

실제 동작 예시:
```
1. Neighbor Discovery
Host A -> FF02::1:FF00:1234 (Neighbor Solicitation)
Host B -> Host A (Neighbor Advertisement)

2. Router Discovery
Router -> FF02::1 (Router Advertisement)
Host -> FF02::2 (Router Solicitation)

3. DHCP
Client -> FF05::1:3 (DHCP Solicit)
Server -> Client (DHCP Advertise)
```

이점:
- 효율적인 네트워크 리소스 사용
- 목적지 기반 필터링 가능
- 특정 서비스별 주소 할당으로 관리 용이

---

IPv6 멀티캐스트는 범위(Scope)에 따라 다르게 동작합니다:

1. Link-Local Scope (FF02::/16)
- 같은 링크 내에서만 통신
- 라우터가 포워딩하지 않음
- 예시:
  - FF02::1 (모든 노드)
  - FF02::2 (모든 라우터)
  - FF02::5 (OSPF 라우터)
  - FF02::1:2 (DHCP 릴레이)

2. Site-Local Scope (FF05::/16)
- 사이트/조직 내부에서 라우팅 가능
- 외부로는 라우팅되지 않음
- 예시:
  - FF05::1:3 (모든 DHCP 서버)
  - FF05::1:4 (모든 DHCP 에이전트)

3. Global Scope (FF0E::/16)
- 전역적으로 라우팅 가능
- 멀티캐스트 라우팅 프로토콜 필요
- 조직간 멀티캐스트 통신에 사용

대부분의 일반적인 용도는 Link-Local Scope를 사용합니다.


---

> Source: `section_31/ysj/note.md`

## 1. WAN (Wide Area Network) 기본 개념

### 네트워크 유형 분류
1. LAN (Local Area Network)
- 단일 건물이나 캠퍼스와 같은 제한된 지리적 영역의 네트워크
- 일반적으로 단일 조직이 소유/관리
- 높은 대역폭, 낮은 지연시간 특성

2. WAN (Wide Area Network) 
- 지리적으로 분산된 LAN들을 상호 연결하는 네트워크
- 예: 뉴욕 본사와 보스턴 지사 간 네트워크 연결
- 서비스 제공자(Service Provider)의 인프라 활용이 일반적

3. MAN (Metropolitan Area Network)
- LAN보다 크고 WAN보다 작은 도시 규모의 네트워크
- 같은 도시 내 여러 지점을 연결
- WAN에 비해 상대적으로 덜 사용되는 용어

## 2. VPN (Virtual Private Network)

### 기본 개념
- 공유 공인 네트워크(주로 인터넷)를 통한 가상 암호화 터널 구성
- 물리적 전용선 대비 저렴한 비용
- 데이터 기밀성을 위한 암호화 제공

### VPN 유형
1. Site-to-Site VPN
- 사무실 간 영구적 연결
- 라우터/방화벽에서 종단 처리
- 일반적으로 IPsec 프로토콜 사용
- 최종 사용자 장비 설정 불필요

2. Remote Access VPN
- 개별 사용자의 원격 접속용
- 사용자 장치에 VPN 클라이언트 소프트웨어 설치 필요
- SSL/TLS 또는 IPsec 사용
- 예: Cisco AnyConnect

### Site-to-Site VPN 구현 방식
1. IPsec 터널
- 개방형 표준, 다양한 벤더 장비 간 호환
- 멀티캐스트 미지원
- 정적 라우팅만 가능

2. GRE over IPsec
- GRE (Generic Routing Encapsulation) 터널에 IPsec 보안 적용
- 멀티캐스트 및 동적 라우팅 프로토콜 지원
- IPsec의 보안성과 GRE의 유연성 결합

3. IPsec VTI (Virtual Tunnel Interface)
- Cisco 전용 기술
- 간단한 구성
- 멀티캐스트 지원

4. DMVPN (Dynamic Multipoint VPN)
- Cisco 전용 기술
- Hub-and-Spoke 구성으로 완전 메시 연결 지원
- 확장성이 우수하며 구성 간소화
- 동적 터널 생성으로 최적 경로 확보

5. FlexVPN
- DMVPN의 차세대 버전
- 향상된 확장성과 유연성

6. GETVPN (Group Encrypted Transport VPN)
- Cisco 전용 기술
- MPLS 환경에서 사용
- 중앙집중식 키/정책 관리

## 3. MPLS (MultiProtocol Label Switching)

- Note: ISP에서 제공하는 VPN, 공용 회선 공유하여 가격이 싸고, 가입자 간 논리적 분리를 제공한다.  
    - Label이라는 IP 주소보다 단순한 정보를 사용해서 라우터 경로를 구성한다.  
    - PE 시작 시 IP 확인 후 Label을 부착 -> P에서 Label 정보를 보고 다른 P로 이동 -> 나가는 PE에서 Label 제거 및 IP로 전달
        - P to P에선 각 라우터마다 Swap이 발생는 방식 or PHP 최적화로 Swap이 발생하지 않는 방식 등이 있음.
    - https://www.cloudflare.com/ko-kr/learning/network-layer/what-is-mpls/
    https://louis-j.tistory.com/entry/IP-MPLS-MPLS-%EC%99%84%EC%A0%84-%EC%A0%95%EB%B3%B5-%ED%98%84%EB%8C%80-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC%EC%9D%98-%ED%95%B5%EC%8B%AC-%EA%B8%B0%EC%88%A0%EC%9D%84-%ED%8C%8C%ED%97%A4%EC%B9%98%EB%8B%A4
    - http://www.ktword.co.kr/test/view/view.php?m_temp1=2508&id=461
    - https://catsbi.oopy.io/75315c4f-20d7-4196-a239-363f374f7727

### MPLS VPN 개요
- 서비스 제공자의 공유 인프라를 통한 고객 간 분리된 통신
- SLA (Service Level Agreement) 기반 서비스 품질 보장
- 일반 인터넷 VPN 대비 안정적인 서비스 품질

### MPLS 구성요소
1. PE (Provider Edge) 라우터
- 고객 네트워크와 직접 연결
- MPLS VPN 서비스 제공 경계점

2. P (Provider) 라우터
- MPLS 코어 네트워크 구성
- 레이블 기반 패킷 전송 담당

3. CE (Customer Edge) 라우터
- 고객 측 라우터
- PE와 직접 연결

### MPLS VPN 유형
1. Layer 3 VPN
특징
- PE와 CE 라우터가 서로 라우팅 정보를 교환
- 마치 직접 연결된 라우터처럼 동작
- 각 사이트는 자신만의 IP 주소 체계 사용 가능

예시: `본사(10.1.0.0/16) ←→ MPLS망 ←→ 지사(192.168.1.0/24)`
- 서로 다른 IP 대역 사용 가능
- 라우팅 프로토콜로 경로 정보 교환

2. Layer 2 VPN
- VPLS (Virtual Private LAN Service)
  - 멀티포인트 L2 연결
    - 여러 지점을 하나의 거대한 스위치로 연결한 것처럼 동작
  - 단일 브로드캐스트 도메인 구성
- VPWS (Virtual Private Wire Service)
  - 포인트-투-포인트 L2 연결
    - 두 지점을 직접 케이블로 연결한 것처럼 동작
  - pseudowire 기술 사용

## 4. 전용회선 (Leased Line)

### 특징
- 두 지점 간 전용 물리적 연결
- 고정 대역폭 보장
- 대칭적 업로드/다운로드 속도
- 높은 신뢰성과 보안성
- SLA 기반 서비스 품질 보장

### 대역폭 옵션
1. 북미 지역
- T1: 1.544 Mbps
- T2: 6.312 Mbps
- T3: 44.736 Mbps

2. 유럽/기타 지역
- E1: 2.048 Mbps
- E2: 8.448 Mbps
- E3: 34.368 Mbps

### 장단점
장점:
- 전용 대역폭 보장
- 높은 보안성
- SLA 보장
- 안정적인 성능

단점:
- 높은 비용
- 긴 구축 기간
- 확장성 제한

## 5. 기타 WAN 연결 옵션

### 광케이블 기반 서비스
1. SONET/SDH
- SONET: 북미 표준
- SDH: 국제 표준
- 고속 광전송 네트워크 구현

2. DWDM (Dense Wavelength Division Multiplexing)
- 단일 광섬유로 다중 광신호 전송
- 높은 대역폭 효율성
- 백본(Backbone) 네트워크에 주로 사용

### 소규모 사무실/가정용 옵션
1. DSL (Digital Subscriber Line)
- 기존 전화선 활용
- 비대칭 속도 특성
- PPPoE 프로토콜 사용

2. Cable Internet
- 케이블 TV 망 활용
- 공유 대역폭 특성

3. 4G/5G 무선
- 이동통신망 활용
- 백업 회선으로 활용 가능

## 6. WAN 토폴로지

### 주요 토폴로지 유형
1. Hub-and-Spoke (Star)
- 중앙 집중형 구조
- 단순한 구성
- 중앙 보안 정책 적용 용이
- 단일 장애점 위험

2. Dual Hub-and-Spoke
- 이중화된 허브 구성
- 향상된 가용성
- 높은 구축 비용

3. Full Mesh
- 모든 지점 간 직접 연결
- 최적의 트래픽 경로
- 높은 구축/운영 비용
- 복잡한 구성

4. Partial Mesh
- 선택적 직접 연결
- 비용과 성능의 균형
- 중요 지점 간 직접 경로 제공

### 인터넷 연결 이중화 옵션
1. Single-homed
- 단일 ISP, 단일 회선
- 단순한 구성
- 단일 장애점 존재

2. Dual-homed
- 단일 ISP, 이중 회선
- 회선 레벨 이중화

3. Multi-homed
- 복수 ISP, 단일 회선
- ISP 레벨 이중화

4. Dual Multi-homed
- 복수 ISP, 이중 회선
- 최고 수준의 이중화
- 복잡한 구성과 높은 비용

## 7. WAN 인터페이스 카드

- Note: 여담 파트, 지원 라우터가 다르므로 사용에 주의하라는 내용.

### 주요 유형
1. 이더넷 인터페이스
- 기본 온보드 포트
- 추가 모듈 장착 가능

2. 시리얼 인터페이스
- WIC-2T: 구형 플랫폼용
- HWIC-2T: 신형 플랫폼용

3. T1/E1 인터페이스
- NIM-2MFT-T1/E1
- 음성/데이터 통합 지원

### 선택 시 고려사항
- 라우터 플랫폼 호환성
- 필요한 포트 수와 유형
- 대역폭 요구사항
- 향후 확장성


---

> Source: `section_32/ysj/note.md`

## Section 32 정리

## 251. IT 보안 위협의 현주소

### 1. **기본 용어**
- **위협**: IT 자산에 피해를 줄 가능성.
- **취약점**: 시스템의 보안 약점.
- **익스플로잇**: 취약점을 이용한 공격.
- **위험**: 공격이 성공할 가능성.
- **완화**: 공격 가능성과 심각성을 줄이기 위한 조치.

### 2. **멀웨어의 유형**
- **바이러스**: 인간의 행동을 통해 전파되는 악성 코드.
- **웜**: 인간의 개입 없이 스스로 전파되는 악성 코드.
- **트로이 목마**: 유용한 소프트웨어로 위장해 시스템에 침투하는 악성 코드.
- **랜섬웨어**: 데이터를 암호화하고 금전을 요구하는 악성 코드.

### 3. **해킹 도구**
- **암호 해독 도구**: 자동으로 암호를 추측.
- **스니퍼**: 네트워크 데이터를 감시.
- **핑 스위퍼**: 시스템의 활성 여부 확인.
- **포트 및 취약점 스캐너**: 취약점을 찾기 위해 시스템 조사.

### 4. **공격자의 유형**
- **스크립트 키디**: 이미 만들어진 해킹 도구를 사용하는 비숙련 공격자.
- **표적 공격자**: 특정 개인이나 조직을 대상으로 체계적으로 공격을 수행하는 숙련된 공격자.

### 5. **표적 공격의 단계**
1. **외부 정찰**: 시스템에 대한 정보를 수집.
2. **초기 침투**: 접근 가능한 시스템 공격.
3. **권한 확대**: 더 높은 권한을 획득.
4. **내부 정찰**: 내부 시스템 탐색.
5. **최종 공격**: 목표 시스템에 도달하고 최대한 피해를 유발.

## 252. 해커가 사용하는 주요 공격 방법과 이에 대한 설명

1. **정찰 (Reconnaissance)**  
   - 표적 대상에 대한 정보를 수집하며, 눈에 띄지 않게 시작.  
   - **사용하는 방법**:
     - **Whois 데이터베이스**: 도메인 소유자 정보 확인.
     - **공개 전화번호부 및 구인 정보**: 조직 구조, 기술 스택 파악.  
   - **예시**: 구인 광고에서 기술 스택 노출 → Cisco CallManager 사용 파악.  

2. **소셜 엔지니어링**  
   - 사람을 속여 정보를 빼내는 공격.  
   - **기법**:
     - **전화 사기**: IT 관리자라고 속여 비밀번호 변경 유도.  
     - **피싱**: 가짜 웹사이트로 사용자의 계정 정보 유출.  
   - **예시**: PayPal 사칭 이메일로 사용자 이름, 비밀번호 탈취.  

3. **데이터 유출 (Data Breach)**  
   - 조직 외부로 민감 정보가 유출되는 사건.  
   - **유출 경로**:
     - 해커의 시스템 침입 (예: 신용카드 정보 탈취).  
     - 내부자 실수 (예: 암호화되지 않은 USB 분실).  
   - **결과**: 정보 협박 또는 추가 공격 준비.  

4. **서비스 거부 공격 (DoS/DDoS)**  
   - **DoS**: 서버를 트래픽으로 마비시키는 공격.  
     - TCP SYN 플러드: 연결 요청만 반복해 리소스 소모.  
   - **DDoS**: 봇넷을 활용해 다수의 좀비 호스트에서 공격.  
     - 방어 난이도가 더 높음.  
     - Note: 터널링을 사용해서 봇넷에 접근한다고 함.
        - `해커 → [암호화된 터널] → C&C 서버 → [암호화된 터널] → 감염된 컴퓨터들`
        - 감염된 곳에서 악성 프로그램이 터널링을 사용해서 아웃바운드 트래픽으로 연결되어 C&C에 의해 조종되기 때문에 방화벽이 뚤림.

5. **스푸핑 (Spoofing)**  
   - 신원을 가장해 트래픽을 위장.  
   - **유형**:
     - **IP 스푸핑**: 공격자의 IP를 피해자로 위장.  
     - **MAC 주소 스푸핑**: 네트워크 혼란 유발.  
     - **악성 DHCP 서버**: 악성 IP 할당.  

6. **중간자 공격 (Man-in-the-Middle, MITM)**  
   - 공격자가 두 호스트 사이의 통신을 가로채고 조작.  
   - **기법**:
     - ARP 스푸핑: 네트워크 트래픽 탈취.  
   - **결과**: 데이터 유출 및 시스템 접근.  

7. **암호 공격 (Password Attacks)**  
   - **방법**:
     - 사전 공격: 사전 단어로 암호 추측.  
     - 무차별 대입 공격: 모든 조합 시도.  
   - **목표**: 사용자의 계정 정보 확보.  

8. **버퍼 오버플로 (Buffer Overflow)**  
   - 잘못된 데이터 입력으로 시스템을 손상시키는 공격.  
   - **결과**: 시스템 충돌, 관리자 권한 탈취.  

9. **패킷 스니퍼 (Packet Sniffer)**  
   - 네트워크에서 전송되는 데이터를 도청.  
   - **결과**: 암호화되지 않은 민감 정보 탈취, 추가 공격 준비.  

## 253-254. IDS와 IPS, 방화벽 vs 패킷 필터

---

#### **1. IDS (Intrusion Detection System)**
- **기능**: 네트워크의 트래픽을 감시하고 공격 의심 사항을 **탐지**하여 관리자에게 알림.
- **작동 방식**:  
  - 트래픽 사본을 통해 분석 (미러링 사용).
  - 시그니처 기반 탐지(알려진 공격 패턴)와 변칙 탐지(비정상 트래픽 활동 감지) 지원.
  - 직접 트래픽 차단은 불가능하지만, 방화벽과 협력해 공격 차단 가능.
- **위치**: 네트워크 흐름 옆에 위치하여 트래픽 사본을 분석.

---

#### **2. IPS (Intrusion Prevention System)**
- **기능**: 트래픽을 실시간으로 **분석** 및 **차단**하여 공격을 방지.
- **작동 방식**:
  - 인라인으로 트래픽을 거쳐가며 공격 감지 시 즉시 차단.
  - 시그니처와 변칙 탐지 모두 활용.
- **위치**: 네트워크 흐름 **인라인**에 위치하여 트래픽이 직접 지나감.
- **문제점**:  
  - 병목 현상 발생 가능 (트래픽 과부하 시 처리 속도 저하).  
  - 클러스터링을 통해 처리량 확장 가능.

---

#### **3. 방화벽**
- **기능**: 네트워크 트래픽을 **허용**하거나 **차단**.
- **작동 방식**:  
  - 규칙 기반으로 작동 (IP, 포트, 프로토콜 기반).  
  - 스테이트풀 방화벽은 연결 상태를 추적하여 반환 트래픽 허용.
- **특징**:  
  - 내부 네트워크와 인터넷 간 경계를 보호.
  - DMZ(비무장지대) 설정 가능 (민감한 서버 보호).
  - 최신 방화벽은 IPS 기능 포함 (차세대 방화벽).
- Note:
  - 여기서 말하는 건 하드웨어 방화벽으로 실제 물리적 기기임.
  - 모든 라우터 사이사이에 끼우기에는 비싸기도 하고, 기존 구조를 변경하기 때문에, ACL과 함께 사용하여 보안을 향샹시킴.

---

#### **4. IDS, IPS, 방화벽의 협력**
- IDS는 방화벽과 함께 사용하여 탐지와 차단 기능을 분리함.
- IPS는 방화벽과 결합하여 실시간 방어력을 높임.
- 차세대 방화벽은 IPS, IDS 기능 통합 제공.
- 네트워크의 **다계층 보안**을 위해 ACL과 방화벽을 결합:
  - 외부 트래픽 필터링에 ACL 사용.
  - 내부 및 민감 영역 보안에는 IPS와 방화벽 조합.

---

#### **5. 보안 토폴로지의 예시**
- **인터넷 엣지**: 외부와 내부 네트워크 경계에 방화벽 배치.
- **DMZ**: 외부 트래픽과 내부 트래픽을 분리하여 민감한 서버 보호.
- **내부 네트워크**:
  - 부서 간 트래픽 통제 (스위치 및 방화벽 사용).
  - 내부 서버 보호를 위해 IPS 추가 배치.

---

#### **6. ACL vs. 방화벽**
- **ACL (Access Control List)**:
  - 규칙에 따라 트래픽을 허용하거나 차단.
  - 스테이트풀 기능 없음 (연결 상태 추적 불가).
  - 적절한 양방향 설정 필요.
- **스테이트풀 방화벽**:
  - 반환 트래픽 자동 허용.
  - 보다 강력하고 안전한 연결 제어 가능.

- Note: 방화벽은 

#### 결론
IDS, IPS, 방화벽은 서로 보완적으로 작동하며, 네트워크 보안을 다계층으로 강화하는 데 필수적입니다.  
- **필수**: 방화벽은 인터넷 연결 시 기본적인 방어 장치.  
- **선택적**: IPS 및 ACL은 환경에 따라 추가적으로 활용 가능.  
- 최신 기술을 통해 IPS와 방화벽이 통합된 차세대 보안 장비를 배치하면 관리 효율성을 높이고 더 강력한 보호를 제공합니다.

### 255-256. 암호화 기법, TLS 전송층 보안
1. **확실성 (Authenticity)**  
   - 데이터가 정말 신뢰할 수 있는 출처로부터 왔음을 증명.  
2. **기밀성 (Confidentiality)**  
   - 데이터가 전송 중에도 프라이버시와 비밀이 유지됨.  
3. **일관성 (Integrity)**  
   - 데이터가 전송 중에 변경되지 않았음을 보장.  
4. **부인 방지 (Non-repudiation)**  
   - 데이터를 보낸 사람이 나중에 자신이 보냈음을 부인할 수 없도록 보장.  

#### 암호화 방식  
1. **대칭 암호화 기법 (Symmetric Encryption)**  
   - 발신자와 수신자가 동일한 키를 사용하여 데이터를 암호화 및 복호화.  
2. **비대칭 암호화 기법 (Asymmetric Encryption)**  
   - 공개 키 (*Public Key*)와 개인 키 (*Private Key*)의 쌍을 사용하여 데이터를 암호화 및 복호화.  ---

#### 대칭 암호화 알고리즘  
1. **DES** (Data Encryption Standard)  
2. **3DES** (Triple Data Encryption Standard)  
3. **AES** (Advanced Encryption Standard)  
4. **SEAL**  

(DES와 3DES는 보안 문제로 잘 사용되지 않음).

#### 비대칭 암호화 알고리즘  
1. **RSA** (Rivest-Shamir-Adleman)  
2. **ECDSA** (Elliptic Curve Digital Signature Algorithm)  

#### HMAC (Hash-based Message Authentication Code)  
- 데이터를 해시 값으로 변환하여 데이터 무결성을 보장.  

#### 키 배포 문제 (Key Distribution Problem)  
- 대칭 암호화에서 양측이 안전하게 키를 공유하는 데 발생하는 문제.  

#### 공인 키 인프라 (Public Key Infrastructure, PKI)  
- 신뢰할 수 있는 인증 기관을 통해 공개 키를 안전하게 공유.  

#### 전송 계층 보안 (Transport Layer Security, TLS)  
- 네트워크 통신을 보호하는 보안 프로토콜. SSL의 후속 기술.  

### **인터넷 암호화 프로토콜: TLS**
1. **TLS (Transport Layer Security)**:
   - SSL의 후속 프로토콜로 안전한 통신 보장.
   - 예시: HTTPS를 통한 보안 웹 브라우징.

2. **TLS 작동 과정**:
   - Amazon과 같은 웹사이트는 **공인 인증 기관(CA)**에서 인증서를 발급받음 (예: Verisign).
   - 인증서에는 공개 키가 포함되며, CA의 비밀키로 서명됨.
   - 브라우저는 CA의 공개 키로 인증서를 검증해 신뢰성 확인.

3. **대칭 키 교환**:
   - 비대칭 암호화를 통해 대칭 공유 키를 안전하게 교환.
   - 이후 데이터 전송에는 대칭 암호화를 사용하여 속도를 높임.

4. **피싱 방지**:
   - 인증서 검증은 인증 기관(CA)을 신뢰하는 브라우저에 의해 이루어짐.
   - 유효한 인증서라도 가짜 사이트라면 URL이나 연결 상태(HTTPS)를 확인해야 함.

## 257-258. 지역 간 VPN 가상 사설 네트워크, 원격 액세스 VPN 가상 사설 네트워크

1. Site-to-Site VPN
- 두 사이트 간 암호화된 통신 제공
- 주로 IPsec 사용
- DES, 3DES, AES 등의 대칭 암호화 알고리즘 활용
- 일반적으로 방화벽이나 라우터에서 터널 종료
- 인증 방식: 사전 공유키 또는 인증서

구성 요소:
- ISAKMP/IKE: 초기 인증 및 키 교환 담당
- AH: 무결성, 인증 제공
- ESP: 기밀성, 무결성, 인증 제공 (더 보편적으로 사용)
- 터널/전송 모드: 패킷 암호화 방식 결정

2. Client-to-Site VPN (원격 액세스)
- Cisco AnyConnect 사용 (ASA 방화벽에서 종료)
- TLS/SSL 기반 암호화 
- 두 가지 터널링 방식:
  - 스플릿 터널링: 회사 트래픽만 VPN 통과
  - 풀 터널링: 모든 트래픽이 VPN 통과 (중앙 집중식 보안 관리 가능)

주요 구성사항:
- 관심 트래픽 정의 (ACL 사용)
- ISAKMP/IKE 설정
- IPsec 보안 정책 구성
- NAT 예외 설정 필요

## 259. 위협 방어 솔루션

### 멀웨어 방어
- 시그니처 기반 탐지: 기존 바이러스의 특징적인 패턴을 데이터베이스와 대조하여 탐지
- 휴리스틱 탐지: 의심스러운 프로그램 행동을 실시간으로 분석하여 새로운 위협 감지
- IPS: 네트워크 트래픽을 실시간 모니터링하여 악성 활동 차단
- Cisco WSA: 웹 기반 위협으로부터 네트워크 보호
- Cisco ESA: 이메일을 통한 위협 차단 및 필터링

### 소셜 엔지니어링 및 정찰 방어
- 보안 인식 교육: 직원들에게 사회공학적 공격 식별법과 대응 방법 교육
- 보안 정책: 정보 공유와 접근에 대한 명확한 가이드라인 수립
- 기술적 대응: 정찰 활동 감지 및 차단을 위한 모니터링 시스템 구축

### DDoS 공격 방어 
- IPS/방화벽: 비정상적인 트래픽 패턴 감지 및 차단
- 안티-DDoS 서비스: 대규모 DDoS 공격에 대한 클라우드 기반 방어
- 분산 배치: 서비스를 여러 지역에 분산하여 가용성 확보

### 스푸핑 및 중간자 공격 방어
- uRPF: 소스 IP 주소가 위조된 패킷을 필터링하여 IP 스푸핑 방지
- 랜덤 TCP 시퀀스: TCP 연결 하이재킹 방지를 위한 무작위 시퀀스 번호 사용  
- DAI: ARP 스푸핑 공격을 탐지하고 차단하는 스위치 보안 기능

### 비밀번호 공격 방어
- 복잡한 비밀번호: 길이, 특수문자 등 강력한 비밀번호 정책 적용
- MFA: 비밀번호 외 추가 인증 요소 도입으로 보안 강화
- 보안 교육: 피싱 등 비밀번호 탈취 시도에 대한 인식 제고

### 버퍼 오버플로우/패킷 스니핑 방어
- 소프트웨어 패치: 버퍼 오버플로우 취약점에 대한 정기적인 업데이트
- 네트워크 보안: 암호화 및 필터링으로 패킷 스니핑 방지

### 모의 해킹
- 내부 테스트: 내부 시스템 및 네트워크의 취약점 점검
- 외부 테스트: 외부에서 접근 가능한 서비스의 보안성 평가

## 추가

- VPN은 터널링 기술을 사용해서 제 3자가 통신하는 데이터를 볼 수 없도록 캡슐화한다.
    - 터널링: 공용 네트워크(인터넷)를 통해 가상의 전용 통로를 만드는 기술
    - 따라서 무슨 데이터를 보내는지, 목적지(IP)인지, 무슨 프로토콜을 사용하는지도 암호화되어 알 수 없음.

대부분 정확하나, 몇 가지 수정이 필요합니다:

TLS(HTTPS) 작동 방식:
1. 인증서 검증
- 서버: 비밀키 보유, 인증서(공개키 포함)는 CA의 비밀키로 서명
- 브라우저: CA 공개키로 인증서 검증 (신뢰할 수 있는 CA 목록 보유)
2. TLS 연결 과정 
- 클라이언트: Client Hello (지원하는 암호화 방식, 랜덤 문자열 전송)
- 서버: Server Hello (선택된 암호화 방식, 랜덤 문자열, 인증서 전송)
- 클라이언트: 인증서 검증 후, Pre-master secret 생성하여 서버 공개키로 암호화 전송
    - 인증서 검증은 CA에게 요청을 보내서 이루어짐.
- 양측: 교환된 정보로 동일한 대칭키(세션키) 생성
3. 데이터 전송
- 생성된 대칭키로 이후 모든 통신 암호화
- 각 세션마다 새로운 대칭키 사용

공격에서 안전한 이유:
1. **피싱 공격 (Phishing)**  
   - **공격 방법**: 가짜 웹사이트로 유인, 인증서를 보내 사용자를 속임.  
   - **방어 방법**: 인증서의 도메인 정보 불일치 시 브라우저 경고.
2. **인증서 위조 (Fake Certificate)**  
   - **공격 방법**: 유효한 인증서를 얻어 가짜 웹사이트로 유인.  
   - **방어 방법**: 인증서의 도메인 정보가 일치하지 않으면 경고.
3. **자체 인증 기관 공격 (Self-Signed Certificate)**  
   - **공격 방법**: 자체 인증 기관으로 가짜 인증서 발급.  
   - **방어 방법**: 브라우저는 공인 인증 기관 인증서만 신뢰.
4. **중간자 공격 (Man-in-the-Middle)**  
   - **공격 방법**: 사용자와 서버 사이에 가로채기.  
   - **방어 방법**: TLS 인증서와 암호화된 키 교환으로 데이터 보호.
5. **인증서 탈취 (Certificate Theft)**  
   - **공격 방법**: 인증서 탈취 후 악용.  
   - **방어 방법**: 비밀키는 서버만 가지고 있어 탈취해도 무효.
6. **DNS 스푸핑 (DNS Spoofing)**  
   - **공격 방법**: 가짜 웹사이트로 유도.  
   - **방어 방법**: 인증서 검증을 통해 실제 서버와 연결 확인.

---

> Source: `section_33/ysj/note.md`

## Section 33 정리


### Cisco 라우터 및 스위치 기본 보안 설정 요약

1. **접속 모드 및 계층 구조**
   - **사용자 모드**: 제한된 명령어만 사용 가능. (프롬프트: `>`).  
   - **관리자 모드 (Enable 모드)**: 더 많은 명령어 사용 가능. (프롬프트: `#`).  
   - **글로벌 구성 모드**: 장치 설정 수정. (`configure terminal` → 프롬프트 `(config)`).

2. **비밀번호 구성 방법**
   - **콘솔 라인 비밀번호**  
     - 물리적 연결 보호.  
     - 명령어:  
       ```plaintext
       line console 0
       password [비밀번호]
       login
       ```  
   - **VTY 라인 비밀번호 (텔넷/SSH)**  
     - 원격 연결 보호.  
     - 명령어:  
       ```plaintext
       line vty 0 15
       password [비밀번호]
       login
       ```  
   - **활성 프롬프트 비밀번호 (Enable 모드 전환 시 필요)**  
     - 설정 방식:  
       ```plaintext
       enable secret [비밀번호]
       ```  
     - **중요**: `enable secret`은 암호화되며, `enable password`는 평문으로 저장됨.  
     - `enable secret`만 사용하는 것이 최선.  
     - `enable password` 설정이 있다면 `no enable password`로 제거.  
     - 예시:  
       ```plaintext
       enable secret [암호화된 비밀번호]
       no enable password
       ```

3. **비밀번호 암호화**  
   - `service password-encryption`을 사용해 모든 비밀번호를 암호화.  
     - Note: config 설정 파일의 내용을 암호화하여 읽을 수 없게 함. 설정 안하면 sh run에서 사용자 비밀번호가 평문으로 보임. 
   - 명령어:  
     ```plaintext
     service password-encryption
     ```
   - 적용 후 `sh run` 명령을 실행하면 모든 비밀번호가 암호화되어 표시됨.

4. **자동 종료 설정 (Exec Timeout)**  
   - 비활동 시 자동 로그아웃. 기본값: 10분.  
   - 설정 예:  
     ```plaintext
     line console 0
     exec-timeout [분] [초]
     line vty 0 15
     exec-timeout [분] [초]
     ```  
   - 비활성화: `no exec-timeout`.

5. **접속 제한 (ACL 적용)**  
   - 특정 IP에서만 텔넷/SSH 접속 허용.  
   - 명령어:  
     ```plaintext
     access-list 1 permit host [관리자 IP]
     line vty 0 15
     access-class 1 in
     ```

6. **추가 보안 팁**  
   - 라인 수준(콘솔/VTY) 비밀번호와 활성 프롬프트 비밀번호를 모두 설정 권장.  
   - 비밀번호 암호화(`enable secret` + `service password-encryption`)는 기본 설정.  
   - 모든 설정 변경 후 반드시 저장(`write memory` 또는 `copy running-config startup-config`).  

### 사용자 명과 관리자 레벨

1. **라인 레벨 보안**  
   - **콘솔 및 VTY 비밀번호 구성**  
     - 단점: 같은 비밀번호를 사용하면 모든 관리자가 동일한 권한을 가짐.  
     - 명령어 예:  
       ```plaintext
       line console 0
       password [비밀번호]
       login
       line vty 0 15
       password [비밀번호]
       login
       ```  

2. **사용자별 계정 및 비밀번호 구성**  
   - 각 사용자마다 사용자명과 비밀번호를 개별 지정 가능.  
   - 명령어 예:  
     ```plaintext
     username [사용자명] secret [비밀번호]
     line console 0
     login local
     line vty 0 15
     login local
     ```  

3. **관리자 레벨 (Privilege Level)**
   - **레벨 0**: 로그아웃, 활성화, 도움말 등 기본 명령만 사용 가능.  
   - **레벨 1 (기본)**: 읽기 전용 명령 사용 가능.  
   - **레벨 15**: 모든 명령 사용 가능.  
   - 사용자 계정에 특정 레벨 지정 가능:  
     ```plaintext
     username [사용자명] privilege [레벨] secret [비밀번호]
     ```  
     

4. **명령어의 관리자 레벨 변경**  
   - 특정 명령어에 관리자 레벨을 할당 가능.  
   - 명령어 예:  
     ```plaintext
     privilege exec level [레벨] [명령어]
     ```  

5. **활성화 비밀번호에 레벨 지정**  
   - 기본 활성화 비밀번호는 레벨 15에만 적용.  
   - 특정 레벨에 비밀번호 지정 가능:  
     ```plaintext
     enable secret level [레벨] [비밀번호]
     ```  


### **SSH 보안 구성**
- 텔넷은 트래픽이 암호화되지 않아 취약하므로 **SSH 사용 권장.**
- Note: 텔넷은 허용하지 않고, SSH만 사용하는게 안전
- SSH 설정 절차:
  1. 도메인 이름 설정: `ip domain-name example.com`
  2. 인증서 생성: `crypto key generate rsa` (최소 768비트 권장).
  3. VTY 라인에 SSH 전용 입력값 설정: `transport input ssh`.
  4. 로컬 사용자 계정 사용 설정: `login local`.
  5. SSH 버전2 활성화: `ip ssh version 2`.
- SSH 접속: 
  - Linux: `ssh -l username IP`.
  - Windows: PuTTY 사용.

### **AAA 개념 및 필요성**  
- **AAA란**: 인증(Authentication), 권한 검증(Authorization), 계정 관리(Accounting).  
- **기존 로컬 보안의 한계**:  
  - 새 관리자가 들어오거나 나갈 때 모든 라우터와 스위치에 수동으로 사용자 계정을 추가/삭제해야 함.  
  - 라인 레벨 비밀번호 변경 시 모든 장치에서 설정 변경 필요.  
- **AAA 서버 도입 장점**:  
  - 보안 중앙화.  
  - 사용자 인증, 권한, 비밀번호 관리가 중앙 서버에서 이루어짐.  
  - 장치별 수동 관리 필요성 제거.  
  - Note: 서버라는 이름에서 알 수 있듯이, 네트워크에서 특정 역할을 수행하는 독립적인 HOST이다.

**AAA 기능 및 프로토콜**  
- **인증(Authentication)**: 사용자 이름과 비밀번호로 본인 확인.  
- **권한 검증(Authorization)**: 사용자가 수행 가능한 작업을 결정.  
- **계정 관리(Accounting)**: 사용자가 실행한 명령어 및 활동 추적.  
- **AAA 주요 프로토콜**:  
  - **RADIUS**: VPN 등 유저 레벨 서비스에 적합.  
  - **TACACS+**: 관리자 권한 제어 및 세부 명령 제어 가능.  

**AAA 서버와 액티브 디렉토리 통합**  
  - Note 액티브 디렉토리: MS(윈도우)의 사용자 정보 관리 DB, Cisco의 AAA 서버와 별도이나. 관리 및 보안 측면에서 하나로 통합하는게 유리함.
- **장점**:  
  - 하나의 사용자 이름과 비밀번호로 모든 장치 접근 가능.  
  - Cisco 명령어 권한 제어(Cisco AAA 서버)와 Windows 로그인 통합 가능.  
- **통합 과정**:  
  - 라우터가 AAA 서버와 통신해 사용자 정보를 확인.  
  - AAA 서버가 LDAP를 사용해 액티브 디렉토리와 통신.  
  - 도메인 컨트롤러가 그룹 정보를 제공해 권한 부여.  

**AAA 서버 구성 방식**  
- **기본 설정**:  
  - `aaa new-model`: AAA 활성화.  
  - `radius-server host [IP] key [비밀번호]`: RADIUS 서버 추가.  
  - `aaa authentication login default group radius local`: RADIUS 인증 우선, 로컬 사용자 명 대체 옵션 설정.  
- **백업 사용자 계정 설정**:  
  - `username [이름] password [비밀번호]`: AAA 서버 연결 실패 시 사용할 로컬 계정 추가.  
- **RADIUS 및 TACACS+ 새로운 구성 방식**:  
  - 각각 `radius-server`와 `tacacs-server` 명령어 사용.  
  - 서버 그룹 생성 및 우선순위 지정 가능.  

**운영 환경에서의 활용 예**  
- **글로벌 구성**:  
  - 로그인 배너: "관리자 전용" 등의 메시지 표시.  
  - Exec 배너: 인증된 관리자가 아닌 경우 로그아웃 경고 메시지 제공.  
- **보안 유지**:  
  - 중앙 관리로 계정과 권한 변경 시 빠른 적용 가능.  
  - 사용자 활동 추적으로 문제 발생 시 원인 추적 용이.  


---

> Source: `section_34/ysj/note.md`

## Section 34 정리

### Syslog

- Note: Syslog라는 메시지 로깅 형식 표준이 있다.

1. **Syslog 기본 개념**:
   - Syslog는 표준 메시지 로깅 형식으로 Cisco IOS가 따르는 업계 표준.
   - 장치 이벤트 발생 시 로그 메시지가 생성되며, 메시지에는 시퀀스 번호, 타임스탬프, Facility(출처), Severity(심각도), mnemonic(간략 설명), 자세한 설명 등이 포함.

2. **Severity 레벨** (0~7):
   - **0**: Emergency (시스템 사용 불가, 심각)
   - **1**: Alert (즉각 조치 필요)
   - **2**: Critical (심각한 상태)
   - **3**: Error (오류)
   - **4**: Warning (주의 필요)
   - **5**: Notice (정상적이지만 주의 필요)
   - **6**: Informational (정보 제공용)
   - **7**: Debug (디버깅 상세 정보)

3. **Syslog 메시지 저장 위치**:
   - **콘솔 라인**: 기본 활성화, 기본 Severity는 Debug.
   - **가상 터미널 라인(VTY)**: 기본 비활성화.
   - **로깅 버퍼(RAM)**: 기본 활성화.
   - **외부 Syslog 서버**: 로그 중앙 집중화에 사용.

4. **Syslog 설정 방법**:
   - **로깅 활성화/비활성화**:
     - `logging console` / `no logging console` (콘솔 라인)
     - `logging monitor <level>` (VTY 라인)
     - `logging buffered <level>` (버퍼)
   - **외부 서버 로깅**:
     - `logging <서버 IP>` 및 `logging trap <level>`.

5. **Terminal Monitor 명령**:
   - 텔넷/SSH 세션에서 디버깅 메시지를 보기 위해 필요.
   - 명령: `terminal monitor`.

6. **Logging Synchronous**:
   - 명령 입력 중 로그 메시지가 방해되지 않도록 설정.
   - 적용: `line console 0` 및 `line vty 0 15`에서 `logging synchronous`.

7. **Debug 명령 사용 주의**:
   - 실시간 디버깅 정보를 출력.
   - 프로덕션 환경에서 과도한 출력은 장치 성능에 영향을 줄 수 있음.
   - 디버깅 종료: `undebug all`.

8. **Syslog 서버의 장점**:
   - 로그 중앙 집중화.
   - 문제 해결 시 전체 네트워크 로그 분석 가능.
   - SIEM(System Information and Event Management)과 통합해 고급 분석 가능.


### SNMP

#### SNMP(Simple Network Management Protocol)

1. 개요
- 네트워크 모니터링을 위한 개방형 표준 프로토콜
- 라우터, 스위치, 서버 등 대부분의 네트워크 장치에서 사용

2. 구성 요소
- SNMP 매니저(서버/NMS): 정보 수집/정리
- SNMP 에이전트: 관리 장치에서 실행되는 소프트웨어
- MIB(Management Information Base): 장치별 데이터 변수 저장 데이터베이스

3. 동작 방식
- Get: 매니저가 장치에서 정보 수집
- Trap: 장치가 매니저로 정보 푸시
- Set: 매니저가 장치 설정 변경(덜 일반적)

4. 버전
- SNMPv1: 일반 텍스트 인증
- SNMPv2c: 일반 텍스트 인증, 대량 검색 지원
- SNMPv3: 강력한 인증/암호화 지원(권장)

5. 보안 고려사항
- 기본 커뮤니티 문자열(public/private) 사용 금지
- 미사용 장치는 SNMP 비활성화
- 가능하면 SNMPv3 사용
- SNMPv2c 사용 시 커스텀 커뮤니티 문자열 설정

#### SNMPv3 구성

1. 보안 모델
- 유저와 그룹 기반 인증 사용
- Community String 대신 암호화된 인증 방식 도입

2. 보안 레벨
- noAuthnoPriv: 기본 인증만 (유저네임)
- AuthNoPriv: 비밀번호 인증 (암호화)
- AuthPriv: 비밀번호 인증 + 통신 암호화 (권장)

3. 구성 단계

그룹 구성:
```
snmp-server group Flackbox-group v3 priv
```

유저 구성:
```
snmp-server user Flackbox-user Flackbox-group v3 auth sha AUTHPASSWORD priv aes 128 PRIVPASSWORD
```

4. 추가 설정 옵션
- access: NMS 서버 IP 접근 제어
- context: 스위치의 VLAN 접근 제어
- view: MIB 객체 접근 권한 설정
  - read view: 읽기 권한 (기본: 모든 접근)
  - write view: 쓰기 권한 (기본: 접근 불가)
  - notify view: 트랩 알림 설정

5. 암호화 옵션
- 인증: SHA (보안성 높음)
- 암호화: AES 128/192/256 (숫자가 클수록 보안 강화)


### Syslog vs SNMP

1. Syslog vs SNMP
- Syslog: 세분화된 로그 정보 제공, 단방향 푸시 방식
- SNMP: 양방향 통신 가능, 더 다양한 기능성 제공
- 상호 보완적이므로 둘 다 사용 가능
- 대부분의 NMS 서버가 두 프로토콜 모두 지원

2. NMS vs SIEM
- 공통점: 
  - 네트워크 장치의 로그 정보 수집
  - Syslog, SNMP, NetFlow 등 동일한 프로토콜 사용

- 차이점:
  NMS:
  - 네트워크 성능/상태 모니터링 중심
  - 대역폭, 인터페이스 상태 등 네트워크 문제 감지
  - 예시: SolarWinds

  SIEM:
  - 보안 모니터링/분석 중심
  - 인증 실패, 악성코드, 해킹 시도 등 보안 위협 감지
  - 예시: InfoSight

결론: 각 도구가 서로 다른 목적을 가지고 있어 상호 보완적으로 사용 가능

---

Syslog와 SNMP의 기본 개념:

Syslog:
- 장치의 상태, 이벤트, 오류 등을 기록하는 로깅 프로토콜
- 장치에서 Syslog 서버로 단방향 메시지 전송
- 상세한 로그 정보 제공

SNMP (Simple Network Management Protocol):
- 네트워크 장치 모니터링/관리를 위한 표준 프로토콜
- 양방향 통신 지원:
  - Get: 서버가 장치에서 정보 수집
  - Trap: 장치가 서버로 정보 전송
- 장치 상태 모니터링, 구성 변경 등 관리 기능 제공

두 프로토콜은 상호 보완적으로 사용되며, 대부분의 네트워크 관리 시스템에서 둘 다 지원합니다.

### 리뷰

- 후반부라 그런가 자격증에 필요한데 별로 중요하지 않은 부분을 막 넘기는 느낌. 재미도 없고 설명도 빨리빨리 넘긴다고 느낌.
- 자막 어투가 약간 달라진거 같기도 함. 여러 사람이 동시에 번역했으려나...
- 사실 이런것까지 알아야 하나? 하는 생각도 들긴 함. 중반 넘어가면서부터 그런 생각이 계속 있음.
- 일단 마무리는 하고 싶어서 이렇게까지 왔지만, 다음에는 강의에서 다루는 내용이 제한적이라면 짦은 강의로 찾아봐야 할듯.
    - 이게 43시간 짜리인데, 다루는 범위가 "3계층 이하 네트워크 동작 + 네트워크 저수준 인프라 구축"임. 
    - 저 내용이였으면 5~15으로 3주 내외로 끊으면 더 좋을듯.

---

> Source: `section_35/ysj/note.md`

## Section 35 정리

1. QoS 배경과 필요성
- 과거: 음성, 영상, 데이터 네트워크가 물리적으로 분리
- 현재: 통합 네트워크로 전환 (비용 절감, 기능 향상)
- 문제점: 동일한 대역폭을 공유하면서 트래픽 간 경쟁 발생

2. 음성/영상 통화의 품질 요구조건
- 지연 시간: 150ms 이하
- 지터(지연 시간 편차): 30ms 이하
- 패킷 손실률: 1% 이하

3. 네트워크 혼잡 발생 원인
- 들어오는 트래픽 속도 > 나가는 트래픽 속도
- 예: 내부 인터페이스(100Mbps) > 외부 인터페이스(2Mbps)

4. 혼잡 해결 방법
- 대역폭 추가 (비용 증가)
- QoS 기술 활용 (우선순위 부여)
   - 음성 패킷을 대기열 앞으로 이동
   - 중요 트래픽의 지연, 지터, 손실 최소화

5. QoS 한계
- 일시적인 혼잡 완화용
- 지속적 혼잡 시에는 링크 업그레이드 필요
- 보통 링크 활용률 80% 목표로 운영

이 강의의 핵심은 통합 네트워크 환경에서 발생하는 트래픽 혼잡 문제를 QoS를 통해 효과적으로 관리하는 것입니다.

---

1. CoS (Class of Service)
- 2계층(Layer 2) QoS 표시 방식
- 802.1q 프레임 헤더의 3비트 필드 사용
- 값 범위: 0-7
   - 기본값: 0 (최선형 트래픽, Best Effort: 보장은 못하고, 네트워크 자원이 허용하는 범위 내에서 최선을 다해보긴 할게)
   - 6-7: 네트워크 제어용
   - 최대 사용 가능값: 5
- 사용 예시
   - 음성 페이로드: CoS 5
   - 통화 신호: CoS 3
CoS, 
2. DSCP (Differentiated Services Code Point)
- 3계층(Layer 3) QoS 표시 방식
- IP 헤더의 ToS 바이트 중 6비트 사용
- 값 범위: 0-63 (64개 값)
- 사용 예시
   - 음성 페이로드: DSCP 46(EF)
   - 통화 신호: DSCP 24(CS3)
   - 미션 크리티컬 데이터: DSCP 26(AF31)
   - SD 영상: DSCP 34(AF41)
   - HD 영상: CS4

3. 신뢰 범위 관리
- IP 전화기 등 신뢰할 수 있는 장치만 선별적으로 신뢰
- PC의 표시는 신뢰하지 않음
  - PC에서 오는 트래픽은 CoS 0/DSCP 0으로 강제 설정
  - 이유: 사용자가 임의로 우선순위를 높이는 것 방지
- 필요한 경우 관리자가 특정 애플리케이션/장치에 대한 예외 정책 설정

4. 중요 포인트
- 하나의 패킷이 CoS와 DSCP 값을 모두 가질 수 있음
- DSCP가 선호되는 이유: IP 헤더의 단일 바이트만 확인하면 되어 효율적
- 분류/표시만으로는 QoS 구성이 완료되지 않음
- 실제 서비스 제공을 위해서는 큐잉 설정 필요


다음과 같은 글을 보면 DSCP를 위주로 쓰는 듯? CoS는 거의 안쓰이거나 제한적으로 쓰이는 듯 하다.
https://community.cisco.com/t5/routing/when-to-use-cos-instead-of-dscp/m-p/2071709#M202684
이 글도 잘 설명해주는 듯?
https://white-polarbear.tistory.com/52 - QoS Classification and Marking

---

큐잉(혼잡 관리)에 대한 내용을 정리해드리겠습니다:

1. 큐잉의 종류
- CBWFQ (Class-Based Weighted Fair Queueing)
   - 특정 트래픽 종류에 대역폭 보장
   - 혼잡 시 지정된 대역폭 제공

- LLQ (Low Latency Queueing)
   - CBWFQ + 우선순위 큐
   - 특정 트래픽(음성/영상)에 우선순위 부여
   - 우선순위 트래픽을 대기열 앞쪽에 배치

2. MQC(모듈형 QoS 명령줄) 구성 3단계
- Class-map: 처리할 트래픽 정의
- Policy-map: 트래픽 처리 방법 지정
- Service-policy: 정책을 인터페이스에 적용

3. 대역폭 할당 예시
- 전체 대역폭: 768Kbps
- 음성 트래픽: 33%(256Kbps) - 우선순위 큐
- 통화 신호: 5% - 일반 큐
- 나머지 트래픽: fair-queue (공정한 라운드 로빈 방식)

4. 중요 특징
- Priority percent: 지정된 비율까지만 사용 가능
- Bandwidth percent: 최소 보장, 여유 있으면 추가 사용 가능
- Class-default: 지정되지 않은 모든 트래픽
- 혼잡 상황에서만 큐잉 정책이 효과 발생

5. 실제 적용 시 주의사항
- 서비스 정책을 인터페이스에 적용하는 마지막 단계 필수
- 현실에서는 더 큰 대역폭 사용

---

1. 트래픽 정형화(Shaping)와 감시(Policing)의 차이
- 정형화
   - 초과 트래픽을 통제하여 일정 속도 유지
   - 트래픽 흐름을 매끄럽게 조절
   - 주로 고객 측에서 사용
   
- 감시
   - 초과 트래픽을 폐기하거나 표기
   - 더 공격적인 방식
   - 주로 서비스 제공자 측에서 사용
   - Note: CE 라우터 쪽 인터페이스의 PE에 유입되는 트래픽에 감시 QoS 정책을 구성

2. 주요 사용 사례
- 서비스 제공자 시나리오
   - 물리적 링크: 100Mbps
   - 계약된 대역폭: 10Mbps
   - PE 라우터에서 감시 정책으로 초과 트래픽 폐기

- 기업 네트워크 사용 사례
   - Worm 트래픽 제어
   - 불필요한 트래픽(P2P, 스캐빈저 트래픽) 제한
   - DSCP 8 또는 CS1로 표시하여 관리

3. 정형화와 LLQ 결합 예시
- 전체 대역폭: 10Mbps
- 세부 할당
   - 음성: 1Mbps (우선순위)
   - 영상: 3Mbps (우선순위)
   - 데이터: 6Mbps
- 혼잡 발생 시 음성/영상 트래픽 우선 처리

4. 중요 포인트
- 트래픽 종류별로 다른 속도 설정 가능
- 정형화와 큐잉을 함께 사용하여 효과적인 트래픽 관리 가능

---

## 정리

- QoS
   - 좁은 범위로는 네트워크 상의 자원 분배, 넒은 범위로는 서비스 품질을 의미. 강의에서는 네트워크 강의이므로 좁은 범위를 의미함.

- QoS 메커니즘: QoS를 수행하는 방법
   - 큐잉: 제일 보편적인 방식. 우선순위나 여러 조건을 사용한 혼잡 관리. (중요한 것부터 먼저 처리)
   - 정형화: 초과 트래픽을 통제. 주로 고객 측에서 사용
   - 감시: 초과 트래픽을 폐기하거나 표기. 공격적인 방식. 주로 서비스 제공자 측에서 사용

- QoS가 필요한 이유
   - 여러 네트워크 망이 분리된 상태에서 통합 네트워크로 전환되어가는 중. (비용 절감, 기능 향상)
   - 동일한 대역폭을 공유하면서 트래픽 간 경쟁 문제 발생
   - 음성과 영상 패킷에는 품질 요구 조건이 있는데, 이러한 조건을 지키기 위해서는 트래픽의 우선순위를 나눠 처리할 필요성이 생김.

- (프로토콜이랑 구체적인 내용은 스킵)



---

> Source: `section_36/ysj/note.md`

## Section 36 정리

### 온프레미스 vs 클라우드

1. **온프레미스 솔루션**
- 회사 내부 건물에 IT 장비(서버, 네트워크 장비 등)를 배치 및 소유.
- 자본 비용(CapEx)과 운영 비용(OpEx) 발생.
- 장비 구매, 설치, 구성에 시간이 걸림(약 1주일 이상).
- 모든 장비 관리와 다중화 비용 부담.
- 명확한 책임 경계(내부는 회사 책임, 외부 연결은 서비스 제공자 책임).

2. **콜로케이션(콜로)**
- 외부 데이터 센터에 IT 장비를 배치.
- 데이터 센터 소유주가 전력, 냉각, 보안을 제공.
- IT 장비는 회사가 소유, 데이터 센터의 물리적 공간만 임대.
- 네트워크 연결은 별도의 서비스 제공자가 담당.
- CapEx와 OpEx 발생(장비 구매 및 월 임대료).
- 온프레미스와 유사한 배포 및 구성 방식(시간 소요).
- Note: 콜로케이션은 온프레미스라고 부르기도 하는 듯?

3. **클라우드 컴퓨팅**
- **정의**: NIST 기준, 네트워크를 통해 컴퓨팅 자원을 유비쿼터스, 온디맨드 방식으로 공유.
- **특징**:
  - **주문형 셀프-서비스**: IT 부서 요청 없이 GUI 기반으로 자원 프로비저닝 가능.
  - **신속한 탄력성**: 자원 크기 조정이 빠르고 필요 시 자동 확장/축소.
  - **광대역 네트워크 액세스**: 다양한 장치 및 위치에서 네트워크를 통한 접근 가능.
  - **자원의 공동관리**: 멀티테넌트 모델로 비용 절감 및 자원 효율화.
  - **측정 가능한 서비스**: 사용량 기반으로 자동 측정 및 요금 책정.
- **장점**: 빠른 배포, 유연성, 비용 효율성(OpEx 기반).

4. **비교**
- 온프레미스와 콜로는 장비를 직접 소유하고 CapEx 비용 발생.
- 클라우드는 자원 공유, 유연한 확장, 측정 가능한 서비스 등 기존 모델과 차별화됨.

---

### 클라우드의 가상화

1. **가상화의 개념과 중요성**:
   - 가상화는 클라우드 컴퓨팅의 핵심 기반 기술로, 물리적 하드웨어의 효율성을 높이기 위해 여러 운영 체제 및 애플리케이션을 분리된 환경에서 실행할 수 있게 함.
   - 초기에는 물리적 서버에서 각 애플리케이션을 독립적으로 실행했으나, 활용률이 낮고 비용이 비효율적이었음.

2. **서버 가상화**:
   - **하이퍼바이저**를 통해 물리적 서버를 분리된 가상 머신(VM)으로 구분.
   - VM마다 독립된 운영 체제와 애플리케이션이 실행되며, 문제 발생 시 다른 VM에 영향을 주지 않음.
   - Note: 데이터센터에서는 타입 1을 사용함.
   - 하이퍼바이저 유형:
     - **타입 1**: 하드웨어에서 여러 OS를 직접 실행(예: VMware ESXi, Microsoft Hyper-V).
     - **타입 2**: 호스트 운영 체제 위에서 실행(예: VMware Workstation, VirtualBox).

3. **컨테이너**:
   - 운영 체제를 가상화하지 않고 애플리케이션과 종속성만 포함.
   - 가볍고 이식성이 뛰어나며, 마이크로서비스와 같은 소규모 애플리케이션에 적합.
   - 대표 도구: Docker.

4. **네트워크 가상화**:
   - 가상 스위치를 통해 여러 VM이 동일한 물리적 네트워크 연결을 공유 가능.
   - VLAN 태그를 통해 트래픽을 분리 및 관리.
   - 라우터를 통해 다른 서브넷 간 통신이 가능.

5. **활용 사례**:
   - 클라우드 환경에서 비용 절감 및 효율적 리소스 사용.
   - 데이터센터에서는 타입 1 하이퍼바이저가 주로 사용되며, 실험용으로는 타입 2 하이퍼바이저 활용.

가상화는 클라우드 컴퓨팅에서 리소스를 효과적으로 사용하고 확장 가능성을 높이는 핵심 기술임.


---

### 클라우드 배포 모델 요약

1. **퍼블릭 클라우드 (Public Cloud)**  
   - **특징**: 클라우드 인프라가 **일반 대중**에게 제공되며, 기업, 학계, 정부 기관 등이 소유, 운영 가능.  
   - **장점**: 낮은 초기 비용, 유연한 확장성, 유지보수 책임 전가.  
   - **예시**:  
     - AWS, Microsoft Azure, Google Cloud는 IaaS, PaaS, SaaS 지원.  
     - Salesforce는 SaaS 전문.  

2. **프라이빗 클라우드 (Private Cloud)**  
   - **특징**: 하나의 **조직 전용** 클라우드 인프라. 내부 혹은 제삼자에 의해 운영 가능.  
   - **장점**: 높은 보안성, 조직 특화, 기존 온프레미스보다 자동화된 워크플로 제공.  
   - **차이점**: 퍼블릭 클라우드처럼 주문형 셀프 서비스, 네트워크 액세스, 리소스 풀링 등 클라우드의 핵심 특성을 충족.  
   - **예시**:  
     - 미국 국방부의 AWS 기반 프라이빗 클라우드.  

3. **커뮤니티 클라우드 (Community Cloud)**  
   - **특징**: 공통의 목적이나 규제 요건을 공유하는 **여러 조직**이 인프라를 공동 이용.  
   - **장점**: 협업과 비용 분담, 특정 요구 충족.  
   - **사용 사례**: 정부 기관 간 협력, 의료 단체 간 데이터 공유.  

4. **하이브리드 클라우드 (Hybrid Cloud)**  
   - **특징**: 퍼블릭, 프라이빗, 커뮤니티 클라우드를 **조합**하여 구성.  
   - **장점**: 유연한 확장성, 비용 절감, 재해 복구 지원.  
   - **사용 사례**:  
     - 클라우드 버스팅: 프라이빗 클라우드의 용량 부족 시 퍼블릭 클라우드 사용.  
     - 재해 복구: 본사는 프라이빗 클라우드, 재해 복구는 퍼블릭 클라우드 활용.  

---

### **클라우드 서비스 모델**
1. **IaaS (Infrastructure as a Service)**  
   - 제공자가 네트워크, 저장소, 컴퓨팅 기반 구조 등 하드웨어와 하이퍼바이저까지 관리.
   - 고객은 운영 체제, 애플리케이션, 데이터 등을 직접 관리.
   - 예: Amazon EC2, Google Compute Engine.
   
2. **PaaS (Platform as a Service)**  
   - 제공자가 하드웨어와 운영 체제, 플랫폼을 제공하고 관리.
   - 고객은 애플리케이션과 데이터만 관리.
   - 주로 개발 환경 제공에 사용.
   - 예: Microsoft Azure, Google App Engine, IBM Bluemix.

3. **SaaS (Software as a Service)**  
   - 제공자가 모든 것을 관리(하드웨어, 운영 체제, 소프트웨어, 데이터).
   - 고객은 애플리케이션을 서비스로 사용.
   - 예: Microsoft Office 365, Salesforce, Google Workspace.

---

### **온프레미스 및 클라우드 비교**
- **온프레미스**: 모든 하드웨어와 소프트웨어를 직접 구매, 설치, 관리.
- **콜로케이션 (Colocation)**: 일부 하드웨어는 고객이 관리하되, 물리적 환경과 네트워크 장비는 제공자가 관리.
- **클라우드 솔루션**: 제공자가 대부분의 관리 업무를 담당, 필요에 따라 IaaS, PaaS, SaaS 중 선택.

---

### **클라우드 컴퓨팅의 장점**
1. **확장성**  
   - 필요에 따라 용량을 유연하게 늘리거나 줄일 수 있음.
   - 프로젝트 기반으로 자원을 효율적으로 활용 가능.

2. **비용 효율성**  
   - 초기 투자 비용(CapEx) 대신 월 사용료(OpEx)로 전환.
   - 감가상각과 하드웨어 갱신 부담 해소.

3. **유연성 (클라우드 버스팅)**  
   - 온프레미스와 클라우드를 혼합해 사용 가능.
   - 일시적 부하 증가에 대응.

4. **비즈니스 민첩성**  
   - 신속한 서버 프로비저닝 및 애플리케이션 배포.
   - 변화하는 시장에 빠르게 대응 가능.

5. **생산성**  
   - IT 부서가 하드웨어 관리 대신 전략적 업무에 집중 가능.

6. **가용성과 안정성**  
   - 대규모 데이터 센터와 높은 신뢰성을 보장.
   - ISO 27001 등의 인증을 기반으로 한 보안 및 품질 관리.

7. **경쟁 우위**  
   - 혁신에 더 많은 자원을 투자할 수 있어 시장에서 유리한 위치 확보.

8. **고려 사항**
- 비용 분석: 클라우드 도입 시 장기적인 TCO(Total Cost of Ownership)와 온프레미스 유지 비용을 비교.
- 혼합 사용: 클라우드와 온프레미스를 동시에 활용해 각 솔루션의 장점을 최대화.

--- 

### 네트워크 가상화 추가 정리

1. VLAN 기반 가상 네트워킹
- 구성 요소:
  - 가상 스위치 (소프트웨어)
  - 물리적 호스트와 VM들
  - 트렁크 포트 연결
- 특징:
  - VLAN으로 트래픽 분리
  - 단일 물리적 연결로 다중 VLAN 지원

2. 가상 라우터 기반 구성
- 구성 방식:
  - VM으로 라우터 구현 (예: Cisco CSR 1000V)
  - 고급 라우팅 기능 제공
- 장점:
  - 클라우드 환경에서 커스텀 라우팅 가능
  - 여러 VM 간 라우팅 제어

3. 방화벽 가상화 (Cisco ASA)
- 구성:
  - 관리자 콘텍스트
  - 고객별 보안 콘텍스트
- 특징:
  - 독립적 방화벽 기능
  - 고객별 관리 권한 부여 가능

4. VRF 기반 구성
- 특징:
  - 단일 라우터에서 다중 라우팅 테이블
  - MPLS VPN 서비스 지원
- 용도:
  - 고객/부서별 트래픽 분리
  - 보안 강화

5. 클러스터링
- 특징:
  - 다중 물리적 시스템을 단일 가상 시스템으로 통합
- 장점:
  - 성능 향상
  - 안정성 강화
  - 효율적 다중화


---

> Source: `section_37/ysj/note.md`

## Section 37 정리

### 무선 네트워크의 종류

1. Wi-Fi 네트워크 유형
- WPAN (무선 개인 영역): 10m 이내, 블루투스 사용
- WLAN (무선 로컬): 100m 이내, 캠퍼스/기업용
- WMAN (무선 대도시): 도시 규모 네트워크

- Note:
    - AP(Access Point): 무선 네트워크의 핵심 장비, 무선 장치들이 유선 네트워크에 접속할 수 있게 해주는 중계기 역할. (e.g. Wi-Fi 공유기)

2. 네트워크 운영 모드
- Ad Hoc (IBSS): 
  - 장치 간 직접 통신
  - 확장성 한계 있음
  
- 인프라 모드:
  - AP 통한 통신
  - 유선 네트워크 연결 가능
  - 다수 AP 배치로 확장 가능

- 무선 스테이션은 Ad Hoc 또는 인프라 모드, 둘 중 하나를 운용

3. 특수 기능
- Wi-Fi Direct: 
  - 인프라+P2P 동시 지원 - Note: 정확히는 인프라 모드긴 함.
  - Miracast, DLNA, Direct Print 제공
  

- 무선 브리지:
  - 건물 간 무선 연결
  
- 메시 네트워크:
  - 5GHz 백홀로 AP 간 연결
  - 통신 영역 확장 용이

### IEEE 802.11 표준의 주요 용어와 개념

각 개념을 자세히 설명해드리겠습니다:

1. 기본 개념
- BSS (기본 서비스 세트)
  - AP를 중심으로 형성된 하나의 무선 네트워크 단위
  - 모든 무선 장치는 AP를 통해 통신
  - IBSS(애드혹)와 달리 AP가 중앙 통제

- DS (분배 시스템)
  - AP와 기존 유선 네트워크를 연결하는 인프라
  - 주로 스위치나 라우터로 구성
  - 여러 BSS를 하나의 네트워크로 통합

- 반이중 통신
  - 무선 특성상 한 시점에 한 장치만 데이터 전송 가능
  - 허브처럼 작동하여 충돌 가능성 존재
  - 효율적인 대역폭 사용을 위해 관리 필요

2. 식별자
- BSSID
  - 각 AP의 고유 MAC 주소
  - 네트워크에서 AP를 구분하는 식별자
  - 48비트 주소 체계 사용

- SSID
  - 사용자가 인식할 수 있는 네트워크 이름
  - 하나의 AP에서 여러 SSID 운영 가능
    예: "Company_Staff", "Company_Guest"
  - SSID별 다른 보안 정책 적용
    - 직원용: WPA2-Enterprise + 사용자인증
    - 게스트용: 간단한 비밀번호
  - VLAN 매핑으로 네트워크 분리
    - 직원용: 내부 리소스 접근 가능
    - 게스트용: 인터넷만 접근 가능

3. 커버리지
- BSA
  - AP의 실제 무선 신호가 도달하는 물리적 범위
  - 보통 실내 100m, 실외 300m 정도
  - 건물 구조, 장애물에 따라 변동

- ESS
  - 여러 BSS를 하나의 논리적 네트워크로 통합
  - 각 AP는 다른 채널 사용하여 간섭 방지
  - 끊김 없는 연결성 제공

- 로밍
  - 사용자가 AP 간 이동시 자동 전환
  - 같은 SSID를 가진 AP 간에만 가능
  - 신호 강도에 따라 최적의 AP 선택

### 무선 LAN 컨트롤러 및 CAPWAP

1. WLC(무선 랜 컨트롤러) 개요
- 다수의 AP를 중앙 관리
- 하드웨어/소프트웨어/블레이드 형태 제공
- 이중화 지원으로 안정성 보장

2. AP 유형
- 자율(Autonomous) AP: 독립적 운영
- 경량(Lightweight) AP: WLC 관리 하에 운영 - 작업량이 줄어들었기 때문 
- 같은 하드웨어도 소프트웨어로 모드 전환 가능

3. ZTP(Zero Touch Provisioning)
- AP가 자동으로 WLC 검색
    - 액세스 포인트를 관리하기 쉽게 만듦
- 검색 방법: - 중 1
  * DHCP 옵션 43
  * DNS 조회
  * 로컬 서브넷 브로드캐스트

4. WLC 주요 기능
- WLAN 설정 관리
- AP 채널/전력 제어
- 비인가 AP 탐지
- 끊김 없는 로밍 지원 - Note: WLC가 인증을 수행하므로, WLAN이 바뀌어도, 같은 WLC 관리하에 있으면 연결이 유지됨.

5. CAPWAP 프로토콜
- WLC와 AP 간 통신에 사용되는 프로토콜
- UDP 포트 5246/5247 사용 - 방화벽 조건 확인
- DTLS 암호화 적용

6. Split MAC 구조
- WLC(무선 랜 컨트롤러)와 AP(액세스 포인트) 간의 작업 분담 구조
- AP 처리: 실시간 트래픽, 비콘, 암호화
- WLC 처리: 인증, 로밍, RF 관리, QoS

7. FlexConnect
- 일반적으로 모든 트래픽이 WLC를 거쳐야 함
- 지사 사무실에서 본사 WLC까지 가는 것은 비효율적임. 불필요한 지연이 발생함.
- 로컬 트래픽은 멀리까지 안보내고 근처에서 처리함
- 지사 사무실용 특수 모드
- WAN 대역폭 절약
- 중앙 관리는 유지하되, 소규모 지사 사무실에서 WLC 설치 비용을 절감하고 싶은 경우 유용함.

### 무선 네트워크를 위한 스위치 구성

1. 자율(단독형) AP 구성
- VLAN 생성: 기업용(21), 게스트용(22) 
- AP 연결 포트: 트렁크 모드
  * 여러 VLAN 트래픽 처리 필요
  * 각 WLAN의 트래픽을 해당 VLAN으로 태그

2. WLC(무선 랜 컨트롤러) + 경량 AP 사용 시 구성
- VLAN 생성
  * 기업용(21), 게스트용(22)
  * 관리용(10): 관리자가 WLC에 접속하여 설정을 변경하기 위한 용도
  * AP관리용(11): AP와 WLC 간의 CAPWAP 통신을 위한 용도

- 포트 구성
  * WLC 연결 포트: 트렁크 모드 (모든 VLAN 허용)
  * AP 연결 포트: 액세스 모드 (관리 VLAN만 사용)

주요 차이점:
- 자율 AP: AP가 직접 VLAN 태그 처리
- WLC 사용: WLC가 중앙에서 VLAN 태그 처리, AP는 CAPWAP 터널 통해 통신

### 무선 채널 및 라디오 주파수


1. 정부에서 각 목적별로 주파수 대역 할당 및 규제
예) FM 라디오: 88-108MHz

2. 대부분의 주파수는 면허 필요
- 라디오 방송국 설립 시 특정 주파수 사용 허가 필요
- 간섭 방지를 위한 규제

3. ISM 대역(WiFi 사용)
- 면허 불필요
- 누구나 사용 가능
- 간섭에 대한 보호 없음
- 설치는 쉽지만 간섭 위험 높음

4. WiFi 주파수 대역
- 2.4GHz와 5GHz 사용
- ISM(산업, 과학, 의료용) 대역으로 면허 불필요
- 간섭 가능성 있음

5. WiFi 표준 발전
- 802.11 (1997): 2.4GHz, 2Mbps
- 802.11a/b (1999): 5GHz/2.4GHz, 54/11Mbps
- 802.11g (2003): 2.4GHz, 54Mbps
- 802.11n (2009): 듀얼밴드, 600Mbps
- 802.11ac (2013): 5GHz, 3500Mbps
- WiFi 6 (2019): 듀얼밴드, 9608Mbps

6. 채널 특성
2.4GHz:
- 22MHz 채널 폭
- 채널 범위가 겹치는게 많으므로 간섭 많음. - 특히 2.4GHz는 많은 기기에서 사용되므로
- 비중첩 채널은 최대 3개 3개(1,6,11)
- 범위 넓고 장애물 통과 우수

5GHz:
- 20MHz 기본 채널 폭
- 채널 결합 가능(20/40/80/160MHz) - 그럼 데이터 전송 속도 빨라짐
- 도달 거리, 벽 투과율이 낮아 주변 기기와 간섭 가능성 낮음
- 채널 겹합이 가능해서 처리량 높음

7. 네트워크 설계 고려사항
- 사이트 조사 필요
- AP 위치 최적화
- 간섭원 파악
- WLC로 채널/전력 관리

### 무선 보안

1. 무선 보안의 필요성
- 신호의 물리적 경계 통제 어려움
- 물리적 접근 없이도 네트워크 접속 가능
- 주차장 등 외부에서 침입 위험 - 막기 어려움 or 불가능

2. 보안 표준 발전
- WEP (1999): RC4 암호화, 취약점 발견
- WPA (2003): TKIP 도입
- WPA2 (2004): AES 암호화, CCMP 지원
- WPA3 (2018): KRACK 공격 방어, 현재 최신 표준

3. WPA 인증 방식
WPA Personal:
- 사전 공유 키 사용
- 홈 네트워크에 적합
- 관리 부담 있음 (비밀번호 변경 필요)

WPA Enterprise:
- AAA 서버 사용 (RADIUS, 802.1X)
- 사용자 단위 보안 관리
- 기업환경에 적합
- 확장성 우수

권장사항: 최소 WPA2 이상 사용, 기업은 Enterprise 방식 채택

---

> Source: `section_38/ysj/note.md`

## Section 38 정리

### Python, Git, GitHub 및 CI-CD

(아는 내용이라 생략)

### JSON, XML, YAML

(아는 내용이라 생략)

### APIs - CRUD, REST 및 SOAP

(대부분 아는 내용이라 생략)

**웹 서비스 API의 주요 유형**
1. **SOAP (Simple Object Access Protocol)**
   - **프로토콜 기반**.
   - **XML** 형식의 데이터 사용.
   - **엄격한 표준** 준수 (프로토콜 명세 명확).
   - 일반적으로 HTTP/HTTPS를 통해 전송.
   
2. **REST (Representational State Transfer)**
   - **아키텍처 기반** (프로토콜 아님).
   - 구조와 지침 제공 (SOAP보다 유연).
   - 다양한 데이터 형식 지원:
     - 일반적으로 **JSON**과 **XML** 사용.
   - HTTP/HTTPS 전송 방식 사용.
   - 현대 웹 API에서 가장 널리 사용.

**RESTful API의 특징 및 제약 조건**
- **클라이언트-서버 아키텍처**: 클라이언트가 요청, 서버가 응답.
- **상태 비저장 (Stateless)**: 요청 간 서버에 클라이언트 상태 저장 없음.
  - 요청마다 인증 정보 포함.
- **캐시 가능**: 서버가 응답을 캐시 가능 여부로 정의.
- **계층화된 시스템**: 클라이언트와 서버 사이의 중간 계층 투명성.
- **선택적 코드 온디맨드 (Code on Demand)**: 서버에서 클라이언트로 실행 코드 전송 가능.

### 모델 주도 프로그램화 - YANG, NETCONF, RESTCONF 및 gRPC


모델 주도 프로그램화는 네트워크 자동화와 관련이 있음.

YANG이라는 데이터 모델링 언어로 네트워크 정보를 구성

NETCONF RESTCONF 및 gRPC는 네트워크 관리 데이터 전송을 위한 프로토콜

JSON, XML, GPB 등의 형식으로 YANG 데이터를 전송

내부적으로 YANG에 정의된 구성대로 자동으로 네트워크를 관리

그냥 k8s 생각하면 될듯?


**1. 데이터 모델과 YANG**
- **데이터 모델**: 데이터의 구성 및 배치를 설명하는 표준화된 형식(스키마).  
  예: 자동차 대리점 데이터베이스의 구조 (Make → Model → Trim).
- **YANG**:  
  - "Yet Another Next Generation"의 약자.  
  - 2010년 IETF 표준화.  
  - 네트워크 장치의 구성 및 운영 데이터를 표현하는 데이터 모델링 언어.  
  - 장치 내부 및 API 전송에 사용.  

**2. NETCONF**
- **개요**:  
  - 2006년 IETF 표준화.  
  - YANG 데이터와 원격으로 상호작용(읽기/쓰기)할 수 있는 프로토콜.  
  - SNMP를 보완/대체하며 보안 및 쓰기 기능 강화.
- **특징**:  
  - XML 인코딩, 일반적으로 SSH/TLS를 통해 전송.  
  - RPC(원격 프로시저 호출) 기반으로 데이터 작업 수행.
- **프로토콜 스택**:  
  - **Transport**: SSH/TLS.  
  - **Messages**: RPC 사용.  
  - **Operations**: CRUD 작업.  
  - **Content**: YANG 데이터를 포함.

**3. RESTCONF**
- **개요**:  
  - NETCONF 기반으로 RESTful 접근 방식을 사용.  
  - YANG을 REST API에 매핑하는 방식으로 동작.
- **특징**:  
  - 2017년 표준화.  
  - XML 또는 JSON 지원, HTTP/HTTPS 전송.  
  - HTTP 동사(GET, POST, PUT, DELETE 등)로 작업.
- **프로토콜 스택**:  
  - **Transport**: HTTP/HTTPS.  
  - **Operations**: CRUD 작업(HTTP 기반).  
  - **Content**: XML 또는 JSON.

**4. gRPC**
- **개요**:  
  - 2015년 Google에서 개발한 오픈소스 RPC 시스템.  
  - 원격 분석 데이터 수집에 적합.  
  - XML/JSON 대신 GPB(Google Protocol Buffers) 사용.
- **특징**:  
  - HTTP/2 전송.  
  - 대규모 IoT 환경에서 효율적.  

---

#### model driven programmability stack 주요 개념 정의

- **네트워크 관리**: 네트워크와 서비스 수명 주기를 관리하는 데 필요한 프로세스, 도구, 기술 및 역할을 포괄하는 용어.

- **자동화**: 시스템이 수동 작업을 자동으로 수행하도록 하는 기술.

- **오케스트레이션**: 여러 시스템의 작업을 조정하여 전체 작업을 완료하는 기능.

- **데이터 모델링**: 데이터 유형과 계층 구조를 설명하는 방법. 네트워크 프로그래밍에서는 주로 YANG 언어를 사용.

- **프로그래밍 가능성**: API를 통해 시스템의 데이터를 검색하거나 구성을 푸시하는 기능.

- **API (Application Programming Interface)**: 소프트웨어 간 상호 작용을 위해 설계된 시스템 인터페이스.

네트워크 프로그래밍 가능성은 6개 계층으로 구성된 스택으로 요약됩니다.
1. 애플리케이션
2. 모델
3. 프로토콜
4. 인코딩
5. 전송
6. 인프라구조

- **프로토콜**: NETCONF, RESTCONF, gRPC가 주로 사용됨.
- **데이터 인코딩**: XML, JSON, YAML, GPB가 일반적.

- 참고하면 좋을 글
    - Introduction to Programmability 시리즈
        - https://blogs.cisco.com/developer/intro-to-programmability-1
        - https://blogs.cisco.com/developer/intro-to-programmability-2
        - https://blogs.cisco.com/developer/intro-to-programmability-3


## 구성 관리 도구 - Ansible 및 Terraform

### 구성 관리 도구와 네트워크 자동화 요약  

**1. 구성 관리 도구 개요**  
- 프로그래밍 전문가가 아니더라도 네트워크 자동화를 구현할 수 있는 도구 제공.  
- 주요 도구: **Ansible, Puppet, Chef, Terraform** (모두 무료 오픈 소스, 유료 엔터프라이즈 에디션 제공).  
- 자동화를 통해 여러 장치를 중앙에서 제어, 네트워크 및 서버 구성 간소화.  

**2. 각 도구의 특징 및 비교**  

**Ansible**  
- **특징**: 에이전트리스, 푸시 모델, YAML 기반.  
- **장점**:  
  - SSH를 통해 장치를 중앙에서 제어.  
  - 쉬운 학습 곡선, 네트워크 관리에 적합.  
  - Python으로 작성, Linux/Mac에서 실행.  
- **작동 방식**:  
  - 인벤토리 파일로 관리할 장치 정의.  
  - 플레이북(YAML 파일)로 작업 지침 작성.  
  - 미리 작성된 모듈로 네트워크 구성을 간단히 수행.  
- **적합성**: 구성 관리 도구로 우수, 초기 설정 간단.  

**Puppet**  
- **특징**: 에이전트 기반(에이전트리스 옵션 있음), 풀 모델, Ruby 기반 DSL 사용.  
- **장점**:  
  - 장치가 Puppet Master에 주기적으로 체크인하여 구성 유지(30분마다).  
  - 구성 일관성 유지에 유리.  
- **작동 방식**:  
  - Puppet Master(Linux 서버)에서 모든 작업 제어.  
  - 매니페스트로 장치 속성 정의.  
- **적합성**: 서버 관리에 적합하지만, 네트워크 관리에는 에이전트 제약 존재.  

**Chef**  
- **특징**: 에이전트 기반, 풀 모델, Ruby 기반.  
- **작동 방식**:  
  - Cookbooks와 Recipes로 구성 작업 정의.  
  - Puppet과 유사, 2009년에 출시.  
- **적합성**: 서버 관리에 적합, 네트워크 환경에서는 활용 제한.  

**Terraform**  
- **특징**: 에이전트리스, 푸시 모델, 선언적 접근 방식 사용.  
- **장점**:  
  - 코드형 인프라 도구로 인프라를 자동으로 프로비저닝.  
  - 클라우드 환경 및 온프레미스 플랫폼에서 사용 가능.  
  - 상태 파일로 리소스 변경 추적 및 자동 관리.  
  - 플랫폼 플러그인(Providers)을 통해 AWS, Cisco 등 다양한 환경 지원.  
- **작동 방식**:  
  - 설정 파일로 원하는 최종 상태 정의.  
  - 계획(Plan) → 실행(Apply) → 상태 업데이트(Consolidate).  
- **적합성**: 인프라 초기 프로비저닝에 매우 적합.  


**3. 에이전트(Agent)와 에이전트리스(Agentless)의 차이**  

| **구분**            | **에이전트 기반**                           | **에이전트리스**                       |
|---------------------|--------------------------------------------|---------------------------------------|
| **설치 요구**       | 대상 장치에 소프트웨어(에이전트) 설치 필요    | 별도의 소프트웨어 설치 불필요           |
| **작동 방식**        | 장치 내부 에이전트가 작업 수행 및 상태 보고   | SSH, REST API 등 기존 프로토콜로 직접 명령 실행 |
| **장점**            | 지속적 상태 관리, 고급 작업 가능              | 설정 간편, 호환성 높음, 리소스 절약       |
| **단점**            | 설치와 유지보수 필요, 장치 리소스 사용         | 상태 관리와 복잡한 작업에 한계           |
| **대표 도구**       | Puppet, Chef                               | Ansible, Terraform                    |

**적합한 경우**  
- **에이전트 기반**: 지속적 상태 관리, 데이터센터 운영.  
- **에이전트리스**: 네트워크 초기 설정, 간단한 환경 구성.  
**네트워크 자동화**에서는 보통 **에이전트리스**가 선호됨.


**4. 통합 사용 가능성**:  
  - Terraform으로 초기 인프라 프로비저닝 후 Ansible로 구성 관리.  
  - 반대로 Ansible 플레이북에서 Terraform 호출하여 환경 설정도 가능.  

**5. 결론**  
- 네트워크 자동화를 위해 **Ansible**과 **Terraform**이 가장 적합.  
- 두 도구를 함께 사용하면 초기 프로비저닝부터 구성 관리까지 원활히 수행 가능.  
- 사용 목적에 따라 적합한 도구 선택 필요(예: Terraform은 프로비저닝, Ansible은 세부 구성).

### Ansible 랩 데모

(생략)

### SDN 소프트웨어 정의 네트워킹

**1. 네트워크 플레인의 세 가지 구성 요소**  
- **데이터 플레인**: 트래픽(패킷)이 장치를 통해 전달됨.  
- **제어 플레인**: 트래픽 경로를 결정(예: OSPF 업데이트).  
- **관리 플레인**: 네트워크 장치 구성 및 모니터링(Telnet, SSH, SNMP).  

**2. SDN의 개념**  
- **기존 모델**: 데이터 플레인과 제어 플레인이 각 장치에 통합.  
- **SDN 모델**:  
  - 데이터 플레인과 제어 플레인을 분리.  
  - 제어 플레인은 중앙 **SDN 컨트롤러**에서 관리.  
  - 장치는 데이터 플레인 역할만 수행.  

**3. SDN 아키텍처**  
- **애플리케이션 계층**: 사용자 인터페이스, REST API로 SDN 컨트롤러와 통신.  
- **제어 계층**: SDN 컨트롤러, 네트워크 지능 관리.  
- **인프라 계층**: 라우터, 스위치 등의 물리 장치.  
  - **사우스바운드 API**: SDN 컨트롤러 ↔ 장치 연결(OpenFlow, SNMP, RESTCONF).  
  - **노스바운드 API**: SDN 컨트롤러 ↔ 비즈니스 애플리케이션 연결(REST).  

**4. SDN 구현 방식**  
- **순수 SDN**: 제어 플레인과 데이터 플레인 완전 분리.  
- **하이브리드 SDN**: 일부 제어 플레인을 장치에 유지(Cisco 등 대부분의 구현).  

**5. Cisco의 SDN 컨트롤러**  
- **APIC**: 데이터 센터용. Nexus 스위치 제어.  
- **APIC-EM**: 기업 환경용(캠퍼스, 지사, WAN).  
- **DNA Center**: APIC-EM의 업그레이드(현재는 Catalyst Center로 이름 변경).  

SDN은 네트워크를 더 유연하고 효율적으로 관리할 수 있는 구조를 제공하며, 중앙 집중화된 제어와 자동화를 가능하게 합니다.

### 1. Catalyst Center (구 DNA Center)

##### 개요
- Cisco의 **SDN 컨트롤러**이자 **의도 기반 네트워킹(IBN)** 플랫폼
- "무엇을" 하고 싶은지만 지정하면 "어떻게" 할지는 시스템이 자동 결정
- 네트워크를 **중앙 통합 방식**으로 관리

##### 주요 기능
1. **네트워크 관리**
   - 비즈니스 의도를 네트워크 정책으로 자동 변환
   - QoS, 보안 정책의 중앙 관리 및 자동 배포
   
2. **프로비저닝**
   - 플러그 앤 플레이(PnP) 자동 구성
   - 원격 장치 설정 및 관리
   
3. **보증(Assurance)**
   - 네트워크 상태 실시간 모니터링
   - 자동 문제 감지 및 해결 방안 제시
   
4. **운영 체제 관리**
   - 자동화된 OS 버전 관리
   - Golden Image 기반 일관된 배포
   
5. **사용자 기반 액세스**
   - Cisco ISE 연동
   - 사용자 인증 기반 접근 제어

### 구현 특징
- **REST API** 지원으로 프로그래밍 가능
- 클라우드/온프레미스 유연한 배치
- 클러스터링 통한 고가용성

#### 2. SD-Access

##### 특징
1. **신원 기반 접근 제어**
   - 물리적 위치 독립적 접근
   - ISE 및 Catalyst Center 연동
   
2. **네트워크 구조**
   - 언더레이: 물리적 네트워크 인프라
   - 오버레이: VXLAN 기반 가상 네트워크
   
3. **핵심 기술**
   - LISP: 사용자 이동성 지원
   - VXLAN: 가상 네트워크 구현
   - TrustSec: SGT 기반 트래픽 제어

##### 장점
- 기존 네트워크와 호환
- 유연한 사용자 이동성
- 중앙화된 정책 관리

#### 3. SD-WAN

##### 구성요소
1. **데이터 평면**: WAN 엣지 라우터
2. **제어 평면**: SD-WAN 컨트롤러
3. **관리 평면**: SD-WAN 매니저
4. **오케스트레이션**: SD-WAN 검증자

##### 주요 특징
- 자동화된 구성 및 장애 조치
- 전송 방식 독립성
- 애플리케이션 기반 라우팅
- 클라우드 통합

#### 4. Cisco Meraki

##### 개요
- 클라우드 기반 네트워크 관리
- 2012년 Cisco 인수
- 단일 대시보드 통합 관리

##### 제품군
- **MX**: 보안/라우팅
- **MS**: 스위치
- **MR**: 무선 AP
- **MV**: 스마트 카메라
- **MT**: IoT 센서
- **Systems Manager**: 엔드포인트 관리

##### 특징
- 클라우드 기반 중앙 관리
- 제로 터치 프로비저닝
- 템플릿 기반 구성
- 실시간 모니터링
- SD-WAN 기능 통합

### 리뷰

- 요즘에 인프라도 k8s같이 오케스트레이션 서비스가 널리 사용되는 만큼. 네트워크 구성도 안시블이랑 테라폼 같은 자동화 도구와 같이 추상화가 많이 되는듯?
- 실제 회사들은 이런 식으로 하겠다는고 느낌.
- Ansible, Terraform 같은 구성 관리 도구를 "프로그래밍 전문가가 아니더라도 네트워크 자동화를 구현할 수 있는 도구" 라고 하는데, 개발자인 입장에서 개발 관련 포스트에서 구성 관리 도구를 소개할때는 "인프라 지식이 부족해도 인프라 구성을 할 수 있게 해주는 도구"여서 둘 다 전문 분야가 아닌 영역을 쉽게 다룰 수 있게 추상화 한다는 점은 동일하지만, 추상화하는 대상이 정반대인게 재미있음.

---

> Source: `section_39/ysj/note.md`

## Section 39 정리

근데 이걸 네트워크 강의에서 해야하나?

### 개요: AI와 ML 개념 및 네트워크 운영에서의 활용  

이 섹션에서는 인공지능(AI)과 머신러닝(ML)의 개념과 모델을 학습하며, 특히 네트워크 운영에서의 활용에 중점을 둡니다.  
- **AI와 ML 개요**:  
  - AI는 인간 지능을 모방하여 학습, 추론, 문제 해결 등을 수행합니다.  
  - ML은 AI의 하위 집합으로, 데이터를 분석해 패턴을 학습하고 경험을 통해 성능을 향상시킵니다.  
  - 주요 훈련 방식: 지도 학습, 비지도 학습, 반지도 학습, 강화 학습.  

- **생성형 및 예측형 AI**:  
  - **예측형 AI**는 과거 데이터를 기반으로 미래의 사건이나 문제를 예측합니다.  
  - **생성형 AI**는 데이터를 학습해 텍스트, 이미지 등 새로운 출력을 생성합니다.  

- **네트워크 운영에서의 활용**:  
  - **AI의 이점**:  
    - 패턴 학습을 통해 네트워크 이상 감지 및 자동 조치 수행.  
    - 과거 데이터를 기반으로 트래픽 혼잡, 하드웨어 고장 등 문제를 예측.  
    - 네트워크 설정 최적화 및 시뮬레이션 생성.  
  - **기존 도구 한계**:  
    - Ansible, Terraform 같은 자동화 도구는 고정적 작업에 적합하지만, 복잡한 이상 탐지나 동적 문제 해결에는 한계가 있음.  
  - **Cisco의 AI 적용**: 다양한 제품에 AI를 활용해 네트워크 효율성과 정확성 향상.  

- **생성형 AI의 주의점**:  
  - ChatGPT 같은 도구는 생성 속도가 빠르지만, 네트워크 데이터에 최적화되어 있지 않아 검증이 필수.  
  - RAG 기술을 통해 데이터의 정확성과 최신성을 개선 가능.  

### 키워드 위주로 AI 핵심 요약:

**1. 신경망 (Neural Networks):**
- **구조:** 입력층, 은닉층, 출력층으로 구성.
- **작동:** 각 노드는 입력을 가중치로 평가하여 활성화 여부 결정.
- **딥러닝:** 은닉층 2개 이상 포함, 이미지 분류 등 다양한 데이터 분석 가능.
- **훈련:** 역전파(backpropagation)를 통해 가중치 조정.

**2. 생성형 AI 모델 (Generative AI Models):**
- **주요 모델:**
  - **트랜스포머:** 텍스트 기반, 시퀀스 학습 및 생성에 특화.
  - **GAN:** 생성자(Generator)와 판별자(Discriminator)가 경쟁하여 고품질 데이터 생성.
  - **VAE:** 데이터 압축(인코더)과 복원(디코더)을 통해 중요한 특성만 유지.

**3. 트랜스포머와 LLM:**
- **트랜스포머:** 인코더와 디코더로 구성, 자연어 처리(NLP) 및 순차적 데이터 학습에 뛰어남.
- **LLM:** 방대한 데이터 기반 학습, GPT 모델로 대표됨, 텍스트 생성, 번역 등 활용.

**4. 환각 문제와 해결:**
- **문제:** LLM이 잘못된 정보(환각) 생성 가능.
- **해결:** 
  - 실시간 데이터 통합.
  - 특정 도메인 데이터로 추가 훈련.
  - 검색 증강 생성(RAG) 적용.

**5. 검색 증강 생성(RAG):**
- LLM에 외부 데이터베이스나 실시간 정보를 연결해 환각 문제 감소.

**6. 응용 분야:**
- 텍스트 생성, 이미지 생성, 네트워크 트래픽 시뮬레이션, 이상 감지, 다중 모달 모델 개발.

### AIOps(AI for IT Operations)

1. Cisco Catalyst Center (구 DNA Center)
- 네트워크 데이터 수집 및 분석
- AI 기반 네트워크 트래픽 기준 설정과 이상 감지
- 다른 네트워크와의 트래픽 벤치마크 비교

2. Cisco Meraki
- Wi-Fi 네트워크 시각화, 관리 및 보증
- Auto RF 기능으로 AP의 채널과 전력 수준 자동 최적화
- AI를 통한 무선 리소스 관리 최적화

3. Cisco Nexus Dashboard
- 데이터센터의 자동화된 프로비저닝과 모니터링
- NX-OS, Nexus, MDS 스위치 전용
- 패브릭 컨트롤러와 오케스트레이터 서비스 제공
- AI 기반 트래픽 분석과 이상 감지

4. Cisco AppDynamics
- 애플리케이션과 인프라 모니터링
- ML/AI를 통한 성능 기준선 설정
- 애플리케이션 성능 문제의 근본 원인 분석

5. Cisco ThousandEyes
- 클라우드와 인터넷 기반 네트워크 모니터링
- 내부/외부 네트워크 성능 모니터링
- ISP와 클라우드 제공업체 문제 식별
- 전 세계적 네트워크 측정 데이터 수집

6. Cisco Secure Network Analytics (구 StealthWatch)
- 네트워크 트래픽 분석과 보안 모니터링
- ML 기반 이상 징후와 위협 식별
- 자동 위협 대응 기능
- ISE와 통합하여 감염된 호스트 격리 가능

이러한 제품들은 대부분 머신러닝과 AI를 활용하여 트래픽 분석, 이상 감지, 근본 원인 분석 등의 기능을 제공합니다. 각 제품은 특정 사용 사례에 맞춰져 있으며, 온프레미스 또는 클라우드 기반으로 배포할 수 있습니다.
