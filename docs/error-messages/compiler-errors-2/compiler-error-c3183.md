---
description: '자세한 정보: 컴파일러 오류 C3183'
title: 컴파일러 오류 C3183
ms.date: 11/04/2016
f1_keywords:
- C3183
helpviewer_keywords:
- C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
ms.openlocfilehash: 1a2b761af05ec9285e4222a874e1641466106c9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174106"
---
# <a name="compiler-error-c3183"></a>컴파일러 오류 C3183

WinRT 또는 관리되는 형식 'type' 내부에 명명되지 않은 클래스, 구조체 또는 공용 구조체를 정의할 수 없습니다.

WinRT 또는 관리되는 형식에 포함된 형식의 이름을 지정해야 합니다.

다음 샘플에서는 C3183 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3183a.cpp
// compile with: /clr /c
ref class Test
{
   ref class
   {  // C3183, delete class or name it
      int a;
      int b;
   };
};
```
