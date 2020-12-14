---
description: '자세한 정보: 컴파일러 오류 C2790'
title: 컴파일러 오류 C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: 0913b87f40e7f4ad2ecccb333e67bb0d76b4afde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297805"
---
# <a name="compiler-error-c2790"></a>컴파일러 오류 C2790

' super ':이 키워드는 클래스 멤버 함수의 본문 내 에서만 사용할 수 있습니다.

이 오류 메시지는 사용자가 멤버 함수의 [컨텍스트 외부에서](../../cpp/super.md) 키워드를 사용 하려고 할 때 나타납니다.

다음 샘플에서는 C2790를 생성 합니다.

```cpp
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```
