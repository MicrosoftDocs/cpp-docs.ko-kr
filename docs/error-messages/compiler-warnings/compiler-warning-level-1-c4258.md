---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4258'
title: 컴파일러 경고(수준 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: 1a9bf1fdb6bded2bfad76f25c8bd1bbeadd43bf7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266210"
---
# <a name="compiler-warning-level-1-c4258"></a>컴파일러 경고(수준 1) C4258

' variable ': for 루프의 정의가 무시 됩니다. 바깥쪽 범위의 정의가 사용 됩니다. "

[/Ze](../../build/reference/za-ze-disable-language-extensions.md) 및 [/zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)에서 [for](../../cpp/for-statement-cpp.md) 루프에 정의 된 변수는 루프가 끝난 후 범위를 벗어났습니다 **`for`** . 루프 변수와 이름이 같지만 바깥쪽 루프에 정의 된 변수가 루프를 포함 하는 범위에서 다시 사용 되는 경우이 경고가 발생 합니다 **`for`** . 예를 들어:

```cpp
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```
