---
title: "stack, queue, deque"
date: 2024-03-15 01:00:00 +09:00
categories: [algorithm, review]
tags:
  [
    stack,
    queue,
    deque.
    .
    .
  ]
---

#stack

스택을 쌓으며 가장 나중에 입장한 요소가 가장 먼저 pop

```Python
stack = []

stack.append(1)
stack.append(2)
stack.append(3)
stack.append(4)
stack.pop()
stack.append(5)
stack.append(6)
stack.pop()

print(stack)
print(stack[::-1])
stack.reverse()
print(stack)
```

result

```Python
[1, 2, 3, 5]
[5, 3, 2, 1]
[5, 3, 2, 1]
```

#queue, deque

first in first out

```Python
from collections import deque

queue = deque() # 큐.스택 구현 라이브러리(시간복잡도 효율적)

queue.append(1)
queue.append(2)
queue.append(3)
queue.popleft()
queue.append(4)
queue.append(5)
queue.popleft()
queue.append(6)

print(queue)
queue.reverse()
print(queue)
```
result
```Python
deque([3, 4, 5, 6])
deque([6, 5, 4, 3])
```

# deque

효율적인 큐, 스택 라이브러리

```text
deque.append(item): item을 데크의 오른쪽 끝에 삽입한다.
deque.appendleft(item): item을 데크의 왼쪽 끝에 삽입한다.
deque.pop(): 데크의 오른쪽 끝 엘리먼트를 가져오는 동시에 데크에서 삭제한다.
deque.popleft(): 데크의 왼쪽 끝 엘리먼트를 가져오는 동시에 데크에서 삭제한다.
deque.extend(array): 주어진 배열(array)을 순환하면서 데크의 오른쪽에 추가한다.
deque.extendleft(array): 주어진 배열(array)을 순환하면서 데크의 왼쪽에 추가한다.
deque.remove(item): item을 데크에서 찾아 삭제한다.
deque.rotate(num): 데크를 num만큼 회전한다(양수면 오른쪽, 음수면 왼쪽).
```

