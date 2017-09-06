---
layout: post
title: "linux tip"
description: "linux tip을 적은 페이지"
date: 2017-09-06
tags: [linux]
comments: false
share: false
---

리눅스를 사용하면서 알게된 팁.

--- 

## 1. core

**segmentation fault** 가 발생하면 당황하게 되는데 이때 당황하지 말고 **gdb**를 이용해서 확인해 보자.
> 어느분 말씀으론 인류가 정복하기 힘든 세가지가 linux kernel, vi editor, gdb 라고 하는데...

segmentation fault가 발생하면 다음 순서로 진행을 해보자
* dump size를 크게 잡기
* core 와 binary 올리기
* backtrace 보기
* f #n 으로 원하는 프레임으로 이동하기
* p val로 변수 값 확인해 보기