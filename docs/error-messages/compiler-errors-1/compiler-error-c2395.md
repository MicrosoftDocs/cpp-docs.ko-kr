---
description: '자세한 정보: 컴파일러 오류 C2395'
title: 컴파일러 오류 C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: 86b6123646ca91945a861e9b9822076877421ac8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145472"
---
# <a name="compiler-error-c2395"></a>컴파일러 오류 C2395

'your_type::operator'op'' : CLR 또는 WinRT 연산자가 잘못되었습니다. 하나 이상의 매개 변수가 ' t ', ' t% '&, ' t ', ' t ^ ', ' t ^&% ', ' t = ' your_type ' 형식 이어야 합니다.

Windows 런타임 또는 관리되는 형식의 연산자는 형식이 연산자 반환 값의 형식과 동일한 매개 변수를 하나 이상 사용할 수 없습니다.

다음 샘플에서는 C2395를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```
