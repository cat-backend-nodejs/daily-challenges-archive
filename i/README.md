# I- Social Distancing

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/I)

## Tutorial

* You can simply create a 2D array with the given size $26 × 26$ and initialize it with zeroes, then for each present student change its value in the grid to 1.
* Then you can loop through the grid, if the current grid element `grid[i][j]` is equal to 1 and surrounded by ones in the four directions `grid[i+1][j]`, `grid[i-1][j]`, `grid[i][j+1]`, `grid[i+1][j-1]` then the student is surrounded and you can add 1 to the result.
* Make sure to skip the corners of the grid _(at $i=0, 25$ or $j=0, 25$)_

## Solution

### C++
```c++
#include "bits/stdc++.h"
 
using namespace std;

int main() {
    vector<vector<bool>> s(26, vector<bool>(26));
 
    int n; cin >> n;
    while(n--) {
        int x, y; cin >> x >> y;
        s[x][y] = 1;
    }

    int cnt = 0;
    for(int i = 1; i < 25; ++i)
        for(int j = 1; j < 25; ++j)
            if(s[i][j] && s[i+1][j] && s[i-1][j] && s[i][j+1] && s[i][j-1])
                cnt++;

    cout << cnt;
}
```

### Python
```py
n = int(input())
a = []
g = [[False]*28 for i in range(28)]
for i in range(n):
    x, y = map(int, input().split())
    x += 1; y += 1
    a.append((x, y))
    g[x][y] = True
ans = 0
for x, y in a:
    s = 0
    for dx,dy in [(0,1),(0,-1),(1,0),(-1,0)]:
        s += int(g[x+dx][y+dy])
    ans += s//4
print(ans)
```