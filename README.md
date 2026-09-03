IoT-Fender

> IoT 환경을 위한 실시간 패킷 수집 및 Flooding 공격 탐지/차단 시스템 (IDS)

`IoT-Fender`는 라즈베리파이 게이트웨이 환경에서 네트워크 트래픽을 실시간으로 수집·파싱하고, ICMP / TCP SYN Flooding 공격을 감지하여 자동 차단 및 대시보드로 시각화하는 모듈형 IDS 시스템입니다.

---

# 시스템 아키텍처 및 모듈 구조

본 프로젝트는 소프트웨어 공학의 모듈화 원칙에 따라 크게 2개의 핵심 모듈로 구성되며, 모듈 간 데이터는 약속된 JSON 규격으로 통신합니다.

1. `capture` (패킷 수집 & 파싱 모듈)
   - 네트워크 인터페이스에서 Raw 패킷 수집
   - IP 및 TCP/ICMP 헤더 분석 (출발지/목적지 IP, 포트, SYN 플래그 등 추출)
   - 파싱된 정제 데이터를 탐지 모듈로 전달 (JSON 포맷)

2. `detection` (Flooding 탐지/차단 & 대시보드 UI 모듈)
   - 전달받은 패킷 데이터를 바탕으로 단위 시간당 임계치(Threshold) 분석
   - ICMP / TCP SYN Flooding 공격 감지 시 `iptables`를 통한 공격 IP 자동 차단
   - Streamlit 기반 실시간 트래픽 및 공격 대응 현황 시각화

---

# 기술 스택 (Tech Stack)

- Language: Python 3.10+
- Network / Packet Parsing: NONE
- Mitigation: Linux `iptables`
- Dashboard: Streamlit
- Testing Tools: `hping3`, Wireshark

---

# 시작하기 (Getting Started)

1. 저장소 클론 (Repository Clone)
```bash
git clone [https://github.com/your-org/IoT-Fender.git](https://github.com/your-org/IoT-Fender.git)
cd IoT-Fender
