---
description: '자세한 정보: 컴파일러 오류 C2791'
title: 컴파일러 오류 C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: 0f5bd93c1c6ee32399da793147a18e9225b5fcb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297774"
---
# <a name="compiler-error-c2791"></a>컴파일러 오류 C2791

' super '를 잘못 사용 했습니다. ' class '에 기본 클래스가 없습니다.

[슈퍼](../../cpp/super.md) 키워드는 기본 클래스가 없는 클래스의 멤버 함수 컨텍스트 내에서 사용 되었습니다.

다음 샘플에서는 C2791를 생성 합니다.

```cpp
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```
