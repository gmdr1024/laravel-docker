# laravel-docker
Docker files for Laravel

# Architecture

```mermaid
flowchart LR

%%外部要素
OU1[Host OS]

%%グループとサービス
subgraph GS[Docker]
  subgraph GV["web (amazon linux 2023)"]
    NW1{{"Apache 2.4"}}
    CP1("PHP 8.3<br>Node.js 20")
  end
  subgraph GV2["db (oracle linux 9)"]
    DB1[("MySQL 8")]
  end
end

%%サービス同士の関係
OU1 --> NW1
NW1 --> CP1
CP1 --> DB1

linkStyle 0 stroke:#222
linkStyle 1 stroke:#222
linkStyle 2 stroke:#222

%%グループのスタイル
classDef SGS fill:#def,color:#07b,stroke:#07b
classDef SGV fill:#555,color:#fff,stroke:#555

class GS SGS
class GV SGV
class GV2 SGV

%%サービスのスタイル
classDef SOU fill:#aaa,color:#fff,stroke:#aaa
classDef SNW fill:#84d,color:#fff,stroke:#fff
classDef SCP fill:#e83,color:#fff,stroke:#fff
classDef SDB fill:#46d,color:#fff,stroke:#fff

class OU1 SOU
class NW1 SNW
class CP1 SCP
class DB1 SDB
```
