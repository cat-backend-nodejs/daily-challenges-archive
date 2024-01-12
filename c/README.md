# C- Sir Eyad

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/C)

## Tutorial

- firstly, count all players having skill level higher than `k`, becuase every one of them can form a team by himself.
- then, it's optimal to form the remaining teams on this way:
  - form a team with the highest skill player `a` with the lowest skill `b` such that `a + b >= k` holds.
  - repeat the process untill you can't form more teams.
- you can solve the problem using two pointers algorithm after sorting the array.

## Solution

### C++

```c++
int main() {
    int t; cin >> t;
    while(t--) {
        int n, k; cin >> n >> k;
        vector<int> v(n);
        for(int &i : v) cin >> i;
        sort(v.begin(), v.end());

        int l = 0, r = n - 1, res = 0;
        while(l <= r) {
            if(v[r] >= k)  // player r by himself
                r--, res++;

            else if(r != l && v[r] + v[l] >= k) // player r with player l
                r--, l++, res++;

            else // v[l] + v[r] < k
                l++;
        }

        cout << res << endl;
    }
}
```

### Python

```py
for t in range(int(input())):
    n, k = map(int, input().split())
    a = list(map(int, input().split()))
    a.sort(reverse=True)

    c = 0
    i = 0
    j = n-1
    while i < n and a[i] >= k:
        c += 1
        i += 1
    while i < j:
        if a[i] + a[j] >= k:
            c += 1
            i += 1
            j -= 1
        else:
            j -= 1

    print(c)
```
