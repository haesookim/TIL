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
// pickOne will take the value of 'Truth' since an empty string takes a boolean value of false
var one = '';
var two = 'Truth';

var pickTwo = one || two;

// Essentially operates like this
var pickOne;

if (one){
    pickOne = one;
} else{
    pickOne = two;
}
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

* Arrow function syntax
    * Essentially the same as a function expression but uses the fat arrow syntax ()=> instead of using the keyword 'function'

{% highlight javascript %}
const identifier = (arg1, arg2) => {
    return;
}
{% endhighlight %}

* Conscise Arrow functions
    * Basically used for simplifying javascript code
    * If you have one argument/parameter, then you don't need parentheses
        * if you have zero or 2 <=, then you need parentheses
    * Single-line code blocks do not require curly braces
    * Implicit return
        * Single-line code implies the result of the expression will be the return value
        * this means that the return statement can be omitted

### Arrays

* can define arrays using the 'let' or 'const' keywords
    * with 'let'-defined arrays you can reassign elements or the entire array
    * with 'const'-defined arrays you can reassign individual elements, but not the entire array

* Mutating/non-mutating methods
    * Methods such as .push(), .pop() etc. are *mutating methods*, meaning that such methods, when called, will alter the original array and save a new form to it.
    * in contrast, methods like .slice() are non-mutating

### Pass-by Reference

When you pass a variable to a function: array 자료형 등은 값 자체가 대입되는 것이 아닌 값이 저장되어 있는 memory reference를 보내는 것, therefore the variable is modified outside of the scope
* Find a more robust explanation for this

### Functions

* Functions as a **First-class object**
    * In JavaScript, functions are also considered as data
    * as first-class objects, javaScript functions can have properties and methods as well as its invoked utility
        * i.e.) .name, .length, .tostring() etc.
    * We can also assign a function to a variable
{% highlight javascript %}
function thisDoesSomething(){
    console.log('do Something');
}

const do = thisDoesSomething;
// This will assign the functional value(reference) of the 'thisDoesSomething' function
// Not the return result! Note that there are no parentheses

do();
// This will have the same functionality as thisDoesSomething();
{% endhighlight %}