---
description: '자세한 정보: 컴파일러 오류 C2394'
title: 컴파일러 오류 C2394
ms.date: 11/04/2016
f1_keywords:
- C2394
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
ms.openlocfilehash: 116ab480c5a72c18bfa551e582fb797d3c216d6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194870"
---
# <a name="compiler-error-c2394"></a>컴파일러 오류 C2394

' your_type:: operator'op ' ": CLR 또는 WinRToperator이 잘못 되었습니다. 하나 이상의 매개 변수는 ' t ^ ', ' t ^% ', ' t ^& ' 형식 이어야 합니다. 여기서 T = ' your_type '

Windows 런타임 또는 관리되는 형식의 연산자는 형식이 연산자 반환 값의 형식과 동일한 매개 변수를 하나 이상 사용할 수 없습니다.

다음 샘플에서는 C2394 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2394.cpp
// compile with: /clr /c
ref struct Y {
   static Y^ operator -(int i, char c);   // C2394

   // OK
   static Y^ operator -(Y^ hY, char c);
   // or
   static Y^ operator -(int i, Y^& rhY);
};
```
