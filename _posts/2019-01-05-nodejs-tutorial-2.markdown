---
layout: post
title:  "Node.js Tutorial #2"
date:   2019-01-05
categories: [Node]
tags: [backend, web]
---

### EventEmitter Class

event 모듈을 필요로 하고, 여러 가지 기능에 따라 다른 method를 사용한다.

* addListener(event, listener)
    * listener는 여러 번 추가될 수 있다 (같은 조합으로 여러 번 호출할 경우)
    * 지정된 event의 listener array의 끝에 해당 listener를 추가한다
* on(event, listener)
    * addListener와 차이는?
* once(event, listener)
    * 1회성 listener를 추가한다 
    * event가 이 다음에 호출되는 첫 번째 경우에 listener가 작동하고, 그 후에는 작동하지 않음
* removeListener(event, listener)
    * listener array에서 해당하는 listener를 제거한다
    * array index가 바뀐다
* removeAllListeners([event])
* setMaxListeners(n)
    * 기본적으로 EventEmitter는 10개 이상의 listener를 가질 때 경고메시지를 출력한다 
    * Zero input -> unlimited output
* listeners(event)
    * returns listener array
* emit(event, [arg1], [arg2], ....)
    * execute each of the listeners in order with the supplied arguments
    * return boolean for whether the event had listeners