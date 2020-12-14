---
description: '자세한 정보: 컴파일러 오류 C2798'
title: 컴파일러 오류 C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: d3a78eaf09797d658c64b5659dcd0e05191fab1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297592"
---
# <a name="compiler-error-c2798"></a>컴파일러 오류 C2798

' super:: member '이 (가) 모호 합니다.

상속 된 여러 구조체에는 [슈퍼](../../cpp/super.md)에서 참조 하는 멤버가 포함 됩니다. 다음 중 하나를 수행 하 여 오류를 해결할 수 있습니다.

- D의 상속 목록에서 B1 또는 B2를 제거 하는 중입니다.

- B1 또는 B2의 데이터 멤버 이름 변경

다음 샘플에서는 C2798를 생성 합니다.

```cpp
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```
