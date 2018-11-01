---
title: 컴파일러 오류 C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: ec0018fc1aafc7e3e0423608f4db9f78946e4597
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432641"
---
# <a name="compiler-error-c3482"></a>컴파일러 오류 C3482

비정적 멤버 함수 내에서는 'this'는 람다 캡처로만 사용할 수 있습니다.

`this` 를 정적 메서드 또는 전역 함수에서 선언된 람다 식의 캡처 목록에 전달할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 바깥쪽 함수를 비정적 메서드로 변환하거나

- 람다 식의 캡처 목록에서 `this` 포인터를 제거합니다.

## <a name="example"></a>예제

다음 예제에서는 C3482를 생성합니다.

```
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>참고 항목

[람다 식](../../cpp/lambda-expressions-in-cpp.md)