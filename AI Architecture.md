#Orchestration using pro code solution
[AI Agent Orchestration Patterns - Azure Architecture Center | Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/ai-agent-design-patterns)

![image.png](/.attachments/image-3d47636f-2e26-4085-9b6c-30a682fd73f6.png)

#Concurrent Pattern
:::mermaid
graph TD
    A[Input] --> HA["Hiring Agent (Orchestrator)"]
        HA --> IA[Interview Agent]
        HA --> EHA[Employee Handbook Agent]
        HA --> WHA[Work History Agent]
        HA --> BA[Benefits Agent]
        HA --> SA[Sentiments Agent]

        IA --> EMAIL["📨 Send Interview Questions via Email"]
        
        IA --> HA
        EHA --> HA
        WHA --> HA
        BA --> HA
        SA --> HA

        HA --> DEC["Aggregate results to output hiring Decision"]
        DEC --> END[Output]

        subgraph Concurrent Tasks
            IA
            EHA
            WHA
            BA
            SA
        end
        style HA fill:#4A90E2,stroke:#2E5C8A,stroke-width:3px,color:#fff
        style DEC fill:#FFB84D,stroke:#CC8A3D,stroke-width:3px,color:#fff
        style EMAIL fill:#98D8C8,stroke:#50C878,stroke-width:2px
        
        style IA fill:#E8F4F8,stroke:#4A90E2,stroke-width:2px
        style EHA fill:#E8F4F8,stroke:#4A90E2,stroke-width:2px
        style WHA fill:#E8F4F8,stroke:#4A90E2,stroke-width:2px
    style BA fill:#E8F4F8,stroke:#4A90E2,stroke-width:2px
    style SA fill:#E8F4F8,stroke:#4A90E2,stroke-width:2px

linkStyle 7,8,9,10 stroke:#50C878,stroke-width:2px
