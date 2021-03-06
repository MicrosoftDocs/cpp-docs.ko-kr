---
description: '자세한 정보: 컴파일러 오류 C3493'
title: 컴파일러 오류 C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: 8f16a53dbaf5b9924a4874d29d560f9c089eb244
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315532"
---
# <a name="compiler-error-c3493"></a>컴파일러 오류 C3493

지정된 기본 캡처 모드가 없기 때문에 'var'을 암시적으로 캡처할 수 없습니다.

빈 람다 식 캡처 `[]`는 람다 식에서 명시적으로 또는 암시적으로 변수를 캡처하지 않도록 지정합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 기본 캡처 모드를 제공합니다. 또는

- 하나 이상의 변수를 명시적으로 캡처합니다.

## <a name="examples"></a>예제

다음 예제에서는 외부 변수를 수정하지만 빈 캡처 절을 지정하기 때문에 C3493을 생성합니다.

```cpp
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

다음 예제에서는 참조 방식을 기본 캡처 모드로 지정하여 C3493을 해결합니다.

```cpp
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
