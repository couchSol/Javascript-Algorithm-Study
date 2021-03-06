## 섹션4 : 문제 해결 접근법
- 알고리즘이란 무엇인가
- 알고리즘을 해결할 계획
- 비교 및 대조를 비롯한 빈도카운터, 투 포인터, 분할정복 등을 수립

---

### 알고리즘
: 특정 작업을 달성하기 위한 과정이나 일련의 단계

### How Do You Imporve?
1. 문제 해결을 위한 계획 수립
2. 일반적인 문제 해결 패턴 파악 (섹션 4)

### 문제 해결 단계
- 문제 이해
- 구체적 예시
- 문제 세분화
- 문제 해결 및 단순화
- 문제 복습 및 재구성

---

### 문제 이해
1. 문제를 나만의 방식으로 다시 생각할 수 있는가?
2. 문제가 어떤 입력값을 담고있는가?
3. 문제 해결책에서 나와야하는 출력값은 무엇인가?
4. 입력값이 출력값을 결정할 수 있는가?
다른말로, 문제를 해결할 충분한 정보가 주어졌는가?
5. 문제의 일부인 데이터의 중요한 부분에 어떻게 라벨을 지정할 수 있는가?

**예시 )** 두 숫자를 가지고 합계를 반환하는 함수를 작성하세요.
1. 문제를 나만의 방식으로 다시 생각할 수 있는가?
```
덧셈을 수행하는 함수를 작성하자
```
2. 문제가 어떤 입력값을 담고있는가?
```
숫자가 정수? 부동 소수점? 아주 큰 숫자라면?
```
3. 문제 해결책에서 나와야하는 출력값은 무엇인가?
```
때에 따라 정수? 부동 소수점? 큰 숫자라면 문자열 반환?
```
4. 입력값이 출력값을 결정할 수 있는가?
다른말로, 문제를 해결할 충분한 정보가 주어졌는가?
```
숫자 하나만 입력된다면? 0을 더해야할까? undefined ? null?
```
5. 문제의 일부인 데이터의 중요한 부분에 어떻게 라벨을 지정할 수 있는가?
```
무엇이 중요한지 생각
입력값: 함수, 인자 / 출력값: 반환결과
```
---

### 구체적 예시
1. 간단한 예시로 시작
2. 쉬운예제에서 복잡한 예시로 진행
3. 빈 입력값을 포함한 예시 살펴보기
4. 유효하지 않은 입력값 예시 살펴보기

**예시 )** 문자열을 취하고 각 문자의 수를 반환하는 함수를 작성하세요.
1. 간단한 예시로 시작
```js
charCount("aaaa"); // {a:4}
charCount("hello"); // {h:1, e:1, l:2, o:1}
```
2. 쉬운예제에서 복잡한 예시로 진행
```js
charCount("my phone number is 182763")
charCount("Hell hi")
=> 공백? 숫자? 대소문자 구분?
```
3. 빈 입력값을 포함한 예시 살펴보기
```js
charCount("");
=> null? false? undefined?
```
4. 유효하지 않은 입력값 예시 살펴보기
```js
charCount(숫자? 객체? null?);
=> ??
```
---

### 문제 세분화
: 밟아야 할 단계를 명확하게 작성

**예시 )** 문자열을 취하고 각 문자의 수를 반환하는 함수를 작성하세요.
```js
function charCount(str){
    // 마지막에 반환할 빈 객체 만들기
    // 문자열에 루프를 적용, 각 문자에 대해(for Each)..
        // 만약 문자가 숫자/문자이고, 키로써 객체에 있다면 해당 문자에 1을 더하고
        // 만약 문자가 숫자/문자이고, 객체에 없다면 문자를 추가하고 값을 1로 설정
        // 만약 문자가 그 외의 값(공백, 마침표 등)이면 아무것도 하지 않는다.
    // 마지막에 객체 반환
}
```

---

### 단순화
1. 수행하려는 작업에서 어려움을 느낀다면
2. 그 부분은 잠시 무시하고
3. 단순한 해결책을 먼저 작성한다음
4. 다시 어려운 부분을 통합시킨다.

**예시 **)** 문자열을 취하고 각 문자의 수를 반환하는 함수를 작성하세요.
```js
// 예시함수
function charCount("Your PIN number is 1234!"){
    ...
}
// {1:1, 2:1, 3:1, 4:1, b:1, e:1, i:2, m:1, n:2, o:1, p:1, r:2, s:1, u:1, y:1}
=> 문자 다섯개 정도는 하드코딩을 하여 패턴을 파악
```

```js
function charCount(str){
    // 마지막에 반환할 빈 객체 만들기
    var result = {};
    // 문자열에 루프를 적용, 각 문자에 대해(for Each)..
    for (var i=0; i<str.length; i++){
        var char = str[i].toLowerCase();
        // 만약 문자가 숫자/문자이고, 키로써 객체에 있다면 해당 문자에 1을 더하고
        if(result[char] > 0){
            result[char]++;
        }
        // 만약 문자가 숫자/문자이고, 객체에 없다면 문자를 추가하고 값을 1로 설정
        else{
            result[char] = 1;
        }
    }
        // 만약 문자가 그 외의 값(공백, 마침표 등)이면 아무것도 하지 않는다.
    // 마지막에 객체 반환
    return result;
}
```

---

### 리팩토링 셀프 질문
- 결과를 확인할 수 있는가?
- 결과를 다른 방식으로 도출할 수 있는가?
- 한눈에 보고 이해할 수 있는가?
- 결과나 방법을 다른문제에도 적용할 수 있는가?
- 해결책의 성능을 향상시킬 수 있는가?
- 코드를 향상시킬 수 있는 다른 방법을 떠올릴 수 있는가?
- 다른 사람들은 이 문제를 어떻게 해결했는가?

**예시 )** 문자열을 취하고 각 문자의 수를 반환하는 함수를 작성하세요.
```js
// 기존코드
function charCount(str){
    var obj = {};
    for (var i=0; i<str.length; i++){
        var char = str[i].toLowerCase();
        if(/[a-z0-9]/.test(char)){
            if(obj[char] > 0){
                obj[char]++;
            }else{
                obj[char] = 1;
            };
        }
    }
    return obj;
}
```
```js
// 리팩토링 후 코드
function charCount(str){
    var obj = {};
    for (var char of str){
        if(isAlphaNumeric(char)){
            char = char.toLowerCase();
            obj[char] = ++obj[char] || 1;
        }        
    }
    return obj;
}

function isAlphaNumeric(char){
    var code = char.charCodeAt (0);
    if(!(code > 47 && code < 58) && // numeric (0-9)
       !(code > 64 && code < 91) && // upper alphabet (A-Z)
       !(code > 96 && code < 123) // lower alphabet (a-z)
    ){
        return false;
    }
    return true;
}
```