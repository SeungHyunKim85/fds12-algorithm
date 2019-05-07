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
    str = ' ' + str;
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
    return ' '.repeat(n - s.length) + s;
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
      s[i] === 'a' ||
      s[i] === 'e' ||
      s[i] === 'i' ||
      s[i] === 'o' ||
      s[i] === 'u'
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

### 문제4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

```js
function countChar(input) {
  // 결과를 담을 빈배열을 obj 변수에 할당합니다.
  const obj = {};
  // 글자를 하나씩 순회합니다.
  for (let i = 0; i < input.length; i++) {
    const char = input[i];
    // 객체 안에 해당 글자를 키로 가지는 속성이 있다면
    if (char in obj) {
      // 숫자를 하나 올립니다.
      obj[char]++;
    } else {
      // 객체 안에 해당 글자를 키로 가지는 속성이 없다면 1개가 있다고 초기화해줍니다.
      obj[char] = 1;
    }
  }
  // 글자의 갯수가 담긴 객체를 반환합니다.
  return obj;
}
```

### 문제5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)

split 메소드

```js
function isPalindrome(input) {
  // 글자의 길이를 저장합니다.
  var num = input.length;
  // 글자의 절반까지 순회합니다.
  for (i = 0; i <= num / 2 - 1; i++) {
    // 왼쪽에서 i번째, 오른쪽에서 i번째의 글자가 한번이라도 같지 않으면
    if (input[i] !== input[num - i - 1]) {
      // false를 반환합니다.
      return false;
    }
  }
  // 무사히 모든 글자가 같음을 확인했다면 true를 반환합니다.
  return true;
}

isPalindrome('토마토바토'); // false;
isPalindrome('토마토마토'); // true;
```

### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

```js
function subString(str) {
  // arr 변수를 선언하고, 결과를 담아 반환할 배열을 할당합니다.
  var arr = [];
  // 시작점으로 정할 인덱스를 정할 반복문입니다.
  for (let i = 0; i < str.length; i++) {
    // 끝점으로 정할 인덱스를 정할 반복문입니다.
    for (let j = i; j < str.length; j++) {
      // 배열에 정해진 시작점 인덱스, 끝점 인덱스까지 문자열을 잘라서 arr에 push 한다.
      arr.push(str.slice(i, j + 1));
    }
  }
  // 모든 요소가 담긴 배열을 반환한다.
  return arr;
}

console.log(subString('토마토')); // [ '토', '토마', '토마토', '마', '마토', '토' ]
console.log(subString('실')); // [ '실' ]
```

### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:

```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```

```js
function removeDuplicates(str) {
  // 결과값이 될 word 변수에 빈 문자열을 할당합나다.
  var word = '';
  // 단어의 모든 글자를 순회하여
  for (i = 0; i < str.length; i++) {
    // 글자를 담은 word 문자열에 이번 차례의 글자가 담겨있지 않다면 글자를 추가합니다.
    if (!word.includes(str[i])) {
      word += str[i];
    }
  }
  // 중복을 허용하지 않는 글자들을 담은 문자열을 반환합니다.
  return word;
}

console.log(removeDuplicates('tomato')); // 'toma'
console.log(removeDuplicates('sentence')); // 'sentc'
```

### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

- 루프로 먼저 풀어보세요.
- `split` 메소드를 이용해서 풀어보세요.

```js
function emailIdToStar(input) {
  // '@'을 봤을 때 true로 바뀌는 boolean 자료형 변수를 선언하고 아직 '@'을 보지 못했으므오 false로 할당합니다.
  let seen = false;
  // 별표 처리가 된 문자열을 담을 memory 변수를 선언합니다.
  let memory = '';
  // 글자를 하나씩 순회합니다.
  for (i = 0; i < input.length; i++) {
    // 만약 '@'을 만난다면 seen 변수에 true를 할당합니다.
    if (input[i] === '@') {
      seen = true;
    }
    // 만약 @을 본 후라면 글자를 담습니다.
    if (seen === true) {
      memory += input[i];
      // 만약 @을 보지 않은 상태라면 '*'를 담습니다.
    } else {
      memory += '*';
    }
  }
  // 완성된 변수를 반환합니다.
  return memory;
}
emailIdToStar('jhd1925@gamil.com');
```

split 메소드

```js
function emailIdToStar(input) {
  // '@'문자를 기준으로 나뉜 문자열을 담은 배열을 email 변수에 할당합니다.
  // ['jhd1925', 'gmail.com']
  var email = input.split('@');
  // 앞의 id 부분만 id 갯수만큼의 '*'을 만들어 id가 있던 자리에 할당합니다.
  email[0] = '*'.repeat(email[0].length);
  // '*'로 바뀐 문자와 @과 뒤의 email 도메인 주소를 합친 문자열을 반환합니다.
  return email[0] + '@' + email[1];
}

emailIdToStar('jhd1925@gamil.com');
```

### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.

```js
function swapCase(input) {
  var result = '';
  var arr = input.split('');
  for (var item of arr) {
    item === item.toUpperCase()
      ? (result += item.toLowerCase())
      : (result += item.toUpperCase());
  }
  return result;
}

swapCase('JavaScirpt'); // 'jAVAsCIRPT'
```

```js
function swapCase(input) {
  var arr = input.split('');
  var newArr = arr.map(item =>
    item === item.toUpperCase() ? item.toLowerCase() : item.toUpperCase()
  );
  return newArr.join('');
}

swapCase('JavaScirpt'); // 'jAVAsCIRPT'
```

### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

```js
function firstLetterToUpperCace(input) {
  // 결과를 입력받을 빈 str변수를 만듭니다.
  let result = '';
  // 공백을 봤을 때 true로 바뀌고, 공백을 제외한 문자열일 때 false가 되는 seen 변수를 선언하고,
  // 첫 글자는 대문자가 되어야 하므로 true를 할당합니다.
  let seen = true;
  // 문자를 순회합니다.
  for (i = 0; i < input.length; i++) {
    // 만약 seen이 true이면서 글자가 공백문자가 아니면
    // 글자를 대문자로 바꾼 뒤 저장하고 seen에 false를 할당합니다.
    if (seen === true && input[i] !== ' ') {
      result += input[i].toUpperCase();
      seen = false;
      // 글자가 단순히 공백이라면 seen을 true로 바꾸고 글자를 저장합니다.
    } else if (input[i] === ' ') {
      result += input[i];
      seen = true;
      // 글자가 공백도 아니고 seen도 false라면 일반 글자이므로 글자를 글자 그대로 저장합니다.
    } else {
      result += input[i];
    }
  }
  // 담긴 문자열을 반환합니다.
  return result;
}

firstLetterToUpperCace('i am hungry'); // 'I Am Hungry'
```

```js
function firstLetterToUpperCace(input) {
  var result = input.split(' ');
  for (var i = 0; i < result.length; i++) {
    result[i] = result[i].replace(/\w/, a => a.toUpperCase());
  }
  return result.join(' ');
}

firstLetterToUpperCace('i  am hungry'); // 'I Am Hungry'
```
