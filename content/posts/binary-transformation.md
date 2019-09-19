---
title: "Binary Transformation"
date: 2019-09-15T21:31:10+01:00
author: "Dave"
cover: "/img/binary.webp"
draft: false
description: Notes on how to turn a base10 number into a binary, base2, one. Small python script to turn a randomly generated base10 number into binary. While procrastinating on the web...
---

While procrastinating on the web - I learnt some cool, yet probably useless, stuff: how to turn any base 10 number into a binary, base2, number. It's surprisingly easy.

Given any number x, one recursively divids x by 2 until one reaches 0. We deal only in integers. If division returns an even number the binary value is 0, if division returns an odd number the binary value is 1 (which is equal to the remainder of the division). The binary value is given by inverting the order of the results.

Python code:

```
import numpy.random as np


## Generate a random positive INT

x = np.randint(50000)
x_binary = []

## Use modular arithmetic to determine the presence of a remainder

while x > 0:
    if x%2 == 1:
        x_binary.insert(0, 1)
        x = int(x / 2)
    else:
        x_binary.insert(0, 0)
        x = x / 2

## Turn list into string before printing
        
print("".join(str(e) for e in x_binary))
```
Ex:

x = 15

x / 2 = 7 REMAINDER = 1

7 / 2 = 3 REMAINDER = 1

3 / 2 = 1 REMAINDER = 1

1 / 2 = 0 REMAINDER = 1

x<sub>base10</sub> = 1111<sub>base2</sub>

x = 321

x / 2 = 160 REMAINDER = 1

160 / 2 = 80 REMAINDER = 0

80 / 2 = 40 REMAINDER = 0

40 / 2 = 20 REMAINDER = 0

20 / 2 = 10 REMAINDER = 0

10 / 2 = 5 REMAINDER = 0

5 / 2 = 2 REMAINDER = 1

2 / 2 = 1 REMAINDER = 0

1 / 2 = 0 REMAINDER = 1

x<sub>base10</sub> = 0100 0001<sub>base2</sub>