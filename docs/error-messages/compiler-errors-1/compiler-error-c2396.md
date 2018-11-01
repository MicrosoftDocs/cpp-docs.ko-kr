---
title: 컴파일러 오류 C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438091"
---
# <a name="compiler-error-c2396"></a>컴파일러 오류 C2396

' your_type:: operator'type ': CLR 또는 WinRT 사용자 정의 변환 functionnot를 유효 합니다. 다음에서 변환되거나 다음으로 변환해야 합니다. 'T^', 'T^%', 'T^&'(T = 'your_type')

Windows 런타임 또는 관리되는 형식의 변환 함수에 해당 형식이 변환 함수를 포함하는 형식과 동일한 매개 변수가 하나 이상 없습니다.

다음 샘플에서는 C2396을 생성하고 해결 방법을 보여 줍니다.

```
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```