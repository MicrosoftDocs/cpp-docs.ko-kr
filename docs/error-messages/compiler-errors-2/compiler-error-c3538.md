---
title: 컴파일러 오류 C3538
ms.date: 11/04/2016
f1_keywords:
- C3538
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
ms.openlocfilehash: 1e1f131d551440e44e1a2ed9ed9b9c18c71eb22d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508161"
---
# <a name="compiler-error-c3538"></a>컴파일러 오류 C3538

선언자 목록에서 'auto'는 항상 동일한 형식으로 추론되어야 합니다.

선언 목록에 선언된 모든 변수가 동일한 형식으로 확인되지 않습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. **`auto`** 목록의 모든 선언이 동일한 형식으로 추론 되는지 확인 합니다.

## <a name="example"></a>예제

다음 문은 3538 오류를 생성합니다. 각 문은 여러 변수를 선언 하지만 키워드를 사용할 때마다 **`auto`** 동일한 형식으로 추론 되지 않습니다.

```cpp
// C3538.cpp
// Compile with /Zc:auto
// C3538 expected
int main()
{
// Variable x1 is a pointer to char, but y1 is a double.
   auto * x1 = "a", y1 = 3.14;
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;
// Variable x2 is an int, but y2 is a double and z is a char.
   auto x2(1), y2(0.0), z = 'a';
// Variable a is a pointer to int, but b is a pointer to double.
   auto *a = new auto(1), *b = new auto(2.0);
   return 0;
}
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-cpp.md)
