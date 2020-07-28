---
title: 컴파일러 오류 C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: f6f20d9af424fdd4254fc15e0580d62b9dfba144
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184477"
---
# <a name="compiler-error-c3491"></a>컴파일러 오류 C3491

'var': 변경 불가능한 람다에서 값 방식 캡처를 수정할 수 없습니다.

변경할 수 없는 람다 식은 값으로 캡처되는 변수 값을 수정할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 키워드를 사용 하 여 람다 식을 선언 합니다. **`mutable`** 또는

- 람다 식의 캡처 목록에 변수를 참조로 전달합니다.

## <a name="example"></a>예제

다음 예제에서는 변경할 수 없는 람다 식의 본문에서 `m`캡처 변수를 수정하기 때문에 C3491을 생성합니다.

```cpp
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>예제

다음 예에서는 키워드를 사용 하 여 람다 식을 선언 하는 방법으로 C3491를 확인 합니다 **`mutable`** .

```cpp
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>참고 항목

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
