---
date: 2022-07-01
category: til, algo
---

## 문제

- n 이 주어졌을때 n 보다 크고 n의 이진수와 1의 숫자가 같은 가장 작은 자연수를 구해라
- 풀이
  - n 부터 1씩 더해서 제일 조건에 부합 할 경우 바로 결과를 반환하면 효율성도 정확도도 다 통과 할 수 있다.
  - while 약간 성능이 for 보다 안좋다는 말을 들어서 웬만하면 for 를 사용하는게 좋다고 생각한다.

```
  function getOneCount(n) {
      return n
        .toString()
        .split("")
        .reduce((acc, cur) => (cur === "1" ? acc + 1 : acc), 0);
    }

    function solution(n) {
      const oneCountN = getOneCount(n.toString(2));
      let answer;

      for (let i = n + 1; i < Infinity; i++) {
        if (getOneCount(i.toString(2)) === oneCountN) {
          answer = i;
          break;
        }
      }

      return answer;
    }
```
