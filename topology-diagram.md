# Topology Diagram

```mermaid
flowchart TD
    S1["spine1<br>AS 65000"]
    S2["spine2<br>AS 65000"]
    L1["leaf1<br>AS 65101<br>VNI 100"]
    L2["leaf2<br>AS 65102<br>VNI 100"]
    L3["leaf3<br>AS 65103<br>VNI 100"]
    H1["host1"]
    H2["host2"]
    H3["host3"]
    L1 --- S1
    L1 --- S2
    L2 --- S1
    L2 --- S2
    L3 --- S1
    L3 --- S2
    H1 --- L1
    H2 --- L2
    H3 --- L3
```
