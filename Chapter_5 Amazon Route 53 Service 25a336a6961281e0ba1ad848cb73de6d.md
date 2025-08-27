# Chapter_5 Amazon Route 53 Service

- DNS(DomainNameSystem)란?
    - 복잡한 주소 체계를 문자형태의 도메인 네임으로 매핑하여 연결
    - DNS서비스는 통신이 어찌
    - 사용자가웹서버를 ip주소 등록과 도메인구매
    - 사용자는 DNS서버 질의 응답 도메인질의 응답 어떤 퍼블릭인지 알게되었고
- 도메인구조 및 DNS 서버 종류
    
    ![IMG 6.JPEG](Chapter_5%20Amazon%20Route%2053%20Service%2025a336a6961281e0ba1ad848cb73de6d/IMG_6.jpeg)
    
    **1. 도메인 구조 (Domain Structure)**
    
    - **blog:** 서브도메인 (Sub Domain)
    - **cloudneta:** 2단계 도메인 (Second Level Domain, SLD)
    - **net:** 최상위 도메인 (Top Level Domain, TLD)
    - **. (맨 끝의 점):** 루트 도메인 (Root Domain)
    
    **2. DNS 서버 종류 및 동작 방식**
    
    1. **DNS 해석기 (DNS Resolver):** 사용자의 요청을 받아 IP 주소를 찾는 과정을 시작
    2. **루트 네임 서버 (Root Name Servers):** DNS 해석기는 먼저 루트 네임 서버에 .net 도메인을 관리하는 서버의 주소를 물어봄
    3. **TLD 네임 서버 (TLD Name Servers):** 루트 서버로부터 받은 정보로 .net을 관리하는 TLD 네임 서버에 접속하여 cloudneta.net을 관리하는 서버의 주소를 물어봄
    4. **SLD 네임 서버 (SLD Name Servers):** TLD 서버로부터 받은 정보로 cloudneta.net을 관리하는 SLD 네임 서버에 접속 이 서버는 해당 도메인에 대한 최종 정보를 가지고 있어 **권한이 있는 네임 서버 (Authoritative Name Server)** 라고도 불림
- DNS 레코드 유형
    - 도메인에 대한 요청의 처리 방법에 대한 정보로 다양한 DNS레코드 유형이 존재
    - A : 도메인을 IPv4 주소로 매핑
    - AAAA : 도메인을 IPv6주소로 매핑
    - NS : 도메인네임 서버를 식별
    - CNAME : 도메인의 별칭을 정의
- AmazonRoute 53 서비스란?
    - AWS에서 제공 하는 완전 관리형 DNS 서비스
    - 
- AmazonRoute 53 - 라우팅 정책
    - **주요 기능 및 설정 절차**
        - **도메인 네임 등록:** 등록대행소를 통해 도메인을 등록.
        - **호스팅 영역 생성:** 도메인의 DNS 레코드를 관리하는 컨테이너.
            - **퍼블릭 호스팅 영역:** 인터넷에서 확인 가능한 DNS 레코드 관리.
            - **프라이빗 호스팅 영역:** VPC 내부에서만 확인 가능한 DNS 레코드 관리.
        - **레코드 작성:** 호스팅 영역 내에 CNAME, A, NS 등 다양한 유형의 DNS 레코드를 생성하여 라우팅 정책을 설정.
    - **라우팅 정책 종류**
        - DNS 요청에 대한 응답 방식을 정의하는 규칙.
        - **단순 라우팅 (Simple Routing):** 도메인에 하나의 리소스나, 여러 리소스를 랜덤하게 연결.
        - **가중치 기반 라우팅 (Weighted Routing):** 설정한 가중치(비율)에 따라 여러 리소스로 트래픽을 분산.
        - **장애 조치 라우팅 (Failover Routing):** 액티브-패시브 구성으로, 주 리소스의 상태를 확인하여 장애 발생 시 예비 리소스로 자동 전환.
        - **지연 시간 기반 라우팅 (Latency Routing):** 사용자에게 가장 낮은 지연 시간을 제공하는 리소스로 라우팅.
        - **지리 위치 라우팅 (Geolocation Routing):** 사용자의 지리적 위치를 기반 트래픽을 라우팅.
        - **지리 근접 라우팅 (Geoproximity Routing):** 리소스의 지리적 위치를 기반으로 트래픽을 라우팅(트래픽 편중 가능).
        - **다중값 응답 라우팅 (Multi-Value Answer Routing):** 여러 정상적인 리소스 IP 주소를 반환.

---