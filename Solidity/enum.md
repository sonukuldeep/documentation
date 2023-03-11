---
layout: home
title: Enums
parent: Solidity
---
## Enums
Enums restrict a variable to have one of only a few predefined values. The values in this enumerated list are called enums.

### Example:
```c++
enum FreshJuiceSize { SMALL, MEDIUM, LARGE }
FreshJuiceSize choice;
FreshJuiceSize constant defaultChoice = FreshJuiceSize.MEDIUM;
```
