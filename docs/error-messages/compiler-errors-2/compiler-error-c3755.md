---
description: '자세한 정보: 컴파일러 오류 C3755'
title: 컴파일러 오류 C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 24d6af223b6a15cbf1740bf67144250007c2091d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253587"
---
# <a name="compiler-error-c3755"></a>컴파일러 오류 C3755

' delegate ': 대리자를 정의할 수 없습니다.

[대리자 (c + + 구성 요소 확장)](../../extensions/delegate-cpp-component-extensions.md) 를 선언할 수는 있지만 정의할 수는 없습니다.

## <a name="examples"></a>예제

다음 샘플에서는 C3755를 생성 합니다.

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

C3755는 대리자 템플릿을 만들려고 할 때에도 발생할 수 있습니다. 다음 샘플에서는 C3755를 생성 합니다.

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
