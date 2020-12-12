---
description: '자세히 알아보기: volatile (c + +)'
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: cb7bda39ded03342b03ed889125992960210b940
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213340"
---
# <a name="volatile-c"></a>volatile (C++)

하드웨어에 의해 프로그램에서 수정할 수 있는 개체를 선언하는 데 사용할 수 있는 형식 한정자입니다.

## <a name="syntax"></a>구문

```
volatile declarator ;
```

## <a name="remarks"></a>설명

[/Volatile](../build/reference/volatile-volatile-keyword-interpretation.md) 컴파일러 스위치를 사용 하 여 컴파일러가이 키워드를 해석 하는 방법을 수정할 수 있습니다.

Visual Studio는 **`volatile`** 대상 아키텍처에 따라 키워드를 다르게 해석 합니다. ARM의 경우 **/volatile** 컴파일러 옵션이 지정 되지 않은 경우 컴파일러는 **/volatile: iso** 가 지정 된 것 처럼 수행 됩니다. ARM이 아닌 아키텍처의 경우 **/volatile** 컴파일러 옵션을 지정 하지 않으면 컴파일러가 **/volatile: ms** 가 지정 된 것 처럼 수행 됩니다. 따라서 ARM 이외의 아키텍처에서는 **/volatile: iso** 를 지정 하 고 스레드 간에 공유 되는 메모리를 처리할 때 명시적인 동기화 기본 형식 및 컴파일러 내장 함수를 사용 하는 것이 좋습니다.

한정자를 사용 하 여 **`volatile`** 인터럽트 처리기와 같은 비동기 프로세스에서 사용 하는 메모리 위치에 대 한 액세스를 제공할 수 있습니다.

**`volatile`** 가 [__restrict](../cpp/extension-restrict.md) 키워드가 있는 변수에 사용 되는 경우이 **`volatile`** 우선적으로 적용 됩니다.

**`struct`** 멤버가로 표시 되 면 **`volatile`** **`volatile`** 이 전체 구조체로 전파 됩니다. 구조체에 한 가지 명령을 사용 하 여 현재 아키텍처에서 복사할 수 있는 길이가 없으면가 **`volatile`** 해당 구조에서 완전히 손실 될 수 있습니다.

**`volatile`** 다음 조건 중 하나에 해당 하는 경우 키워드는 필드에 영향을 주지 않을 수 있습니다.

- volatile 필드의 길이가 현재 아키텍처에서 하나의 명령을 사용하여 복사할 수 있는 최대 크기를 초과합니다.

- 포함 된 가장 바깥쪽의 길이 **`struct`** 또는 중첩 될 수 있는 멤버의 경우 **`struct`** 한 명령을 사용 하 여 현재 아키텍처에서 복사할 수 있는 최대 크기를 초과 합니다.

프로세서에서 캐시할 수 없는 메모리 액세스의 순서를 변경 하지 않지만 **`volatile`** 컴파일러에서 메모리 액세스의 순서를 변경 하지 않도록 캐시할 수 없는 변수를로 표시 해야 합니다.

로 선언 된 개체는 **`volatile`** 해당 값이 언제 든 지 변경 될 수 있기 때문에 특정 최적화에 사용 되지 않습니다.  이전 명령이 동일한 개체의 값을 요청 하는 경우에도 시스템은 요청 시 일시적 개체의 현재 값을 항상 읽습니다.  또한 개체의 값은 할당에 즉시 기록 됩니다.

## <a name="iso-compliant"></a>ISO 규격

C # Volatile 키워드를 알고 있거나 **`volatile`** 이전 버전의 Microsoft c + + 컴파일러 (MSVC)에서의 동작에 익숙한 경우 c + + 11 Iso 표준 **`volatile`** 키워드는 서로 다르며 [/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md) 컴파일러 옵션이 지정 된 경우 MSVC에서 지원 됩니다. ARM의 경우 기본적으로 지정됩니다. **`volatile`** C + + 11 ISO 표준 코드의 키워드는 하드웨어 액세스에만 사용 되며 스레드 간 통신에는 사용 하지 않습니다. 스레드 간 통신의 경우 [c + + 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)에서 [std:: \<T> atomic](../standard-library/atomic.md) 와 같은 메커니즘을 사용 합니다.

## <a name="end-of-iso-compliant"></a>ISO 규격의 끝

**Microsoft 전용**

**/Volatile: ms** 컴파일러 옵션을 사용 하는 경우 (기본적으로 ARM 이외의 아키텍처가 대상으로 지정 된 경우) 컴파일러는 다른 전역 개체에 대 한 참조 순서를 유지 하는 것 외에도 휘발성 개체에 대 한 참조 간의 순서를 유지 하기 위해 추가 코드를 생성 합니다. 특히 다음 사항에 주의하십시오.

- volatile 개체 쓰기(volatile 쓰기)는 Release 의미 체계를 사용합니다. 즉 명령 시퀀스에서 volatile 개체에 쓰기 전에 발생하는 전역 또는 정적 개체에 대한 참조는 컴파일된 이진 파일에서 volatile 쓰기 전에 발생합니다.

- volatile 개체 읽기(volatile 읽기)는 Acquire 의미 체계를 사용합니다. 즉 명령 시퀀스에서 volatile 메모리 읽기 다음에 발생하는 전역 또는 정적 개체에 대한 참조는 컴파일된 이진 파일에서 volatile 읽기 다음에 발생합니다.

이렇게 하면 다중 스레드 응용 프로그램의 메모리 잠금 및 릴리스에 대해 일시적 개체를 사용할 수 있습니다.

> [!NOTE]
> **/Volatile: ms** 컴파일러 옵션을 사용할 때 제공 되는 향상 된 보증에 의존 하는 경우 코드는 이식 가능 하지 않습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[키워드](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[const 및 volatile 포인터](../cpp/const-and-volatile-pointers.md)
