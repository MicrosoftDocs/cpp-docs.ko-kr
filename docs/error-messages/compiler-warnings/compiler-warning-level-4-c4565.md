---
title: 컴파일러 경고(수준 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: ba2e1e7eb490a28626937a3911608ff9686d6f38
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195982"
---
# <a name="compiler-warning-level-4-c4565"></a>컴파일러 경고(수준 4) C4565

> '*function*': 재정의 기호가 이전에 __declspec (*한정자*)로 선언 되었습니다.

## <a name="remarks"></a>설명

기호가 다시 정의 되거나 다시 선언 되었으며, 첫 번째 정의 나 선언과 달리 두 번째 정의 또는 선언에 **`__declspec`** 한정자 (*한정자*)가 없습니다. 이 경고는 정보 제공용입니다. 이 경고를 해결 하려면 정의 중 하나를 삭제 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4565를 생성 합니다.

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
