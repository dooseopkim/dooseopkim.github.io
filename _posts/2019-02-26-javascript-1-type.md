---
title: Javascript 변수-연산자- 타입
layout: article
sharing: true
license: true
aside:
  toc: true
show_edit_on_github: true
show_subscribe: false
pageview: true
comments: true
key: 20190226javascript1
tags: javascript
---

## 자바스크립트의 버전

- 자바스크립트 버전은 ECMAScript(줄여서ES)의 버전에 따라서 결정되고, 이를 자바스크립트 실행 엔진이 반영합니다.
- ES5, ES6(ES2015).. 이런 식으로 버전을 일컫습니다.
- 2018년을 중심으로 ES6를 지원하는 브라우저가 많아서 몇 년간 ES6 문법이 표준으로 쓰이고 있습니다.
- ES6는 ES5문법을 포함하고 있어 하위호환성 문제가 없습니다.
- 다만 feature별로 지원하지 않는 브라우저가 있을 수 있어 조심해야 합니다.

## 변수   
- 변수는 var, let, const 로 선언할 수 있습니다.
- 어떤 것을 사용하는가에 의해서 scope, 즉 변수의 유효범위가 달라집니다.
- ES6이전까지는 var를 사용해서 변수를 선언할 수 있습니다.


&nbsp;  
보통 이제 let과 const 같은 경우에는  ES6에 있는 기능들이고 그전에 코드들은 아직은 var로 선언을 많이 합니다.  
const와 let의 차이는 재할당이 되냐 안되냐 정도로 정리할수 있습니다.
## 연산자

- 연산자 우선순위를 표현하기 위해서는 ()를 사용하면 됩니다. 
- 수학연산자는 +,-,*,/,%(나머지) 등이 있습니다.
- 그리고 논리 연산자, 관계연산자, 삼항연산자도 있습니다. 

```javascript
//or 연산자 활용
const name = "crong";
const result = name || "pororo";
console.log(result);
var name = "";
var result = name || "pororo";
console.log(result);
```
const name에 값을 할당하고
result에 name이 있느냐? or 연산자를 쓰고 있습니다.
name이 있으면 name이 쓰이고 없으면 'pororo' 가 쓰이는 것입니다. 
AND 연산자일 경우에는 왼쪽 것도 확인하지만 오른쪽 것도 확인 오른쪽 것도 무조건 확인을 하게 돼있죠.
### 연산자 - 삼항연산자
간단한 비교와 값 할당은 삼항연산자를 사용할 수 있습니다.  
```javascript
const data = 11;
const result = (data > 10) ? "ok" : "fail";
console.log(result);
```  

data가 11이고, result는 data가 10보다 크냐? 그럼 "ok" 아니면 "fail" 이렇게 나와있습니다.  
만약 if문으로 표현하려면  
```javascript
const data = 11;
let result = "";
if(data > 10){
	result = "ok";
}else{
	result = "fail";
}
console.log(result);
```
로 할 수 있습니다.  
삼항연산자는 if문이나 그런 조건문들을 아주 간단하게 이렇게 표현할 수가 있습니다.
### 연산자 - 비교연산자
비교는 == 보다는 ===를 사용합니다.
==로 인한 다양한 오류 상황이 있는데 아래 결과를 참고해봅시다. 
```javascript
0 == false;                          //true
"" == false;                         //true
null == false;                    //false
0 == "0";                             //true
null==undefined;         //true
```
 0이랑 false는 다른거 아니야? 라고 생각할 수도 있겠지만
true가 나옵니다 자바스크립트에서는  
공백문자열과 false 또한 true, null과 false를 제외한 모든 비교의 값이 true인 이유는   '=='과 '===' 의 차이입니다.
'==' 는 최대한 타입을 너 혹시 0과 0을 비교한 거 아니야? 라고 자기가 임의적으로 암묵적으로 타입을 바꿔서 비교를 하게 돼는 성질이 있습니다.
```javascript
0 === false;	                  //false
"" === false;	                  //false
null == false;	                //false
0 === "0";		                    //false
null === undefined; 	//false
```
'==='는 크게 얘기해 보면은 그거의 정확한 타입까지 비교를 하게 돼있습니다.  그래서 타입까지 비교를 하려면  다른 언어를 했다고 하는 분들이 특히 헷갈릴 수 있는데 ==은 많이 안쓰고.
===를 습관적으로 많이 쓰시는 게 무조건 좋다. 라고 얘기 드릴 수가 있습니다.


## 자바스크립트의 Type
자바스크립트 타입에는 다양한 것이 존재합니다.  
```javascript
undefined, null, boolean, number, string, object, function, array, Date, RegExp
```
- 타입은 선언할 때가 아니고, 실행타임에 결정됩니다.
- 함수안에서의 파라미터나 변수는 실행될 때 그 타입이 결정됩니다. 
- 타입을 체크하는 또렷한 방법은 없습니다.
- 정확하게는 toString.call 함수를 이용해서 그 결과를 매칭하곤 하는데, 문자, 숫자와 같은 자바스크립트 기본 타입은 'typeof' 키워드를 사용해서 체크할 수 있습니다. 
- 배열은 타입을 체크하는 isArray함수가 표준으로 생겼습니다.
IE와 같은 구 브라우저를 사용해야 한다면 지원범위를 살펴보고 사용해야 합니다.  

&nbsp;  
자바스크립트는 선언할 때 타입이 없고 실행 타임에 결정된다는 말은 만약
```javascript
var f1 = function(a){
	console.log(typeof(a));
}
```
이렇게 해서  console.log(typeof(a)) 한다고 할 때
매개변수로 a가 선언된 함수지만 우리가 run을 a의 타입은 실행 타임에 결정됩니다.
a에다가 문자열을 주면... string이 나오고
불리언 타입을 줬다 그러면? boolean이 나옵니다.
즉 a 타입은 실행 타임에 결정돼요.
지금 여기서 말씀드리는 게 그 얘기입니다.
선언될 때가 아니고 실행 타임에 결정됩니다.
그래서 타입이 없는 언어다! 라는 말 보다는 타입이 나중에 결정된다. 실행 타임에 결정되는 언어다. 라고 얘기할 수가 있습니다. 다이나믹 타입 이런 말도 씁니다.
자바스크립트의 타입을 확일 할 때는 위에 사용했던 것처럼 `typeof()`로 간단한 기본타입의 확인이 가능합니다. 
더 정확한 타입확인은  `toString.call()` 을 사용해보시기 바랍니다.
