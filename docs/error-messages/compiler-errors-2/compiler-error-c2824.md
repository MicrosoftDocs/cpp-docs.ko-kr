---
description: '자세한 정보: 컴파일러 오류 C2824'
title: 컴파일러 오류 C2824
ms.date: 11/04/2016
f1_keywords:
- C2824
helpviewer_keywords:
- C2824
ms.assetid: 5bd865f7-e0af-404e-80fe-e2b798b44a59
ms.openlocfilehash: cb6f7f86647a465cb0b525bc0da8f2d452661af8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194685"
---
# <a name="compiler-error-c2824"></a>컴파일러 오류 C2824

' operator n e w '의 반환 형식은 ' void * ' 여야 합니다.

기반이 아닌 포인터를 사용 하는 경우 연산자의 오버 로드는를 `new` 반환 해야 `void *` 합니다.

다음 샘플에서는 C2824를 생성 합니다.

```cpp
// C2824.cpp
// compile with: /c
class   A {
   A* operator new(size_t i, char *m);   // C2824
   // try the following line instead
   // void* operator new(size_t i, char *m);
};
```
