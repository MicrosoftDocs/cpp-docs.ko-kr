---
title: 컴파일러 오류 C2201
ms.date: 11/04/2016
f1_keywords:
- C2201
helpviewer_keywords:
- C2201
ms.assetid: ed927659-6e9c-447d-9963-19969ae1e957
ms.openlocfilehash: d6697de48c4868170e8c7afa287b0eb43e9523f5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501640"
---
# <a name="compiler-error-c2201"></a>컴파일러 오류 C2201

' identifier ': 내보내거나 가져오려면 외부 링크가 있어야 합니다.

내보낸 식별자는 **`static`** 입니다.

다음 샘플에서는 C2286을 생성합니다.

```cpp
// C2201.cpp
// compile with: /c
__declspec(dllexport) static void func() {}   // C2201 func() is static
__declspec(dllexport) void func2() {}   // OK
```

## <a name="see-also"></a>참고 항목

[링크 형식](../../cpp/program-and-linkage-cpp.md)
