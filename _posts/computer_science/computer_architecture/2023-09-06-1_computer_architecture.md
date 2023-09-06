---
date: 2023-09-05 11:28
title: "[CSAPP] Ch.1 A Tour of Computer Systems"
categories: [ computer_science, computer_architecture]
---


## The compilation system
- C언어는 고급 프로그래밍 언어라 인간 친화적이지만, 시스템에서 C 프로그램을 가동하기 위해서 저급 기계수준 명령어로 번역되어야 한다. 번역된 명령어를 executable object program(혹은 executable object file)이라 한다.
- 유닉스 시스템에서는 이 과정을 compiler driver가 수행하는데 다음과 같다.
- ![Ch1-1](/assets/images/a.png)
- 
	1. Preprocessing phase: 전처리기는 원본 .c 파일을 받아서 '#' 으로 시작하는 코드를 처리한다. 예를 들어 '#include <stdio>' 가 있는 위치에 stdio.h 파일을 삽입한다. 이 밖에서 주석 제거 등을 수행한다.
	2. 
	3. 
	4. 