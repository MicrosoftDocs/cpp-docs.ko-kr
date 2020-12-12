---
description: '자세한 정보: 컴파일러 오류 C2509'
title: 컴파일러 오류 C2509
ms.date: 11/04/2016
f1_keywords:
- C2509
helpviewer_keywords:
- C2509
ms.assetid: 339c1fcd-ec4a-456c-9f18-a9b24d9921af
ms.openlocfilehash: d7b6c2f05aaf525bee9572cd921d1fdffe1b0cf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212963"
---
# <a name="compiler-error-c2509"></a>컴파일러 오류 C2509

' identifier ': 멤버 함수가 ' class '에 선언 되지 않았습니다.

함수가 지정 된 클래스에 선언 되지 않았습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2509를 생성 합니다.

```cpp
// C2509.cpp
// compile with: /c
struct A {
   virtual int vfunc() = 0;
   virtual int vfunc2() = 0;
};

struct B : private A {
   using A::vfunc;
   virtual int vfunc2();
};

int B::vfunc() { return 1; }   // C2509
int B::vfunc2() { return 1; }   // OK
```
