---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4189'
title: 컴파일러 경고(수준 4) C4189
ms.date: 11/04/2016
f1_keywords:
- C4189
helpviewer_keywords:
- C4189
ms.assetid: 7ad9242c-228e-4054-8244-5e914b618ef3
ms.openlocfilehash: c5791325e0dc35ec501e1f4ff8593d620189ad89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173365"
---
# <a name="compiler-warning-level-4-c4189"></a>컴파일러 경고(수준 4) C4189

'identifier': 지역 변수가 초기화되었으나 참조되지 않았습니다.

변수가 선언 및 초기화되었지만 사용되지 않습니다.

다음 샘플에서는 C4189를 생성합니다.

```cpp
// C4189.cpp
// compile with: /W4
int main() {
   int a = 1;   // C4189, remove declaration to resolve
}
```
