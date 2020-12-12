---
description: '자세한 정보: 컴파일러 오류 C3496'
title: 컴파일러 오류 C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: dc3160e1007b65b70ea952aeaee3c77ba8ab21e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315519"
---
# <a name="compiler-error-c3496"></a>컴파일러 오류 C3496

'this'는 항상 값으로 캡처됩니다. '&'가 무시되었습니다.

포인터를 참조로 캡처할 수 없습니다 **`this`** .

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **`this`** 값으로 포인터를 캡처합니다.

## <a name="example"></a>예제

다음 예제에서는 포인터에 대 한 참조가 **`this`** 람다 식의 캡처 목록에 나타나기 때문에 C3496를 생성 합니다.

```cpp
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>참조

[람다 식](../../cpp/lambda-expressions-in-cpp.md)
