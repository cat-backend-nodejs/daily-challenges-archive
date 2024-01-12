# G- Mystery of Digitville

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/G)

## Tutorial

* The trivial solution is to iterate starting from the number till you reach a number in which all the digits are similar, but this solution won't work because the number may get too large and reaching the solution will take so long.
* An alternate solution is to deal with the number as a string, generate a new string of the same length in which the new string contains one repeated character. There are many approaches to acheive this:
    - You can try all characters between 0 and 9 and compare the resulted string with your own string until its greater than or equal it.
    - You can use the first digit in the current string, but that will fail if the number is `3367` because the result will be `4444` instead of `3333`, so you can compare your result with the number and if it's smaller, increase the repeated character by 1.
    - Assume the first digit is `t`. Loop through the string. If you meet a digit different from `t`, if it's bigger then you need to repeat `t+1`. Otherwise you can go along with repeating `t`.

## Solution

### C++
```c++
#include "bits/stdc++.h"
 
using namespace std;

int main() {
    string s; cin >> s;
    string res = string(s.size(), s.front());
    if(res >= s) cout << res;
    else cout << string(s.size(), s.front() + 1);
}
```

### Python
```py
s = input(); n = len(s)
c = s[0]
for i in range(n-1):
    if s[i] > s[i+1]:
        c = s[i]
        break
    if s[i] < s[i+1]:
        c = chr(ord(s[i]) + 1)
        break
print(c * n)
```