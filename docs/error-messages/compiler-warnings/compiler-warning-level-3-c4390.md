---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4390'
title: 컴파일러 경고(수준 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 8067d4beae44e098085122968a227f6ff8bc8b4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160443"
---
# <a name="compiler-warning-level-3-c4390"></a>컴파일러 경고(수준 3) C4390

'; ': 제어 되는 빈 문이 있습니다. 이것이 의도 입니까?

명령이 없는 control 문 뒤에 세미콜론이 있습니다.

매크로 때문에 C4390를 가져오는 경우 매크로를 포함 하는 모듈에서 C4390를 사용 하지 않도록 설정 하려면 [warning](../../preprocessor/warning.md) pragma를 사용 해야 합니다.

다음 샘플에서는 C4390를 생성 합니다.

```cpp
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```
