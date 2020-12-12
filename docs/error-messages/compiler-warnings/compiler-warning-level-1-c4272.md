---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4272'
title: 컴파일러 경고(수준 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: a44e3a4121c1d01b15af47b0b4eefb1f982423bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266119"
---
# <a name="compiler-warning-level-1-c4272"></a>컴파일러 경고(수준 1) C4272

' function ': __declspec (dllimport)로 표시 되어 있습니다. 함수를 가져올 때 네이티브 호출 규칙을 지정 해야 합니다.

[__Clrcall](../../cpp/clrcall.md) 호출 규칙으로 표시 된 함수를 내보내는 것은 오류 이며로 표시 된 함수를 가져오려고 하면 컴파일러가이 경고를 발생 시킵니다 `__clrcall` .

다음 샘플에서는 C4272를 생성 합니다.

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```
