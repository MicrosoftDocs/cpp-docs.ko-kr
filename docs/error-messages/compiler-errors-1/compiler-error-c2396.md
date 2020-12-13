---
description: '자세한 정보: 컴파일러 오류 C2396'
title: 컴파일러 오류 C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: 654b812fbd152a6effb60e6f0919f99bf5039a1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145394"
---
# <a name="compiler-error-c2396"></a>컴파일러 오류 C2396

' your_type:: operator'type ' ': CLR 또는 WinRT 사용자 정의 변환이 잘못 되었습니다. From 또는 convert에서 ' t ^ ', ' t ^% ', ' t ^& ' (여기서 T = ' your_type ')로 변환 해야 합니다.

Windows 런타임 또는 관리되는 형식의 변환 함수에 해당 형식이 변환 함수를 포함하는 형식과 동일한 매개 변수가 하나 이상 없습니다.

다음 샘플에서는 C2396을 생성하고 해결 방법을 보여 줍니다.

```cpp
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
