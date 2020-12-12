---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4637'
title: 컴파일러 경고(수준 3) C4637
ms.date: 11/04/2016
f1_keywords:
- C4637
helpviewer_keywords:
- C4637
ms.assetid: 5fd347c1-2de9-408f-9136-1bf1ff273622
ms.openlocfilehash: 90a9a43ea30b35dabf18f3c300c14f8436bae4a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303896"
---
# <a name="compiler-warning-level-3-c4637"></a>컴파일러 경고(수준 3) C4637

XML 문서 주석 대상: \<include> 태그가 삭제 되었습니다.  reason

태그의 구문이 [\<include>](../../build/reference/include-visual-cpp.md) 잘못 되었습니다.

다음 샘플에서는 C4637을 생성합니다.

```cpp
// C4637.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <include file="c:\davedata\jtest\xml_include.doc"/>
   // Try the following line instead:
   // /// <include file='xml_include.doc' path='MyDocs/MyMembers/*' />
   void MyMethod() {
   }
};   // C4637
```
