---
description: '자세한 정보: 컴파일러 오류 C2581'
title: 컴파일러 오류 C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: 9de6c48c2ade71af238cc62a0f92e642e1262d3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282122"
---
# <a name="compiler-error-c2581"></a>컴파일러 오류 C2581

' type ': static ' operator = ' 함수가 잘못 되었습니다.

대입 ( `=` ) 연산자가로 잘못 선언 되었습니다 **`static`** . 할당 연산자는 일 수 없습니다 **`static`** . 자세한 내용은 [사용자 정의 연산자 (c + +/cli)](../../dotnet/user-defined-operators-cpp-cli.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2581를 생성 합니다.

```cpp
// C2581.cpp
// compile with: /clr /c
ref struct Y {
   static Y ^ operator = (Y^ me, int i);   // C2581
   Y^ operator =(int i);   // OK
};
```
