---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4238'
title: 컴파일러 경고(수준 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: 8999d9ebeb4583256360f6223d4bf51a842fcb01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334876"
---
# <a name="compiler-warning-level-4-c4238"></a>컴파일러 경고(수준 4) C4238

비표준 확장이 사용 됨: 클래스 rvalue가 lvalue로 사용 되었습니다.

이전 버전의 Visual C++와의 호환성을 위해 Microsoft 확장 (**/ze**)을 사용 하면 해당 주소를 암시적으로 또는 명시적으로 사용 하는 컨텍스트에서 클래스 형식을 rvalue로 사용할 수 있습니다. 아래 예제와 같은 일부 경우에는 위험할 수 있습니다.

## <a name="example"></a>예제

```cpp
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

이를 사용 하면 ANSI 호환성 ([/za](../../build/reference/za-ze-disable-language-extensions.md))에서 오류가 발생 합니다.
