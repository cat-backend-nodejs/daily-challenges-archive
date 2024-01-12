# J- Arranged Marriage

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/J)

## Tutorial

- the only condition you need to check is count `a` equals the count of `b`
- if the condition is met then you can make sure that in each operation there are to two adjacent different characters

## Solution

### C++

```c++
int main() {
    int t; cin >> t;
    while(t--) {
        string s; cin >> s;

        int a = 0, b = 0;
        for(char c : s) {
            a += c == 'a';
            b += c == 'b';
        }

        cout << (a == b? "YES" : "NO") << endl;
    }
}
```

### Python

```py
for t in range(int(input())):
    s = input()
    print("YES" if not sum(1 if c == 'a' else -1 for c in s) else "NO")
```
