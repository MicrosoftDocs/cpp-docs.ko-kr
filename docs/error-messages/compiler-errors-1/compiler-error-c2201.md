---
description: '자세한 정보: 컴파일러 오류 C2201'
title: 컴파일러 오류 C2201
ms.date: 11/04/2016
f1_keywords:
- C2201
helpviewer_keywords:
- C2201
ms.assetid: ed927659-6e9c-447d-9963-19969ae1e957
ms.openlocfilehash: 334a459a6fbfa930c99e3c203b1fb214cb36706a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319003"
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
