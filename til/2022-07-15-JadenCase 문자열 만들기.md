---
date: 2022-07-15
category: til,algo
---

## 문제

- JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다.
- 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다.
- 문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

## 풀이

- 문제대로 코드를 작성했는데 틀려서 의아했다 도대체 왜 틀렀을까?
- 그래서 문자 하나하나 반복문으로 순회하면서 작성하면서 작동을 살펴봤다.
- 정말 큰 문제는 내가 문제에 있는 조건 하나를 놓쳤다는 것이다.
- 바로 맨 앞에 문자 를 제외한 나머지는 소문자 라는 것! 당연히 소문자 일줄 알고 소분자로 변환을 안해서 틀린 것이었다.

```
  function isString(char) {
    if (!char.trim()) return false;
    return isNaN(Number(char));
  }

  function solution(s) {
    let answer = "";
    let nextUpper = "";
    for (let i = 0; i < s.length; i++) {
      //공백 다음 것이 문자 일때만 대문자로 바꾼다.
      const cur = s[i];

      if (!i && isString(cur)) {

        //lowerCase 를 추가해주었더니 정답으로 인정되었다.
        answer += cur.toUpperCase();
        continue;
      }

      if (nextUpper) {
        answer += nextUpper;
        nextUpper = "";
        continue;
      }

      answer += cur.toLowerCase();

      if (cur === " " && s[i + 1] && isString(s[i + 1])) {
        nextUpper = s[i + 1].toUpperCase();
      }
    }

    return answer;
  }
```

- 위에 불필요하게 모든 문자열을 반복 해 준 것을 간단하게 split 으로 작성하면서 1줄로 가능하다
- 이렇게 까지 압출 할 생각은 없었는데 다른사람 풀이가 전부 짧은 것을 보고 오기가 생겨서 작성해 봤다.
- 쉽게 작성이 되서 금방 풀 수 있었다.

```
  function solution(s) {
    return s
      .split(" ")
      .map((word) => word.charAt(0).toUpperCase() + word.slice(1).toLowerCase())
      .join(" ");
    }
```
