### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

```js
// 비교할 두 문자열을 받습니다.
function insensitiveEqual(str1, str2) {
  // 만약 두 문자열이 같다면 true를 반환합니다.
  if (str1 === str2) {
    return true;
  }
  // 같지 않다면 false를 반환합니다.
  return false;
}
```

### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백으로 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

반목문을 이용한 풀이

```js
// 문자열 s와 자연수 nd을 받습니다.
function leftPad(s, n) {
  var str = s;
  // n(자연수)가 s(문자열)의 길이보다 크다면
  for (var i = s.length; i < n; i++) {
    // 반복문이 s(문자열)의 길이 - n만큼 돌면서 문자열 왼쪽에 공백을 추가합니다.
    str = " " + str;
  }
  // 조건에 따라 추가됐거나 추가되지 않은 문자열을 반환합니다.
  return str;
}
```

`repeat` 메서드를 이용한 풀이

```js
// 문자열 s와 자연수 n을 받습니다.
function leftPad(s, n) {
  // 자연수 n이 문자열 s의 길이보다 크다면
  if (n > s.length) {
    // 큰 만큼 공백을 문자열 왼쪽에 추가해줍니다.
    return " ".repeat(n - s.length) + s;
  }
  // 자연수 n이 문자열 s의 길이보다 작다면 문자열 s를 그대로 반환합니다.
  return s;
}
```

### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.

if문 비교

```js
function countVowel(s) {
  // 초기값은 모음이 없다고 가정합니다.
  var count = 0;
  // 문자열을 갯수만큼 돌 수 있는 반복문을 만들고,
  for (var i = 0; i < s.length; i++) {
    // 해당 자리의 글자가 모음이면,
    if (
      s[i] === "a" ||
      s[i] === "e" ||
      s[i] === "i" ||
      s[i] === "o" ||
      s[i] === "u"
    ) {
      // 모음의 갯수를 하나 추가합니다.
      count += 1;
    }
  }
  // 집계된 모음의 갯수를 반환합니다.
  return count;
}
```

정규표현식

```js
function countVowel(s) {
  // 모음만 추출된 배열을 vowel 변수에 할당합니다.
  var vowel = s.match(/[aeiou]/g);
  // 추출된 배열이 없으면 (match 메서드는 정규표현식 규칙에 매칭돠는 문자가 없으면 null을 반환합니다.)
  if (vowel == null) {
    return 0;
  }
  // 모음만 들어있는 배열의 길이를 반환합니다.
  return vowel.length;
}
```
