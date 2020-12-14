---
description: '자세한 정보: 컴파일러 오류 C3923'
title: 컴파일러 오류 C3923
ms.date: 11/04/2016
f1_keywords:
- C3923
helpviewer_keywords:
- C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
ms.openlocfilehash: 261ff6d5a3d7f6a246d906b1d91809d8764ca2bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220697"
---
# <a name="compiler-error-c3923"></a>컴파일러 오류 C3923

'member': WinRT 또는 관리되는 클래스의 멤버 함수에는 지역 클래스, 구조체 또는 공용 구조체 정의를 사용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3923 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3923.cpp
// compile with: /clr /c
ref struct x {
   void Test() {
      struct a {};   // C3923
      class b {};   // C3923
      union c {};   // C3923
   }
};
```
