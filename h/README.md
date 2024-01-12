# H- Love Story

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/H)

## Tutorial

- you can observe by trying the algorithm on different values of `n`
  that the value of `n` will quickly reach one of two ends $0$ or $6174$ then it will stay unchanged.
- so you can check if the new value of `n` equals the current value then break the loop and print n.

## Solution

### C++

```c++
typedef long long ll;
int main() {
    int t; cin >> t;
    while(t--) {
        int n;
        ll k;
        cin >> n >> k;
        while (k--) {
            string s = to_string(n);
            s += string(4 - s.length(), '0');

            sort(s.begin(), s.end());
            int a = stoi(s);
            int b = stoi(string(s.rbegin(), s.rend()));

            if(n == b - a)
                break;
            n = b - a;
        }
        cout << n << endl;
    }
}
```

### Python

```py
for t in range(int(input())):
    n, k = map(int, input().split())
    for _ in range(k):
        s = str(n)
        s += '0'*(4-len(s))
        s = list(s)
        s.sort()
        p = int(''.join(s))
        q = int(''.join(s[::-1]))
        if n == q-p: break
        n = q-p
        if n == 0: break
    print(n)
```
