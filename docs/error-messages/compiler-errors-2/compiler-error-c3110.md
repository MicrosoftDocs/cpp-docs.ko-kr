---
title: 컴파일러 오류 C3110
ms.date: 11/04/2016
f1_keywords:
- C3110
helpviewer_keywords:
- C3110
ms.assetid: 821dc71f-896e-4b2d-af0e-aa9932934b7b
ms.openlocfilehash: 9eb3e54b8bd9b296ad9cd7e0b6ea2943c74d1dff
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498488"
---
# <a name="compiler-error-c3110"></a>컴파일러 오류 C3110

' function_name ': COM 인터페이스 메서드를 오버 로드할 수 없습니다.

인터페이스 특성 (예:)이 앞에 오는 인터페이스입니다.

- [재구성](../../windows/attributes/custom-cpp.md)

- [dispinterface](../../windows/attributes/dispinterface.md)

- [dual](../../windows/attributes/dual.md)

- [object](../../windows/attributes/object-cpp.md)

를 오버 로드할 수 없습니다. 다음은 그 예입니다.

```cpp
// C3110.cpp
#include <unknwn.h>
[ object, uuid= "4F98A180-EF37-11D1-978D-0000F805D73B" ]
__interface ITestInterface
{
   HRESULT mf1(void);
   HRESULT mf1(BSTR); // C3110
};

int main()
{
}
```
