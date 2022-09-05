---
date: 2022-09-06
category: algo
---

## two pointer 란?

- 두 곳의 인덱스를 옮기면서 순회하는 방식
- 배열의 부분합을 구하거나 두 배열의 합을 똑같이 만드는 큐 문제 에 사용 할 수 있다.
- 그 외 2 곳에 인덱스를 두고 계산한다는 생각을 응용하면 큐 스택 문제에 많이 사용 할 수 있어 보였다.

## original 공식

```
  //python
  n = 5 # 데이터의 개수 N
  m = 5 # 찾고자하는 부분합 M

  count = 0
  interval_sum = 0
  end = 0

  # start를 차례대로 증가시키며 반복
  for start in range(n):
      # end만큼 이동시키기
      while interval_sum < m and end < n:
          interval_sum += data[end]
          end += 1
      # 부분합이 m일 때 카운트 증가
      if interval_sum == m:
          count += 1
      interval_sum -= data[start]

  print(count)
```

## 스택 큐 문제에 응용

```
  function solution(progresses, speeds) {
    const restDate = progresses.map(getRestDate);

    let s = 0;
    let e = 1;

    const len = restDate.length;
    const answer = [];

    while (e < len) {
      if (restDate[s] < restDate[e]) {
        answer.push(e - s);
        s = e;
      }

      e++;
      if (e === len) answer.push(e - s);
    }
    return answer;

    function getRestDate(percent, i) {
      return Math.ceil((100 - percent) / speeds[i]);
    }
  }

```
