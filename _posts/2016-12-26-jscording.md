---
layout: post
title: '자바스크립트 코딩 컨벤션'
description: "nhn 자바스크립트 코딩 컨벤션"
date: 2016-12-26
tags: [Js, jQuery, 자바스크립트, 제이쿼리]
comments: true
share: true
---

# 코딩 컨벤션
코딩 컨벤션은 **읽고, 관리하기 쉬운 코드를 작성하기 위한 일종의 코딩 스타일 규약**이다.<br>
특히 자바스크립트는 다른 언어에 비해 유연한 문법 구조를 가지고 있어 좀 더 엄격한 코딩 스타일 규약이 필요하다.<br>
아무리 작은 프로젝트라 하더라도 이후 유지 보수 및 추가 개발 등의 관리 이슈가 여전히 존재하기 때문에 코딩 스타일 규약은 반드시 필요하다.<br>
아래 가이드는 **프로그램의 성능을 해치지 않은 범위 내에서 가독성과 관리 용이성을 우선시**하여 작성하였으며, jsHint와 같은 **linter를 사용한다는 가정하에 linter로 검출할 수 없는 모호한 부분을 가이드** 한다.<br><br>

## 목차
* [들여쓰기](#들여쓰기)
* [문장의 종료](#문장의-종료)
* [명명규칙](#명명규칙)
* [전역변수](#전역변수)
* [선언과 할당](#선언과-할당)
    * [변수](#변수)
    * [배열과 객체](#배열과-객체)
    * [함수](#함수)
* [블럭의 줄바꿈](#블럭의-줄바꿈)
* [데이터형 확인하기](#데이터형-확인하기)
* [조건 확인하기](#조건-확인하기)
    * [값이 있는가?](#%EA%B0%92%EC%9D%B4-%EC%9E%88%EB%8A%94%EA%B0%80)
    * [값이 비어있는가?](#%EA%B0%92%EC%9D%B4-%EB%B9%84%EC%96%B4%EC%9E%88%EB%8A%94%EA%B0%80)
    * [할당된 값이 있는가?](#%ED%95%A0%EB%8B%B9%EB%90%9C-%EA%B0%92%EC%9D%B4-%EC%9E%88%EB%8A%94%EA%B0%80)
    * [참조변수가 참(true)인가?](#%EC%B0%B8%EC%A1%B0%EB%B3%80%EC%88%98%EA%B0%80-%EC%B0%B8true%EC%9D%B8%EA%B0%80)
    * [참조변수가 거짓(false)인가?](#%EC%B0%B8%EC%A1%B0%EB%B3%80%EC%88%98%EA%B0%80-%EA%B1%B0%EC%A7%93false%EC%9D%B8%EA%B0%80)
* [반환하기](#반환하기)
* [순회하기](#순회하기)

***

<br>
<br>

## 들여쓰기
절대 space와 tab을 섞어서 사용하지 않는다.<br>
프로젝트를 시작할 때 반드시 space와 tab 둘 중 하나를 선택해야 한다.<br>
이는 프로젝트의 성격에 따라 선택이 가능한 부분이며, space를 사용할 경우 2문자 또는 4문자를 사용한다.<br>
들여쓰기에 대한 규칙이 합의되면 편집기의 들여쓰기 설정을 규칙대로 설정해 놓고 사용할 것을 권장한다. <br>
> 참고<br>
FE개발팀은 space 4문자를 사용하고 있다.

<br><br>
## 문장의 종료
문장의 종료는 반드시 세미콜론(;)을 사용한다.<br>
자바스크립트는 이를 문법적으로 강제하지 않지만, 종종 생각지 못한 오류를 만들고 디버깅을 어렵게 한다.<br>
> 참고<br>
[안티 패턴 - 문장의 끝은 세미콜론(;)을 사용하라](https://github.com/nhnent/fe.javascript/wiki/%EC%95%88%ED%8B%B0-%ED%8C%A8%ED%84%B4#%EB%AC%B8%EC%9E%A5%EC%9D%98-%EB%81%9D%EC%9D%80-%EC%84%B8%EB%AF%B8%EC%BD%9C%EB%A1%A0%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC)

<br><br>
## 명명규칙
* 공백을 허용하지 않는다.
* 상수는 대문자와 '_'를 사용한다.
* 생성자는 대문자 카멜표기법을 사용한다.
* 함수, 변수는 소문자 카멜표기법을 사용한다.
    * 배열은 복수형 이름을 사용
    * 정규표현식은 'r'로 시작
    * 이벤트 핸들러는 'on'으로 시작
    * 반환 값이 불린인 함수는 'is'로 시작
    * private은 '_'로 시작
    * 커스텀 객체의 프로퍼티 이름에도 동일

[상수]
```javascript
SYMBOLIC_CONSTANTS;
```
[생성자]
```javascript
ConstructorName;
```
[변수]
```javascript
// 숫자, 문자, 불린
dog;
variableName;

// 배열
dogs;

// 정규표현식
rDesc;
```
[함수]
```javascript
// 함수
functionName;

// 이벤트 핸들러
onClickEventHandler;

// 불린 반환 함수
isAvailable;
```
[private]
```javascript
_privateVariableName;
_privateFunctionName;
```
[커스텀 객체와 프로퍼티]
```javascript
customObjectName;
customObjectName.propertyName;
customObjectName._privatePropertyName;
_privateCustomObjectName;
_privateCustomObjectName._privatePropertyName;
```

<br><br>
## 전역변수
네임스페이스를 사용하여 전역변수를 최소화하며 암묵적인 전역변수는 절대로 사용하지 않는다.<br>
> 참고<br>
[안티 패턴 - 전역변수 대신 네임스페이스를 사용하라](https://github.com/nhnent/fe.javascript/wiki/%EC%95%88%ED%8B%B0-%ED%8C%A8%ED%84%B4#%EC%A0%84%EC%97%AD%EB%B3%80%EC%88%98-%EB%8C%80%EC%8B%A0-%EB%84%A4%EC%9E%84%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC)<br>
[안티 패턴 - 변수 선언시 반드시 "var" 키워드를 사용하라](https://github.com/nhnent/fe.javascript/wiki/%EC%95%88%ED%8B%B0-%ED%8C%A8%ED%84%B4#%EB%B3%80%EC%88%98-%EC%84%A0%EC%96%B8%EC%8B%9C-%EB%B0%98%EB%93%9C%EC%8B%9C-var-%ED%82%A4%EC%9B%8C%EB%93%9C%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC)

[전역변수]
```javascript
// Bad
myglobal = "hello";
```
[암묵적 전역 - 1]
```javascript
// Good
function sum(x, y) {
   var result = x + y;
   return result;
}

// Bad
function sum(x, y) {
   result = x + y;
   return result;
}
```
[암묵적 전역 - 2]
```javascript
// Good
function foo() {
   var a,
       b;
   a = b = 0;
}

// Bad
function foo() {
   var a = b = 0;           // var a = (b = 0);와 같다. b가 암묵적 전역이 된다.
}
```

<br><br>
## 선언과 할당
### 변수
변수의 선언은 호이스팅 비용과 가독성을 고려하여 분산시키지 않고, 함수 스코프의 시작 지점에서 var를 한 번만 사용하여 선언한다.<br>
변수는 var 선언과 동시에 할당(초기화)하는 것을 원칙으로 하지만, 아래와 같은 예외 상황을 허용한다.<br>
* 선언과 할당을 동시에 함으로 인해 가독성이 크게 떨어지는 경우, 선언과 할당을 나눠서 할 수 있다.<br>
이런 경우라도 선언은 반드시 스코프의 시작 지점에서 수행되어야 하며, 할당은 최대 두 번까지 사용하는 시점에 나눠 처리할 수 있다.<br>
* 할당 없이 선언만 하는 변수가 많을 경우, 한 줄로 연결해서 선언할 수 있다.<br>
* 선언만 하는 변수와 선언과 동시해 할당을 하는 변수가 섞여 있을 경우, 가독성을 생각하여 이 둘을 적절히 구분하여 선언한다.<br>
* 함수를 바로 빠져나가는 예외처리 조건문이 있을 경우, 변수의 할당은 반드시 예외처리 조건문 이후에 처리한다.
* CommonJS 방식의 모듈 선언으로 인해 외부와 내부에서 사용하는 변수를 구분해야 할 경우, var를 두 번에 나눠 사용할 수 있다.
* 콜백 등을 처리하기 위해 익명 함수를 사용할 경우, 해당 익명 함수의 스코프 안에서 변수를 선언하되 위의 룰을 그대로 적용한다.<br>
이 경우 필요에 따라서는 변수를 외부에 선언하여 클로저를 사용하는 것을 허용한다.

> 참고<br>
[안티 패턴 - 변수와 함수는 사용하기 전에 선언하라](https://github.com/nhnent/fe.javascript/wiki/%EC%95%88%ED%8B%B0-%ED%8C%A8%ED%84%B4#%EB%B3%80%EC%88%98%EC%99%80-%ED%95%A8%EC%88%98%EB%8A%94-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-%EC%A0%84%EC%97%90-%EC%84%A0%EC%96%B8%ED%95%98%EB%9D%BC)

[변수의 선언 및 할당]
```javascript
// Good
var foo = '',
    bar = '',
    quux;

// Bad
var foo = '';
var bar = '';
var qux;
```
```javascript
// Good(1)
var foo, bar, quux;

// Good(2)
var foo,
    bar,
    quux;

// Bad
var foo;
var bar;
var qux;
```
```javascript
// Good
var foo, bar, quux, item,
    i = 0,
    j = 0,
    len = this._array.length,
    len2 = this._array2.length;

// Bad
var foo;
var bar;
var qux;
var i = 0;
var j = 0;
var len = this._array.length;
var len2 = this._array2.length;
var item;
```
[스코프내 변수 선언]
```javascript
// Good
function foo() {
    var bar = '',
        qux;
    ...
}

// Bad
function foo() {
    ...
    var bar = '',
        qux;
}
```
[변수가 많아져 가독성이 떨어질 경우]
```javascript
// Good
function foo() {
    var i,
        j,
        len,
        len2,
        item;

    i = 0;
    len = this._array.length;
    for (; i < len; i++) {
        item = this._array[i];
        ...
    }

    // 선언은 집입부에서 하고, 할당은 사용 시점에 수행
    j = 0;
    len2 = this._array2.length;
    for (; j < len2; j++) {
        item = this._array2[j];
        ...
    }
 }

// Bad
function foo() {
    var i = 0;
        len = this._array.length;

    for (; i < len; i++) {
        ...
    }

    // statement 내에서의 var 사용 제한
    for (var j = 0, len2 = this._array2.length; j < len2; j++) {
        // statement 내에서의 var 사용 제한
        var item = this._array2[j];
        ...
    }
}
```
[선언 시점에 값이 할당되지 않는 변수들]
```javascript
// bad
var i = 0, length = ary.length, j, k;

// good
var i = 0,
    length = ary.length,
    j,
    k;

// good
var i = 0,
    length = ary.length,
    j, k;
```
[예외처리로 바로 빠져나가는 경우]
```javascript
// Good
function foo(isValid) {
    var i,
        len;

    // 예외처리로 바로 빠져나감
    if (!isValid) {
        return false;
    }

    // 선언은 집입부에서 하고, 할당은 사용 시점에 수행
    i = 0;
    len = this._array.length;
    for (; i < len; i++) {
    ...
}

// Bad
function foo() {
    // 진입부에서 변수 선언과 할당 동시 수행 제한
    var i = 0;
        len = this._array.length;

    // 예외처리로 바로 빠져나감
    if (!isValid) {
        return false;
    }

    for (; i < len; i++) {
    ...
}
```
[콜백 등 익명 함수를 사용하는 경우]
```javascript
// Good
function foo() {
    ...

    // 익명 함수의 스코프 안에서 변수 선언
    forEach(ary, function(data1, data2) {
        var resultData1 = calcData(data1),
            resultData2 = calcData(data2);
    ...
    });
}

// Allow
function foo() {
    var length = ary.length,
        i = 0,
        ...

    forEach(ary, function(data1, data2) {
        var resultData1 = calcData(data1),
            resultData2 = calcData(data2);
        ...

        // 필요에 따라 외부에 변수 선언 가능 (클로저 사용 허용)
        i += (length + 2);
        ...
    });
}

// Not Good
function foo() {
    var resultData1, resultData2,
    ...

    forEach(ary, function(data1, data2) {
        resultData1 = calcData(data1);
        resultData2 = calcData(data2);
        ...
    });
}
```

<br><br>
### 배열과 객체
배열과 객체는 반드시 리터럴로 선언한다.<br>
> 참고<br>
[안티 패턴 - 배열과 객체는 리터럴 표기법을 사용하라](https://github.com/nhnent/fe.javascript/wiki/%EC%95%88%ED%8B%B0-%ED%8C%A8%ED%84%B4#%EB%B0%B0%EC%97%B4%EA%B3%BC-%EA%B0%9D%EC%B2%B4%EB%8A%94-%EB%A6%AC%ED%84%B0%EB%9F%B4-%ED%91%9C%EA%B8%B0%EB%B2%95%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC)

[배열]
```javascript
// Good
var emptyArr = [];
var arr = [1, 2, 3, 4, 5];

// Bad
var emptyArr = new Array();
var arr = new Array(1, 2, 3, 4, 5);
```
[객체]
```javascript
// Good
var emptyObj = {};
var obj = {
    pro1: 'val1',
    pro2: 'val2'
};

// Bad
var emptyObj = new Object();
var obj = new Object();

// 추가: 객체의 프로퍼티가 1개인 경우에만 한줄 정의를 허용한다.
// Good
var obj = {foo: 'a'};

// Good
var obj = {
    foo: 'a'
}

// Bad
var obj = {foo: 'a', bar: 'b'}
```

<br><br>
### 함수
함수는 함수 선언식 또는 함수 표현식을 사용하여 선언한다.<br>
> 참고<br>
[안티 패턴 - 함수 생성자 new Function()은 사용하지 마라](https://github.com/nhnent/fe.javascript/wiki/%EC%95%88%ED%8B%B0-%ED%8C%A8%ED%84%B4#%ED%95%A8%EC%88%98-%EC%83%9D%EC%84%B1%EC%9E%90-new-function%EC%9D%80-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EB%A7%88%EB%9D%BC)

```javascript
// Good(1) - 함수 선언식
function doSomething(param1, param2) {
    return param1 + param2;
}

// Good(2) - 함수 표현식
var doSomething = function(param1, param2) {
    return param1 + param2;
}

// Bad
var doSomething = new Function('param1', 'param2', 'return param1 + param2;');
```

<br><br>
## 블럭의 줄바꿈
if/for/while/try 등 블럭 구문을 사용할 때에는 한줄로 빼곡히 사용하지 않는다.<br>
키워드와 조건문 사이에 빈 칸을 사용하고, 괄호로 블럭의 시작과 끝을 명확히 정의하고, 줄 바꿈하여 사용한다.<br>
한 줄짜리 블럭일 경우 {}를 생략할 수 있지만, 이는 코드 구조를 애매하게 만든다.<br>
당장은 라인 두 줄을 줄일 수 있겠지만 이후 오류 발생 확률이 높은 잠재적 위험 요소가 된다.<br>
> 참고<br>
[안티 패턴 - {}를 생략하지 마라](https://github.com/nhnent/fe.javascript/wiki/%EC%95%88%ED%8B%B0-%ED%8C%A8%ED%84%B4#%EB%A5%BC-%EC%83%9D%EB%9E%B5%ED%95%98%EC%A7%80-%EB%A7%88%EB%9D%BC)

[if]
```javascript
// Good
if (condition) {
    ...
}

// Bad
if(condition) doSomething();
```
[if-else]
```javascript
// Good
if (condition) {
    ...
} else {
    ...
}

// Bad
if(condition) doSomething();
else doAnything();
```
[for]
```javascript
// Good
for (var i = 0; i < 100; i++) {
    ...
}

// Better(1)
var i,
    length = 100;
for (i = 0; i < length; i++) {
    ...
}

// Better(2)
var i = 0,
    length = 100;
for (; i < length; i++) {
    ...
}

// Bad
for(var i=0;i<100;i++) someIterativeFn();
```
[for-in]
```javascript
// Good
var prop;
for (prop in object) {
    ...
}

// Bad
for(var prop in object) someIterativeFn();
```
[while]
```javascript
// Good
while (condition) {
    ...
}

// Bad
while(condition) iterating++;
```

<br><br>
## 데이터형 확인하기
암묵적 캐스팅으로 인한 혼동을 막기 위해 완전항등연산자인 ===, !== 만을 사용한다.<br>
> 참고<br>
[안티 패턴 - "==" 대신 "==="을 사용하라](https://github.com/nhnent/fe.javascript/wiki/%EC%95%88%ED%8B%B0-%ED%8C%A8%ED%84%B4#-%EB%8C%80%EC%8B%A0-%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC)

[문자열]
```javascript
typeof variable === 'string'

// code-snippet.js 사용 시
ne.util.isString(variable)
```
[숫자]
```javascript
typeof variable === 'number'

// code-snippet.js 사용 시
ne.util.isNumber(variable)
```
[불린]
```javascript
typeof variable === 'boolean'

// code-snippet.js 사용 시
ne.util.isBoolean(variable)
```
[객체]
```javascript
typeof variable === 'object'

// code-snippet.js 사용 시
ne.util.isObject(variable)
```
[배열]
```javascript
Array.isArray(arrayObject)

// code-snippet.js 사용 시
ne.util.isArray(variable)
```
[널 Null]
```javascript
variable === null

// code-snippet.js 사용 시
ne.util.isNull(variable)
```
[미할당 Undefined]
```javascript
// 전역변수
typeof variable === 'undefined'
// 지역변수
variable === undefined

// code-snippet.js 사용 시
ne.util.isUndefined(variable)
```
[엘리먼트 노드]
```javascript
element.nodeType === 1

// code-snippet.js 사용 시
ne.util.isHTMLNode(variable)
```

<br><br>
## 조건 확인하기
### 값이 있는가?
[문자열] : 빈 문자열이 아닌가?
```javascript
// Good(1)
if (string) ...

// Good(2) - code-snippet.js 사용 시
if (ne.util.isNotEmpty(string)) ...

// Bad
if (string !== "") ...
```
[배열] : 순회할 요소가 있는가?
```javascript
// Good(1)
if (array.length) ...

// Good(2) - code-snippet.js 사용 시
if (ne.util.isNotEmpty(array)) ...

// Bad
if (array.length > 0) ...
```
[객체] : 순회할 속성이 있는가?
```javascript
// Good - code-snippet.js 사용 시
if (ne.util.isNotEmpty(object)) ...
```

<br><br>
### 값이 비어있는가?
[문자열] : 빈 문자열인가?
```javascript
// Good(1)
if (!string) ...

// Good(2) - code-snippet.js 사용 시
if (ne.util.isEmpty(string)) ...

// Bad
if (string === "") ...
```
[배열] : 빈 배열인가?
```javascript
// Good(1)
if (!array.length) ...

// Good(2) - code-snippet.js 사용 시
if (ne.util.isEmpty(array)) ...

// Bad
if (array.length === 0) ...
```
[객체] : 빈 객체인가?
```javascript
// Good - code-snippet.js 사용 시
if (ne.util.isEmpty(object)) ...
```

<br><br>
### 할당된 값이 있는가?
```javascript
// Good - code-snippet.js 사용 시
if (ne.util.isExisty(variable)) ...
```

<br><br>
### 참조변수가 참(true)인가?
```javascript
// Good
if (variable) ...

// Bad(1)
if (variable == true) ...

// Bad(2)
if (variable === true) ...
```

<br><br>
### 참조변수가 거짓(false)인가?
```javascript
// Good
if (!variable) ...

// Bad(1)
if (variable == false) ...

// Bad(2)
if (variable === false) ...
```

<br><br>
## 반환하기
특정 값을 반환해야 하는 경우, 함수의 맨 마지막에서 한 번만 return 한다.<br>
단, 예외 처리로 빠져나가기 위해 사용하는 return false;는 제외한다.
```javascript
// Good
function getResult() {
    var resultData,
    ...

    if (condition) {
        ...
        resultData = someDataInTrue;
    } else {
        ...
        resultData = someDataInFalse;
    }

    return resultData;
}

// Bad
function getResult() {
    ...
    if (condition) {
        ...
        return someDataInTrue;
    }
    ...
    return someDataInFalse;
}
```

<br><br>
## 순회하기
[배열]
```javascript
// Good
for(var i = 0, len = array.length; i < len; i++) ...

// Better(1)
var i = 0,
    len = array.length;
for (; i < len; i++)  ...

// Better(2) - code-snippet.js 사용 시
ne.util.forEachArray(array, function(value, index) {
    ...
});

// Better(3) - code-snippet.js 사용 시
ne.util.forEach(array, function(value, index) {
    ...
});

// Bad
for (var i = 0; i < array.length; i++) ...

// worse
for (var i in array) ...
```
[객체]
```javascript
// good(1)
for (var key in object) ...

// good(2) - code-snippet.js 사용 시
ne.util.forEach(object, function(value, key) {
    ...
});
```

<br><br>
## Return 위치
  Retrun문을 여러곳에서 사용하지 않는다.<br>
  1. 예외처리 조건문
  2. 결과 값

```javascript
// bad
if (condition) {
    ...
    return someDataInTrue;
} else {
    ...
    return someDataInFalse;
}

// good
if (condition) {
    ...
    resultData = someDataInTrue;
} else {
    ...
    resultData = someDataInFalse;
}
return resultData;

// good for exception
if (!ne.util.isNumber(someData)) {
    return ;
}
...
```

<br><br>
## Callback function의 Scope
  되도록이면 Closure의 사용을 피하고 각 스코프에 알맞게 변수를 선언한다.

```javascript
// bad
var data1, data2, ...;

forEach(arr, function() {
    data1 = someFunction1();
    data2 = someFunction2();
    ...
});

// good
forEach(arr, function() {
    var data1 = someFunction1(),
        data2 = someFunction2();
    ...
});

// case that allows closure
var someValue = 0,
    length = arr.length,
    ...;

forEach(arr, function() {
    var data1 = someFunction1(),
        data2 = someFunction2();

    ...
    someValue += data1 + data2 - length;
});
```