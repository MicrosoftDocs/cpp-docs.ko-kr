---
description: '자세한 정보: 컴파일러 오류 C3387'
title: 컴파일러 오류 C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: febd47004026a7e22ca576c153ee8cf1506c3e1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285554"
---
# <a name="compiler-error-c3387"></a>컴파일러 오류 C3387

' member ': __declspec (dllexport)/ \_ _declspec (dllimport)을 (를) 관리 되는 형식 또는 WinRT 형식의 멤버에 적용할 수 없습니다.

`dllimport` [](../../cpp/dllexport-dllimport.md) **`__declspec`** 관리 되는 형식 또는 Windows 런타임 형식의 멤버에는 및 dllexport 한정자를 사용할 수 없습니다.

다음 샘플에서는 C3387 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```
