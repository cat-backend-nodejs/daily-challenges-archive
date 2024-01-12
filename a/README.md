# A- Happy New Year

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/A)

## Tutorial

* A simple way to think of this problem is that we need to store the digits inside the string `s` in a new string, then we can cast this string into an integer and compare it with the given price `x`.

* Another way is to initialize the price with 0, then loop through the string `s`, every time you meet a digit you shift the number by multiplying it by 10 then add the digit. [`price = price*10 + (s[i] - '0')`]

## Solution

### C++
```c++
#include "bits/stdc++.h"
 
using namespace std;

int main() {
    int n, x; cin >> n >> x;
    string s; cin >> s;
 
    int price = 0;
    for(char c : s) {
        if(price > x) break;
        int y = c - '0';
        if(y >= 0 && y <= 9)
            price = price * 10 + y;
    }
 
    if(price <= x)
        cout << "Horray";
    else
        cout << "Maybe next year";
    return 0;
}
```

### Python
```py
n, x = map(int, input().split())
s = input()
price = int("".join(c for c in s if c.isdigit()))
print("Horray" if price <= x else "Maybe next year")
```