---
layout: post
title:  "Figuring out Scrollytelling"
date:   2019-05-03
categories: [Front-end]
tags: [scrollytelling, Javascript, web, frontend]
---

## ScrollyTelling using position sticky

CSS에는 position: sticky라는 attribute가 있다. 기본적으로는 position: relative와 position: fixed의 기능을 섞인 상태로 가지고 있는 것인데, 사용자가 directional variable (top, bottom, left, right)으로 지정한 일정 threshold에 닿기 전까지는 position: relative의 성격을 지니고 있다가 threshold에 도달하면 position: fixed의 형태로 바뀐다.

이 방법을 사용해 scrollytelling을 할 경우, 자바스크립트를 활용한 다양한 스크롤 이벤트를 잡아 줄 필요성이 줄어든다. (scrolly element 내에서 애니메이션을 넣어 줄 경우 step trigger 등이 추가적으로 필요하다)