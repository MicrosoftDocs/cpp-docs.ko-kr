---
description: '자세한 정보: 컴파일러 오류 C3611'
title: 컴파일러 오류 C3611
ms.date: 11/04/2016
f1_keywords:
- C3611
helpviewer_keywords:
- C3611
ms.assetid: 42f3e320-41de-420a-bd05-8924cab765aa
ms.openlocfilehash: 9c18e8e757e3962af1f2e0fbcc0d33384f3b6329
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262297"
---
# <a name="compiler-error-c3611"></a>컴파일러 오류 C3611

' function ': 봉인 된 함수에는 순수 지정자를 사용할 수 없습니다.

Sealed 함수가 잘못 선언 되었습니다.  자세한 내용은 [sealed](../../extensions/sealed-cpp-component-extensions.md)를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3611를 생성 합니다.

```cpp
// C3611.cpp
// compile with: /clr /c

ref struct V {
   virtual void Test() sealed = 0;   // C3611
   virtual void Test2() sealed;   // OK
   virtual void Test3() = 0;   // OK
};
```
