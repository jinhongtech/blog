---
date: 2023-09-16
title: "[컴퓨터 구조] 1.컴파일 시스템"
categories:
  - computer_science
  - computer_architecture
---

## The Compilation System(컴파일 시스템)

"hello, world" 를 출력하기 위해 다음과 같은 코드를 작성했습니다. 이 코드가 실행될 때 어떤 일들이 일어날까요?
```c
#include <stdio.h>

int main()
{
	printf("hello, world\n");
	return 0;
}
```

먼저 이 코드는 C로 작성되었습니다. 고급언어인 C언어는 사람이 읽고 이해하기 쉬운 형태지만 기계에게는 그렇지 않습니다. 기계는 번역기를 사용해 이를 저급언어인 기계어로 번역한 후에 읽을 수 있습니다. 이 때 기계어를 **executable object file(실행 가능한 오브젝트 파일)**, 번역기를 **compiler driver(컴파일러 드라이버)**라고 부릅니다.

## 컴파일 과정

GCC 컴파일러 드라이버를 사용해서 소스 코드 hello.c를 실행 가능한 오브젝트 파일 hello로 변환하는 과정을 살펴보겠습니다.
![1.compilation](/assets/images/computer_architecture/1.compilation.png)

1. **Preprocessing phase**
	- 먼저, 전처리기(cpp)가 소스 코드에서 \#으로 시작하는 전처리 구문을 처리하는 과정입니다. 예를 들어 우리는 코드에서 \# include <stdio.h>를 작성했습니다. 이는 소스 코드에 <stdio.h>라는 헤더 파일을 삽입하라는 의미입니다. 전처리 과정을 거쳐서 hello.c 는 hello.i로 변환됩니다.
2. **Compilation phase**
	- 컴파일러(cc1)가 어셈블리 언어로 번역하는 과정입니다.  프로그램을 어떤 고급 언어으로 작성했건 어떤 컴파일러를 사용했건 간에 출력 파일은 동일한 어셈블리 언어로 변환되기에 유용합니다. 컴파일 과정을 거쳐 hello.i는 hello.s로 변환됩니다.
3. **Assembly phase**
	- 어셈블러(as)가 hello.s를 기계어로 번역하고 이를 relocatable object file(재배치 가능한 오브젝트 파일)인 hello.o로 변환합니다. 
4. **Linking phase**
	- 우리가 작성한 hello.c에는 표준 C라이브러리에서 제공하는 printf 함수가 있습니다. 이 함수는 printf.o라는 분리된 오브젝트 파일에 존재하기 때문에 우리가 변환한 hello.o와 printf.o를 링커(ld)를 통해 합칩니다. 이를 통해 실행 가능한 오브젝트 파일인 hello를 만들 수 있습니다.



## 그래서 이거 왜 알아야 됨?


1. **프로그램 성능의 최적화**: 어떻게 컴파일러가 C를 기계어로 번역하는지 알고 기계 수준 언어에 대해 안다면 조금 더 나은 코드를 작성할 수 있습니다.
2. **링크 타임 에러의 이해**: 링커의 동작과 관련된 프로그래밍 에러를 이해할 수 있습니다.
3. **보안 문제 방지**: 버퍼 오버플로우로 발생되는 취약성을 방지할 수 있습니다.