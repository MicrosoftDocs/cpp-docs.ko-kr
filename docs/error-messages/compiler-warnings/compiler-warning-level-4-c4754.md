---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4754'
title: 컴파일러 경고(수준 4) C4754
ms.date: 11/04/2016
f1_keywords:
- C4754
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
ms.openlocfilehash: b997f81a7d922837ff3f1ea2e5d015e5267428dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330517"
---
# <a name="compiler-warning-level-4-c4754"></a>컴파일러 경고(수준 4) C4754

비교에 포함된 산술 연산에 대한 변환 규칙은 하나의 분기를 실행할 수 없음을 의미합니다.

비교 결과가 항상 동일하기 때문에 C4754 경고가 발생합니다. 이는 연결된 정수 식이 올바르지 않기 때문에 조건 분기 중 하나가 결코 실행되지 않음을 나타냅니다. 이러한 코드 감지는 64비트 아키텍처에서 잘못된 정수 오버플로 검사 시에 자주 발생합니다.

정수 변환 규칙은 복잡하고 많은 미묘한 문제가 있습니다. 각 C4754 경고를 수정 하는 대신 [SafeInt 라이브러리](../../safeint/safeint-library.md)를 사용 하도록 코드를 업데이트할 수 있습니다.

## <a name="examples"></a>예제

이 샘플에서는 C4754를 생성 합니다.

```cpp
// C4754a.cpp
// Compile with: /W4 /c
#include "errno.h"

int sum_overflow(unsigned long a, unsigned long b)
{
   unsigned long long x = a + b; // C4754

   if (x > 0xFFFFFFFF)
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

`a + b` 식은 결과가 64비트 값으로 업캐스팅되고 64비트 변수 `x`에 할당되기 전에 산술 오버플로를 일으킬 수 있습니다. 즉, `x`에 대한 검사가 중복되고 오버플로가 catch되지 않습니다. 이 경우 컴파일러가 다음 경고를 내보냅니다.

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).
```

이 경고를 없애려면 피연산자를 8바이트 값으로 캐스팅하도록 할당 문을 변경하면 됩니다.

```cpp
// Casting one operand is sufficient to force all the operands in
// the addition be upcast according to C/C++ conversion rules, but
// casting both is clearer.
unsigned long long x =
   (unsigned long long)a + (unsigned long long)b;
```

다음 샘플도 C4754를 생성합니다.

```cpp
// C4754b.cpp
// Compile with: /W4 /c
#include "errno.h"

int wrap_overflow(unsigned long a)
{
   if (a + sizeof(unsigned long) < a) // C4754
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

`sizeof()` 연산자는 크기가 아키텍처에 따라 달라지는 `size_t`를 반환합니다. 예제 코드는 `size_t`가 32비트 형식인 32비트 아키텍처에서 작동합니다. 하지만 64비트 아키텍처의 경우에는 `size_t`가 64비트 형식입니다. 정수 변환 규칙은 `a`가 `a + b < a`로 작성된 것처럼 `(size_t)a + (size_t)b < (size_t)a` 식에서 64비트 값으로 업캐스팅됩니다. `a` 및 `b`가 32비트 정수이면 64비트 더하기 식이 오버플로되지 않으며, 제약 조건이 적용되지 않습니다. 따라서 64비트 아키텍처에서는 코드에서 정수 오버플로 조건이 검색되지 않습니다. 이 예제에서는 컴파일러가 다음 경고를 내보내도록 만듭니다.

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).
```

경고 메시지는 원래의 소스 문자열 대신 상수 값 4를 명시적으로 나열합니다. 경고 분석 시 잘못된 코드가 발견될 때는 `sizeof(unsigned long)`가 이미 상수로 변환된 상태입니다. 따라서 소스 코드에서 경고 메시지의 상수 값과 연관된 식을 추적해야 할 수 있습니다. C4754 경고 메시지에서 상수로 분석되는 가장 일반적인 코드의 소스는 `sizeof(TYPE)` 및 `strlen(szConstantString)`과 같은 식입니다.

여기에서 수정된 코드는 다음과 같습니다.

```cpp
// Casting the result of sizeof() to unsigned long ensures
// that all the addition operands are 32-bit, so any overflow
// is detected by the check.
if (a + (unsigned long)sizeof(unsigned long) < a)
```

**참고** 컴파일러 경고에서 참조 되는 줄 번호는 문의 마지막 줄입니다. 여러 줄에 걸쳐 있는 복잡한 조건 문에 대한 경고 메시지에서, 코드 결함을 포함하는 줄은 보고된 줄 이전의 여러 줄일 수 있습니다. 예를 들어:

```cpp
unsigned long a;

if (a + sizeof(unsigned long) < a || // incorrect check
    condition1() ||
    a == 0) {    // C4754 warning reported on this line
         // never executes!
         return INVALID_PARAMETER;
}
```
