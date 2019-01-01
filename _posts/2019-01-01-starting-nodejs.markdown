---
layout: post
title:  "Node.js 설치 및 시작"
date:   2019-01-01
categories: [Node]
tags: [backend, web]
---
Disclaimer: TutorialsPoint의 Node.js 튜토리얼을 기반으로 공부중

### Node.js application fundamentals

Node.js로 만들어진 어플리케이션은 다음 세 가지 요소로 구성되어 있다:
* 모듈 import하기: require 함수를 사용하여 불러온다
{% highlight javascript %}
var http = require("http");
{% endhighlight %}
* 서버 만들기: 클라이언트 측의 요청을 받아들일 서버를 만든다 
    * (시스템프로그래밍에서 배웠던 네트워크 프로그래밍을 여기서 쓸 줄이야ㅠ)
{% highlight javascript %}
http.createServer(function (request, response){
    // HTTP response의 Header 부분을 지정한다 
    // Status code(이 경우에는 200 == OK, 404, 403 등등..)와 content type 등의 header information을 채운다
    response.writeHead(200, {'Content-Type: 'text/plain'});

    // response Body content
    response.end('input content here');
}).listen(8081);
// 8081번 port를 지정한다
// 이렇게 하면 http://127.0.0.1:8081에서 서버가 돌아간다 (localhost 상의 8081번 포트)
{% endhighlight %}
* request processing: 클라이언트가 보낸 request를 받고, processing을 거쳐 response를 보낸다 
    * 실제 Node 프로그램 실행 및 서버 리퀘스트를 받는 것까지
    * (대체 한국어로 메모하는 것의 의미 무엇)

### REPL

파이썬 idle처럼 Read/Eval/Print/Loop을 터미널 상에서 실행할 수 있다. 실행방법은
{% highlight %}
$ node
{% endhighlight %}
이렇게 하면 됨

### NPM 및 패키지 모듈

Node Package Manager(NPM): Node.js 패키지 유틸리티 및 버전관리 툴
{% highlight %}
$ npm install <Module Name>
{% endhighlight %}
이런 식으로 각종 모듈을 locally 설치할 수 있다. 이렇게 설치한 모듈은 *require()*함수로 불러올 수 있음

다만 이렇게 모듈을 설치할 경우 local mode로 들어가며, 해당 앱의 node_modules 디렉토리에서만 찾을 수 있고 다른 앱에서는 찾을 수 없다....?

{% highlight %}
$ npm install <Module Name> -g
{% endhighlight %}
그래서 global mode로 설치해 줄 필요가 있음. 이때는 각 앱의 디렉토리가 아닌 시스템 디렉토리에 저장되고, require() 함수로 불러올 수 없지만 커맨드라인 상에서 실행할 수 있다

참고할 기능들 
{% highlight %}
$ npm uninstall <Module Name>
{% endhighlight %}

{% highlight %}
$ npm update <Module Name>
{% endhighlight %}

{% highlight %}
$ npm search <Module Name>
{% endhighlight %}

새 모듈을 만들 경우: adduser, publish 등을 함께 사용하여 직접 모듈을 공개적으로 전시(?)할 수 있다. npm init를 사용할 경우 package.json 파일을 만들기 위한 기만 데이터를 다 받아오는 형식
{% highlight %}
$ npm init
{% endhighlight %}

### Callback 함수와 비동기 프로그래밍(?)

* GET BACK ON THIS
* Callback 형식으로 쓰여진 코드는 기본적으로 non-blocking 성격을 가진다.
* blocking code는 sequential하기 때문에 같은 블럭 안에서는 논리적 순서를 가지고 실행되지만 scalability가 좋지 않은 편
* 반면 non-blocking code는 각 callback block 단위로 동시에 실행, 블럭 간의 sequence가 사실상 존재하지 않는다. 각 블럭은 parallel processing으로 계속 진행되는 듯
