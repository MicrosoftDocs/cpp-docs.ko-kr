---
description: '자세한 정보: 컴파일러 오류 C3152'
title: 컴파일러 오류 C3152
ms.date: 11/04/2016
f1_keywords:
- C3152
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
ms.openlocfilehash: b7e98535003a03ec5ac8b06d23b105d3727ff605
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322064"
---
# <a name="compiler-error-c3152"></a>컴파일러 오류 C3152

'construct': 'keyword'은(는) 클래스, 구조체 또는 가상 멤버 함수에만 적용될 수 있습니다.

특정 키워드는 C++ 클래스에만 적용될 수 있습니다.

다음 샘플에서는 C3152를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C3152.cpp
// compile with: /clr /c
ref class C {
   int (*pfn)() sealed;   // C3152
   virtual int g() sealed;   // OK
};
```
