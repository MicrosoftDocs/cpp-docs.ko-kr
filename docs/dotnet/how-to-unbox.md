---
description: '자세한 정보: 방법: Unbox'
title: '방법: Unbox'
ms.date: 11/04/2016
helpviewer_keywords:
- unboxing
ms.assetid: 75794696-9275-47bf-9a7d-5abe6585ab91
ms.openlocfilehash: e5f3ae72f1d7b2340baa868a2e1d009b3534e701
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286321"
---
# <a name="how-to-unbox"></a>방법: Unbox

값을 unbox 하 고 수정 하는 방법을 보여 줍니다.

## <a name="example"></a>예제

```cpp
// vcmcppv2_unboxing.cpp
// compile with: /clr
using namespace System;

int main() {
   int ^ i = gcnew int(13);
   int j;
   Console::WriteLine(*i);   // unboxing
   *i = 14;   // unboxing and assignment
   Console::WriteLine(*i);
   j = safe_cast<int>(i);   // unboxing and assignment
   Console::WriteLine(j);
}
```

```Output
13
14
14
```

## <a name="see-also"></a>참고 항목

[boxing](../extensions/boxing-cpp-component-extensions.md)
