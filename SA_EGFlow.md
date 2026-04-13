flowchart TB
    subgraph Data[“数据输入 Data Input”]
        D1[“台风气象数据<br>（路径、风速、降雨）”]
        D2[“电力系统数据<br>（SCADA、PMU、故障）”]
        D3[“社会影响数据<br>（人口、交通、应急资源）”]
    end

    subgraph EG[“事理图谱 Event Evolutionary Graph”]
        direction TB
        E1[“具体事件图谱<br>（1,382节点+388边）”]
        E2[“抽象事件图谱<br>（8类 + p值）”]
        E3[“因果链 & 时序链”]
        E1 --> E2 --> E3
    end

    subgraph SA[“态势感知 Situational Awareness”]
        direction LR
        S1[“觉察 Perception<br>（事件检测）”]
        S2[“理解 Comprehension<br>（影响评估）”]
        S3[“预测 Projection<br>（短时趋势）”]
        S1 --> S2 --> S3
    end

    subgraph Fusion[“融合推演 Fusion”]
        F1[“语义匹配<br>实时事件→抽象事件”]
        F2[“风险概率计算<br>（历史p值）”]
        F3[“演化路径推演<br>（关键节点、扩散）”]
        F1 --> F2 --> F3
    end

    subgraph Decision[“主动防御决策”]
        Dec1[“抢修优先级”]
        Dec2[“动态负荷调控”]
        Dec3[“跨区域支援”]
    end

    Data --> EG
    Data --> SA

    EG -- “历史规律支撑” --> SA

    SA -- “实时状态 & 预测” --> Fusion
    EG -- “历史模式 & 概率” --> Fusion

    Fusion --> Decision

    style Data fill:#f0f4c3,stroke:#827717,stroke-width:2px
    style EG fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    style SA fill:#fff3e0,stroke:#e65100,stroke-width:2px
    style Fusion fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    style Decision fill:#e8f5e9,stroke:#1b5e20,stroke-width:2px
