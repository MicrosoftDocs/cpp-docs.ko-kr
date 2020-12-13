---
description: '자세한 정보: 컴파일러 오류 C2524'
title: 컴파일러 오류 C2524
ms.date: 11/04/2016
f1_keywords:
- C2524
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
ms.openlocfilehash: 94e974674a5e244168499a50304a07264d23e618
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151140"
---
# <a name="compiler-error-c2524"></a>컴파일러 오류 C2524

' 소멸자 ': 소멸자/종료자에는 ' void ' 매개 변수 목록이 있어야 합니다.

소멸자 또는 종료자에 [void](../../cpp/void-cpp.md)가 아닌 매개 변수 목록이 있습니다. 다른 매개 변수 형식은 허용 되지 않습니다.

## <a name="examples"></a>예제

재현 C2524 코드는 다음과 같습니다.

```cpp
// C2524.cpp
// compile with: /c
class A {
   A() {}
   ~A(int i) {}    // C2524
   // try the following line instead
   // ~A() {}
};
```

재현 C2524 코드는 다음과 같습니다.

```cpp
// C2524_b.cpp
// compile with: /clr /c
ref struct I1 {
protected:
   !I1(int i);   // C2524
   // try the following line instead
   // !I1();
};
```
