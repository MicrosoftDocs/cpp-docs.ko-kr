---
description: '자세한 정보: 컴파일러 오류 C2669'
title: 컴파일러 오류 C2669
ms.date: 11/04/2016
f1_keywords:
- C2669
helpviewer_keywords:
- C2669
ms.assetid: f9cb8111-bcdc-484b-a863-2c42e15a0496
ms.openlocfilehash: 01b40131a2eef4ff83d10c5088b2cae3eb7e55e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210649"
---
# <a name="compiler-error-c2669"></a>컴파일러 오류 C2669

익명 공용 구조체에는 멤버 함수를 사용할 수 없습니다.

[익명 공용 구조체](../../cpp/unions.md#anonymous_unions) 에는 멤버 함수를 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2669를 생성 합니다.

```cpp
// C2669.cpp
struct X {
   union {
      int i;
      void f() {   // C2669, remove function
         i = 0;
      }
   };
};
```
