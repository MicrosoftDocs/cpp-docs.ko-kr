---
description: '자세히 알아보기: 방법: 포인터 및 배열 고정'
title: '방법: 포인터 및 배열 고정'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: ab0e09e94c45cc31862ef8d0b6c0771bfeae115d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119137"
---
# <a name="how-to-pin-pointers-and-arrays"></a>방법: 포인터 및 배열 고정

관리되는 개체에 정의된 하위 개체를 고정하면 전체 개체를 고정하는 효과가 있습니다.  예를 들어, 모든 배열 요소가 고정되어 있는 경우 전체 배열도 고정됩니다. 고정된 배열을 선언하기 위한 언어 확장은 없습니다. 배열을 고정하려면 해당 요소 형식에 대한 고정 포인터를 선언하고 이러한 요소 중 하나를 고정합니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>참조

[pin_ptr (c + +/CLI)](pin-ptr-cpp-cli.md)
