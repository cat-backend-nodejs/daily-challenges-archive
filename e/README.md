# E- Too Many Messages

## Problem

[Statement](https://codeforces.com/group/BzMNcpUJn7/contest/496063/problem/E)

## Tutorial

- you need to mentain the current screen chats by using a data structure like deque. initialy it's empty
- then to solve the problem you can loop through the messages and for every message you do the following:
  - check if the `id` is present in the current screen chats, if it's present continue
    without changes.
  - otherwise, you will push the `id` to the top of the screen
  - then check the size of the screen if it's higher than `k` you pop the last chat
- print the final state of the screen

## Solution

### C++

```c++
#include "deque"

signed main() {
    int n, k; cin >> n >> k;
    deque<int> dq;

    while(n--) {
        int id; cin >> id;

        bool onScreen = false;
        for(int i : dq)
            if(i == id)
                onScreen = true;

        if(!onScreen)
            dq.push_back(id);

        if(dq.size() > k)
            dq.pop_front();
    }

    reverse(dq.begin(), dq.end());
    cout << dq.size() << endl;
    for(int i : dq)
        cout << i << ' ';
}
```

### Python

```py
from collections import deque

n, k = map(int, input().split())
a = list(map(int, input().split()))
screen = set()
q = deque()
for i in range(n):
    if a[i] not in screen:
        if len(q) == k:
            screen.remove(q.pop())
        screen.add(a[i])
        q.appendleft(a[i])
print(len(q))
print(*q)
```
