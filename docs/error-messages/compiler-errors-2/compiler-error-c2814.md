---
description: '자세한 정보: 컴파일러 오류 C2814'
title: 컴파일러 오류 C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 3da888c70356abee8ae18990d521d5589a5c5069
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278391"
---
# <a name="compiler-error-c2814"></a>컴파일러 오류 C2814

'member' : 네이티브 형식은 관리되는 형식 또는 WinRT 형식 'type' 내부에 중첩될 수 없습니다.

## <a name="example"></a>예제

네이티브 형식은 CLR 또는 WinRT 형식에 중첩할 수 없습니다. 다음 샘플에서는 C2814 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
