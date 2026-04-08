
## 레이어드 프랙탈 아키텍처

OpenCSP는 공유 모듈이 각 레이어에 재귀적으로 주입되는 레이어드 프랙탈 구조를 채택합니다.

```mermaid
graph TD
    %% 외부 공유 모듈 (DNA)
    subgraph GitHub_Repo [GitHub: OpenCSP-Modules]
        M[[표준 공유 모듈]]
        style GitHub_Repo fill:#f9f9f9,stroke:#333,stroke-width:2px,stroke-dasharray: 5 5
    end

    subgraph Layer1 [Layer 1: 인프라]
        direction TB
        L1_Apply[Terraform Apply] --> L1_Nodes[물리/가상 노드]
        
        subgraph Layer2 [Layer 2: 플랫폼]
            direction TB
            L2_Boot[K3s 부트스트랩] --> L2_Cluster[K3s 클러스터]
            
            subgraph Layer3 [Layer 3: 데이터 & 서비스]
                direction TB
                L3_CR[사용자 커스텀 리소스] --> L3_Controller[Tofu-Controller / Semaphore]
                L3_Controller --> L3_App[동적 서비스 리소스]
            end
        end
    end

    %% 공유 모듈 호출 관계 (프랙탈 주입)
    M -.-> L1_Apply
    M -.-> L2_Boot
    M -.-> L3_Controller

    %% 스타일링
    style Layer1 fill:#e3f2fd,stroke:#1565c0,stroke-width:3px
    style Layer2 fill:#fff3e0,stroke:#ef6c00,stroke-width:3px
    style Layer3 fill:#f1f8e9,stroke:#2e7d32,stroke-width:3px
    style M fill:#ffffff,stroke:#2980b9,font-weight:bold,color:#2980b9
```
