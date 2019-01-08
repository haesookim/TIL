---
layout: post
title:  "Javascript Notes"
date:   2019-01-07
categories: [Javascript]
tags: [Javascript, languages]
---
으악 자바스크립트로 앱 개발도 해봤으면서 이제서야 기초를 다지고 있다니 너무 웃기지만! 기초가 없는 상태로 쭉 가는 것모단 이게 더 낫겠지...

(심지어는 Node 스터디 포스팅이 더 먼저라니ㅠㅠ)

### Variable assignment
* var
    * Is function scoped
    * variable is declared globally no matter the block of declaration
* let : allows you to change the value later
    * Difference with var: is Block scoped
    * declaration only stands for the block it is declared in
    * 범위를 명확하게 정할 수 있으면 var보다 더 좋은 declaration method일 수도 있나?
* const : cannot change value
    * cannot leave as 'undefined' type, must be initialized with declaration

### String interpolation
* Must use backticks to ensure this working
    * not regular quotation marks!
    * on macOS korean mode, type using Option + '`' (otherwise will print ₩)
{% highlight javascript %}
var myName = 'Haesoo';
console.log(`my name is ${myName}.`);
// this will print 'my name is Haesoo.'
{% endhighlight %}

### '==' VS '===' : What's the difference?
* JS에서는 equal operator가 '==' 이 아니라 '==='이다
    * 다른 언어에서의 isEqual()과 동일한 역할을 한다 
    * type과 value의 일치를 검사한다는 느낌
    * unequal operator도 '!=='임
* '=='는 반면 value operator로서 typecast 후의 결과를 출력한다

### Conditionals
* Short-circuit
    * operands are considered from the left, and short-circuits if said operand is true
        * if first operand is true, the second operand is ignored even if true
        * if first operand is false, second operand is considered
    * used for defaulting a value?
    * This is how you implement it
{% highlight javascript %}
var one = '';
var two = 'Truth';

var pickTwo = one || two;
// pickOne will take the value of 'Truth' since an empty string takes a boolean value of false

var pickOne;

if (one){
    pickOne = one;
} else{
    pickOne = two;
}

// Essentially operates like this
{% endhighlight %}

### Function Expression

* Define a function within a function expression, using an anonymous function
    * declare a variable to take the function name (usually uses const)
    * assign an anonymous function to that variable

{% highlight javascript %}
// This is to declare the function

const identifier = function (arg1, arg2){
    return;
}

// This is to call the function

identifier(parameter1, parameter2);

{% endhighlight %}
