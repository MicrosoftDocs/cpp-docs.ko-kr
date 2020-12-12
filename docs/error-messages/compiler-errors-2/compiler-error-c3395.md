---
description: '자세한 정보: 컴파일러 오류 C3395'
title: 컴파일러 오류 C3395
ms.date: 11/04/2016
f1_keywords:
- C3395
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
ms.openlocfilehash: 65db71a9dbc076b21d16f3f0c250c20a9b283daa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321971"
---
# <a name="compiler-error-c3395"></a>컴파일러 오류 C3395

' function ': __declspec (dllexport)을 (를) 호출 규칙을 _clrcall 사용 하는 함수에 적용할 수 없습니다. \_

`__declspec(dllexport)` 및 [__clrcall](../../cpp/clrcall.md) 호환 되지 않습니다.  자세한 내용은 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)를 참조하세요.

다음 샘플에서는 C3395를 생성 합니다.

```cpp
// C3395.cpp
// compile with: /clr /c

__declspec(dllexport) void __clrcall Test(){}   // C3395
void __clrcall Test2(){}   // OK
__declspec(dllexport) void Test3(){}   // OK
```
