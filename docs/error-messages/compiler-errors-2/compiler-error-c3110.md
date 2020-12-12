---
description: '자세한 정보: 컴파일러 오류 C3110'
title: 컴파일러 오류 C3110
ms.date: 11/04/2016
f1_keywords:
- C3110
helpviewer_keywords:
- C3110
ms.assetid: 821dc71f-896e-4b2d-af0e-aa9932934b7b
ms.openlocfilehash: 1e402941ea88a34c48f58df56a365f74c819a8e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116056"
---
# <a name="compiler-error-c3110"></a>컴파일러 오류 C3110

' function_name ': COM 인터페이스 메서드를 오버 로드할 수 없습니다.

인터페이스 특성 (예:)이 앞에 오는 인터페이스입니다.

- [재구성](../../windows/attributes/custom-cpp.md)

- [dispinterface](../../windows/attributes/dispinterface.md)

- [복수](../../windows/attributes/dual.md)

- [object](../../windows/attributes/object-cpp.md)

를 오버 로드할 수 없습니다. 예를 들어:

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
