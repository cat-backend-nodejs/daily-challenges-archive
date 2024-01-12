# D- One Man Army

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/D)

## Tutorial

* The optimal weapon that Sherbiny should use will always be the median of the weapons of his opponents. The median is the value that is in the middle of the array after sorting it. If there are two values in the middle, you can take any of them getting the same result.

* You then loop through the values of the opponents weapons to sum up the absolute differences and store the sum in a variable. If you're using a staticly typed language, a 32-bit integet variable won't fit the value so make sure to user a 64-bit container like `long long` in C++.

## Solution

### C++
```c++
#include "bits/stdc++.h"
 
using namespace std;

int main() {
    int n; cin >> n;
    vector<long long> a(n);
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
    sort(a.begin(), a.end());
    long long weapon = a[n/2], result = 0;
    for (int i = 0; i < n; i++) {
        result += abs(a[i] - weapon);
    }
    cout << result;
}
```

### Python
```py
n = int(input())
a = list(map(int, input().split()))
a.sort()
r = a[n//2]
print(sum(abs(a[i]-r) for i in range(n)))
```