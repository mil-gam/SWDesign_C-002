```mermaid
graph LR
    subgraph "항공예약시스템"
        %% Use Cases
        UC1(고객 등록)
        UC2(고객 조회)
        UC3(고객 인증)
        UC4(마일리지 조회)
        
        UC5(항공권 등록)
        UC6(항공권 조회)
        UC7(항공권 가격 조회)
        
        UC8(항공권 예약)
        UC9(예약 조회)
        UC10(구매 수행)

        %% Relationships: 예약 (include)
        UC8 -.->|include| UC3
        UC8 -.->|include| UC6
        
        %% Relationships: 구매 (include)
        UC10 -.->|include| UC3
        UC10 -.->|include| UC9
        UC10 -.->|include| UC4
    end

    %% Actors
    Customer((고객))
    Admin((관리자))

    %% Actor Connections
    Customer --> UC1
    Customer --> UC3
    Customer --> UC4
    Customer --> UC6
    Customer --> UC7
    Customer --> UC8
    Customer --> UC9
    Customer --> UC10

    Admin --> UC2
    Admin --> UC5