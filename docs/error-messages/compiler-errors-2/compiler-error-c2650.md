---
description: '자세한 정보: 컴파일러 오류 C2650'
title: 컴파일러 오류 C2650
ms.date: 11/04/2016
f1_keywords:
- C2650
helpviewer_keywords:
- C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
ms.openlocfilehash: 161b4a78f200a2fd6ca60d47c76b433624d2e1f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174548"
---
# <a name="compiler-error-c2650"></a>컴파일러 오류 C2650

' operator ': 가상 함수 일 수 없습니다.

**`new`** 또는 **`delete`** 연산자가 선언 되었습니다 **`virtual`** . 이러한 연산자는 **`static`** 멤버 함수 이며 일 수 없습니다 **`virtual`** .

## <a name="example"></a>예제

다음 샘플에서는 C2650를 생성 합니다.

```cpp
// C2650.cpp
// compile with: /c
class A {
   virtual void* operator new( unsigned int );   // C2650
   // try the following line instead
   // void* operator new( unsigned int );
};
```
