---
title: initonly(C++/CLI)
ms.date: 11/04/2016
f1_keywords:
- initonly_cpp
- initonly
helpviewer_keywords:
- initonly attribute [C++]
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
ms.openlocfilehash: 970800968733a285929c3bfa42594360203e573a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545170"
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

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../extensions/classes-and-structs-cpp-component-extensions.md)
