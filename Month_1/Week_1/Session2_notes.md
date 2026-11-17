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
A --> D[loop flow]
B --> E[start]
E --> |condition true| F[yes]
F --> G [Execute code]
E --> |condition false| H[no]
H --> I[Skip]
C --> J[Start]
J --> K {Condition true?}
K --> |yes| L[Execute Block A]
K --> |no| M[Execute Block B]
D --> N[start]
N --> O{Condition true?}
O --> |yes| P[Execute loop body]
p --> Q[check condition again]
O --> |no| R[stop]
```
