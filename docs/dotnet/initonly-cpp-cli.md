---
description: '자세히 알아보기: initonly (c + +/CLI)'
title: initonly(C++/CLI)
ms.date: 11/04/2016
f1_keywords:
- initonly_cpp
- initonly
helpviewer_keywords:
- initonly attribute [C++]
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
ms.openlocfilehash: 186f8f18a3c5ff7ee963b19801a23e9dd82e50a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316650"
---
# <a name="initonly-ccli"></a>initonly(C++/CLI)

**initonly** 는 동일한 클래스의 정적 생성자 또는 선언의 일부로만 변수 할당이 발생할 수 있음을 나타내는 상황에 맞는 키워드입니다.

다음 예제에서는 `initionly`을 사용하는 방법을 보여 줍니다.

```cpp
// mcpp_initonly.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst1;

   initonly
   static int staticConst2 = 0;

   static Y1() {
      staticConst1 = 0;
   }
};
```

## <a name="see-also"></a>참조

[클래스 및 구조체](../extensions/classes-and-structs-cpp-component-extensions.md)
