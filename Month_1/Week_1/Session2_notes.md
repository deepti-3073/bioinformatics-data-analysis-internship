# Module 1: R Programming

## Session 2: Control flow and logical structures

## 1. Objectives
- understand conditional statements 
- apply logical operators 
- implement loops 
- translate biological problems into structured logic

## 2. Control flow 
- determines how R makes decisions and repeats actions 

```mermaid
flowchart TD
    A([Control Flow]) --> B[Conditional flow - if]
    A --> C[if-Else flow]
    A --> D[Loop flow]

    B --> E[Start]
    E --> |Condition true| F[Yes]
    F --> G[Execute code]
    E --> |Condition false| H[No]
    H --> I[Skip code]

    C --> J[Start]
    J --> K{Condition true?}
    K --> |Yes| L[Execute Block A]
    K --> |No| M[Execute Block B]

    D --> N[Start]
    N --> O{Condition true?}
    O --> |Yes| P[Execute loop body]
    P --> O
    O --> |No| R[Stop]
```