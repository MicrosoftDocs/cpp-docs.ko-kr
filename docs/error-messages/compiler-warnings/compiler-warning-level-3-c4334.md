---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4334'
title: 컴파일러 경고(수준 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 3c7a84efc3c98779c5b50dc1b3fb28e687f856eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344031"
---
# <a name="compiler-warning-level-3-c4334"></a>컴파일러 경고(수준 3) C4334

' operator ': 32 비트 시프트 결과가 64 비트로 암시적으로 변환 됩니다 (64 비트 이동 의도?).

32 비트 시프트 결과는 명시적으로 64 비트로 변환 되었으며 컴파일러는 64 비트 시프트를 의도 한 것으로 의심 합니다.  이 경고를 해결 하려면 64 비트 시프트를 사용 하거나 명시적으로 시프트 결과를 64 비트로 캐스팅 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4334를 생성 합니다.

```cpp
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```
