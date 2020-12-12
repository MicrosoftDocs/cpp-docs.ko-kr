---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4633'
title: 컴파일러 경고(수준 3) C4633
ms.date: 11/04/2016
f1_keywords:
- C4633
helpviewer_keywords:
- C4633
ms.assetid: 6d76f268-ba8c-448b-8e83-b903a18b583b
ms.openlocfilehash: 3818d0a54f9ebc43b5686eefa73f10f9036a6373
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325948"
---
# <a name="compiler-warning-level-3-c4633"></a>컴파일러 경고(수준 3) C4633

XML 문서 주석 대상: 오류: 이유

컴파일러가 태그에 전달 하는 이름을 [\<param>](../../build/reference/param-visual-cpp.md) 찾지 못했습니다.

다음 샘플에서는 C4633를 생성 합니다.

```cpp
// C4633.cpp
// compile with: /clr /doc /LD /W3

/// Text for class MyClass.
public ref class MyClass {
   // C4633 remove line for Int3
   /// <param name="Int1">Used to indicate status.</param>
   /// <param name="Int3">Used to indicate status.</param>
   void MyMethod(int Int1) {
      Int1 = 0;
      Int1++;
   }
};
```
