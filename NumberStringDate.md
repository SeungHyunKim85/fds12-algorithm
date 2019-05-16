# 문제 1

양수를 입력받아 이 수를 반지름으로 하는 원의 넓이를 반환하는 함수를 작성하세요.

```js
circleArea(10); // 314.1592653589793
```

# 문제 2

두 정수 `min`, `max` 를 입력받아, `min` 이상 `max` 미만인 임의의 정수를 반환하는 함수를 작성하세요.

```js
minToMax(2, 8); // 2 ~ 7 중 랜덤의 수
```

# 문제 3

정수를 입력받아, 5 단위로 올림한 수를 반환하는 함수를 작성하세요.

예:

```js
ceilBy5(30); -> 30
ceilBy5(32); -> 35
ceilBy5(37); -> 40
```

# 문제 4

임의의 HTML 색상 코드를 반환하는 함수를 작성하세요.

```js
htmlHexCode(); // #92F01A
htmlHexCode(); // #00FF12
```

# 문제 5

rgb색상코드를 랜덤으로 반환하는 함수를 작성하세요.

```js
randomRgbCode(); // rgb(123, 44, 254);
randomRgbCode(); // rgb(12, 3, 223);
```

# 문제 6

소수인 숫자와, 자릿수를 받아서 소수를 자리수만큼만 자른 뒤 반환하는 함수를 작성하세요.

```js
fixFloat(10.12345, 2); // 10.12
fixFloat(15.5678, 1); // 15.6
```

# 문제 7

Camel case의 문자열을 입력받아, snake case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

```js
camelToSnake('helloWorld'); // 'hello_world'
```

# 문제 8

Snake case의 문자열을 입력받아, camel case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

```js
snakeToCamel('hello_world_javascript'); // 'helloWorldJavascript'
```

# 문제 9

2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각 SUN,MON,TUE,WED,THU,FRI,SAT

입니다. 예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 TUE를 반환하세요.

제한 조건

- 2016년은 윤년입니다.
- 2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)

> 출처: 프로그래머스 [2016년]

```js
getDay(5, 24); // 'TUE'
```

# 문제 10

전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 \*으로 가린 문자열을 리턴하는 함수를 `String.prototype.repeat`, `String.prototype.replace`, `String.prototype.substring`등의 String 관련 메소드를 활용해서 작성하세요.

제한 조건

- s는 길이 4 이상, 20이하인 문자열입니다.

> 출처: 프로그래머스 [핸드폰 번호 가리기]

```js
hidePhoneNumber('01033334444'); // '*******4444'
hidePhoneNumber('027778888'); // '*****8888'
```
