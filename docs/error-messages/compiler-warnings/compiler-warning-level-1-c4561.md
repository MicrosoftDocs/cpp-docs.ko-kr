---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4561'
title: 컴파일러 경고(수준 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: fc94879039f72bba0734240bc26d152965d6b650
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337291"
---
# <a name="compiler-warning-level-1-c4561"></a>컴파일러 경고(수준 1) C4561

' __fastcall '이 (가) '/clr ' 옵션과 호환 되지 않습니다. ' _stdcall ' (으)로 변환 합니다. \_

[__Fastcall](../../cpp/fastcall.md) 함수 호출 규칙은 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 컴파일러 옵션과 함께 사용할 수 없습니다. 컴파일러는에 대 한 호출을 무시 합니다 **`__fastcall`** . 이 경고를 해결 하려면에 대 한 호출을 제거 **`__fastcall`** 하거나 **/clr** 을 사용 하지 않고 컴파일합니다.

다음 샘플에서는 C4561를 생성 합니다.

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```
