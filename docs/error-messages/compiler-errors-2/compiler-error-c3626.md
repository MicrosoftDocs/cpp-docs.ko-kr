---
description: '자세한 정보: 컴파일러 오류 C3626'
title: 컴파일러 오류 C3626
ms.date: 11/04/2016
f1_keywords:
- C3626
helpviewer_keywords:
- C3626
ms.assetid: 43926e2b-1ba9-4a43-9343-c58449cbb336
ms.openlocfilehash: 8db976a5f072db618ac4270df3bd1d8edf0ab15c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144419"
---
# <a name="compiler-error-c3626"></a>컴파일러 오류 C3626

' keyword ': ' __event ' 키워드는 대리자에 대 한 포인터인 COM 인터페이스, 멤버 함수 및 데이터 멤버에만 사용할 수 있습니다.

키워드를 잘못 사용 했습니다.

다음 샘플에서는 C3626를 생성 합니다.

```cpp
// C3626.cpp
// compile with: /c
struct A {
   __event int i;   // C3626
// try the following line instead
// __event int i();
};
```
