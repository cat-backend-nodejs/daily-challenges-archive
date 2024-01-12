# F- Crazy Billiard

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/F)

## Tutorial

- you can quickly calculate waleed's score `Ws` as $2 ^ {(log2(n) + 1)} - 1$ ([for more details](https://jarednielsen.com/sum-consecutive-powers-2/))

  or using a loop to sum `i` and each iteration multiply `i` by `2`

- you can quickly calculate samer's score `Ps` mathematically using the formula $n * (n + 1) \over 2$ ([for more details](https://www.cuemath.com/sum-of-natural-numbers-formula/)) then substract `Ws` from it
- the final result is `Ps - Ws`

## Solution

### C++

```c++
typedef long long ll;
int main() {
    int t; cin >> t;
    while(t--) {
        ll n; cin >> n;
        ll ws = 0;
        for(int i = 1; i <= n; i *= 2)
            ws += i;

        ll ps = n * (n + 1) / 2;
        ps -= ws;

        cout << ps - ws << endl;
    }
}
```

### Python

```py
from math import log2
for t in range(int(input())):
    n = int(input())
    x = int(log2(n))
    print(n*(n+1)//2 - 2*(2**(x+1)-1))
```
