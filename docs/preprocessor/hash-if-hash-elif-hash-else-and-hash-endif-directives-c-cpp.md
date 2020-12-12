---
description: '자세한 정보: #if, #elif, #else 및 #endif 지시문 (C/c + +)'
title: '#if, #elif, #else 및 #endif 지시문(C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
ms.openlocfilehash: 511f79da4957f7a26c9af9dbcad46fc29e70d785
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300485"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if, #elif, #else 및 #endif 지시문 (C/c + +)

**#Elif**, **#else** 및 **#endif** 지시문을 사용 하는 **#if** 지시문은 소스 파일의 부분에 대 한 컴파일을 제어 합니다. **#If** 된 후에 작성 하는 식에 0이 아닌 값이 있으면 **#if** 지시문 바로 다음에 오는 줄 그룹이 변환 단위에 유지 됩니다.

## <a name="grammar"></a>문법

*조건* : \
&nbsp;&nbsp;&nbsp;&nbsp;*if part elif-parts*<sub>opt</sub> *else-part*<sub>opt</sub> *endif-line*

*-part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*if 줄 텍스트*

*if-line* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *상수 식*\
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *식별자*\
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *식별자*

*elif-파트* : \
&nbsp;&nbsp;&nbsp;&nbsp;*elif 줄 텍스트*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif 부분 줄 텍스트*

*elif 줄* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#elif**  *상수 식*

*else-파트* : \
&nbsp;&nbsp;&nbsp;&nbsp;*다른 줄 텍스트*

*else 줄* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif-줄* : \
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

## <a name="remarks"></a>설명

소스 파일의 각 **#if** 지시문은 closing **#endif** 지시문과 일치 해야 합니다. **#If** 와 **#endif** 지시문 사이에는 여러 개의 **#elif** 지시문이 나타날 수 있지만 최대 하나의 **#else** 지시어를 사용할 수 있습니다. **#Else** 지시문 (있는 경우)은 **#endif** 전에 마지막 지시문 이어야 합니다.

**#If**, **#elif**, **#else** 및 **#endif** 지시문은 다른 **#if** 지시문의 *텍스트* 부분에 중첩할 수 있습니다. 각각의 중첩 된 **#else**, **#elif** 또는 **#endif** 지시문은 가장 가까운 **#if** 지시문에 속합니다.

**#If** 및 **#ifdef** 와 같은 모든 조건부 컴파일 지시문은 파일 끝 앞에 닫는 **#endif** 지시문과 일치 해야 합니다. 그렇지 않으면 오류 메시지가 생성 됩니다. 조건부 컴파일 지시문이 포함 파일에 포함된 경우 동일한 조건을 만족해야 합니다. 포함 파일의 끝에 일치하지 않는 조건부 컴파일 지시문이 없어야 합니다.

매크로는 **#elif** 명령 다음에 오는 줄 부분 내에서 수행 되므로 *상수 식* 에서 매크로 호출을 사용할 수 있습니다.

전처리기는 추가 처리를 위해 지정 된 *텍스트* 중 하나를 선택 합니다. *텍스트* 에 지정 된 블록은 임의의 텍스트 시퀀스 일 수 있습니다. 두 줄 이상을 차지할 수 있습니다. 일반적으로 *텍스트* 는 컴파일러 또는 전처리기에 의미가 있는 프로그램 텍스트입니다.

전처리기는 선택한 *텍스트* 를 처리 하 여 컴파일러에 전달 합니다. *Text* 에 전처리기 지시문이 포함 된 경우 전처리기는 해당 지시문을 수행 합니다. 전처리기에서 선택한 텍스트 블록만 컴파일됩니다.

전처리기는 true (0이 아닌) 상수 식을 찾을 때까지 각 **#if** 또는 **#elif** 지시문 뒤에 있는 상수 식을 계산 하 여 단일 *텍스트* 항목을 선택 합니다. 모든 텍스트 (로 시작 하는 기타 전처리기 지시문 포함 **#** )를 연결 된 **#elif**, **#else** 또는 **#endif** 으로 선택 합니다.

모든 *상수 식이* false 인 경우 또는 **#elif** 지시문이 나타나지 않는 경우 전처리기는 **#else** 절 다음의 텍스트 블록을 선택 합니다. **#Else** 절이 없고 **#if** 블록에서 *상수 식* 의 모든 인스턴스가 false 인 경우 텍스트 블록이 선택 되지 않습니다.

