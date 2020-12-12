---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4926'
title: 컴파일러 경고(수준 1) C4926
ms.date: 11/04/2016
f1_keywords:
- C4926
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
ms.openlocfilehash: 9b4f1d86085a5e0560237378728c2f267c44c780
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301895"
---
# <a name="compiler-warning-level-1-c4926"></a>컴파일러 경고(수준 1) C4926

'identifier': 기호를 이미 정의했으므로 특성이 무시됩니다.

정방향 선언이 있지만 이름이 같은 특성을 가진 구문이 이미 있습니다. 정방향 선언에 대한 특성은 무시됩니다.

다음 샘플에서는 C4926을 생성합니다.

```cpp
// C4926.cpp
// compile with: /W1
[module(name="MyLib")];

[coclass]
struct a {
};

[coclass]
struct a;   // C4926

int main() {
}
```
