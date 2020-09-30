---
title: 컴파일러 오류 C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 4537c6c76814f2aeb8f8d62579caec86785de252
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510140"
---
# <a name="compiler-error-c3531"></a>컴파일러 오류 C3531

' symbol ': 형식에 ' auto '가 포함 된 기호에는 이니셜라이저가 있어야 합니다.

지정 된 변수에 이니셜라이저 식이 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 변수를 선언할 때 등호 (=)를 사용 하는 단순 할당과 같은 이니셜라이저 식을 지정 합니다.

## <a name="example"></a>예제

다음 예에서는, 및 변수가 초기화 되지 않으므로 C3531을 생성 `x1` `y1, y2, y3` `z2` 합니다.

```cpp
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-cpp.md)
