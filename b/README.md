# B- Save Mario!

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/B)

## Tutorial

The size of the segment that Mario can move to is `L - d`,
you can calculate the speed by which the length of this segment decreases as `v1 + v2`,
then the time left for Mario is the total length devided by the speed
the final formula is `(L - d) / (v1 + v2)`.

## Solution

### C++

```c++
int main() {
    int d, l, v1, v2; cin >> d >> l >> v1 >> v2;
    cout << fixed << setprecision(15) << (double)(l - d) / (v1 + v2);
}
```

### Python

```py
d, l, v1, v2 = map(int, input().split())
print((l-d)/(v1+v2))
```