*상수 식은* 다음과 같은 추가 제한이 있는 정수 상수 식입니다.

- 식은 정수 계열 형식 이어야 하며 정수 상수, 문자 상수 및 **정의 된** 연산자만 포함할 수 있습니다.

- 식에서는 **`sizeof`** 또는 형식 캐스팅 연산자를 사용할 수 없습니다.

- 대상 환경에서 모든 범위의 정수를 표시 하지 못할 수 있습니다.

- 변환은 형식과 동일한 방식으로 형식을 나타냅니다 **`int`** **`long`** **`unsigned int`** **`unsigned long`** .

- 변환기는 문자 상수를 대상 개발 환경에 대한 집합과 다른 코드 값의 집합으로 변환할 수 있습니다. 대상 환경의 속성을 확인 하려면 해당 환경에 대해 빌드된 앱을 사용 하 여 제한 값을 확인 *합니다. H* 매크로.

- 식은 환경을 쿼리하지 않아야 하 고 대상 컴퓨터의 구현 세부 정보에서 절연 된 상태를 유지 해야 합니다.

## <a name="preprocessor-operators"></a>전처리기 연산자

### <a name="defined"></a>정의되는 위치

다음 구문에 나와 있는 것 처럼 특수 상수 식에 **정의** 된 전처리기 연산자를 사용할 수 있습니다.

> **정의 됨 (** *식별자* **)**\
> **정의 된** *식별자*

이 상수 식은 *식별자* 가 현재 정의 된 경우 true (0이 아님)로 간주 됩니다. 그렇지 않으면 조건은 false(0)입니다. 빈 텍스트로 정의된 식별자는 정의된 것으로 간주됩니다. **정의** 된 연산자는 **#if** 및 **#elif** 지시문에 사용할 수 있지만 다른 곳에서는 사용할 수 없습니다.

다음 예제에서 **#if** 및 **#endif** 지시문은 세 가지 함수 호출 중 하나의 컴파일을 제어 합니다.

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

`credit` 식별자가 정의된 경우 `CREDIT`에 대한 함수 호출이 컴파일됩니다. `DEBIT` 식별자가 정의된 경우 `debit`에 대한 함수 호출이 컴파일됩니다. 식별자가 정의되지 않은 경우에는 `printerror`에 대한 호출이 컴파일됩니다. `CREDIT` `credit` C 및 c + +에서 및는 모두 서로 다르기 때문에 고유 식별자입니다.

다음 예제의 조건부 컴파일 문은 `DLEVEL`이라는 이전에 정의된 기호화된 상수를 가정합니다.

```C
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```

첫 번째 **#if** 블록에는 중첩 된 **#if**, **#else** 및 **#endif** 지시문의 두 집합이 표시 됩니다. `DLEVEL > 5`가 true인 경우에만 지시문의 첫 번째 집합이 처리됩니다. 그렇지 않으면 **#else** 이후의 문이 처리 됩니다.

두 번째 예제의 **#elif** 및 **#else** 지시문은의 값을 기준으로 네 가지 선택 항목 중 하나를 수행 하는 데 사용 됩니다 `DLEVEL` . `STACK` 상수는 `DLEVEL`의 정의에 따라 0, 100 또는 200으로 설정됩니다. `DLEVEL`이 5보다 크면 다음 문이

```C
#elif DLEVEL > 5
display(debugptr);
```

는 컴파일되고 `STACK` 정의 되지 않습니다.

조건부 컴파일은 동일한 헤더 파일이 여러 번 포함되는 것을 방지하기 위해 일반적으로 사용됩니다. 헤더 파일에 클래스가 자주 정의 되는 c + +에서는 다음과 같은 구문을 사용 하 여 여러 정의를 방지할 수 있습니다.

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

앞의 코드에서는 기호화된 상수 `EXAMPLE_H`가 정의되어 있는지 여부를 확인합니다. 이 경우 파일이 이미 포함 되어 있으며 다시 처리할 필요가 없습니다. 정의되어 있지 않은 경우에는 `EXAMPLE_H` 상수가 이미 처리된 대로 EXAMPLE.H를 표시하도록 정의됩니다.

### <a name="__has_include"></a>__has_include

**Visual Studio 2017 버전 15.3 이상**: 라이브러리 헤더를 포함할 수 있는지 여부를 확인 합니다.

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```

## <a name="see-also"></a>참고 항목

[전처리기 지시문](../preprocessor/preprocessor-directives.md)
