---
description: '자세한 정보: 컴파일러 오류 C2794'
title: 컴파일러 오류 C2794
ms.date: 11/04/2016
f1_keywords:
- C2794
helpviewer_keywords:
- C2794
ms.assetid: d508191c-9044-4c6a-9119-4bca668c0b93
ms.openlocfilehash: 68f0c20e7942a32ede42fa8d7d069164d083377a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297657"
---
# <a name="compiler-error-c2794"></a>컴파일러 오류 C2794

' function ': ' class '의 직접 또는 간접 기본 클래스의 멤버가 아닙니다.

[Super](../../cpp/super.md) 를 사용 하 여 존재 하지 않는 멤버 함수를 호출 하려고 했습니다.

다음 샘플에서는 C2794를 생성 합니다.

```cpp
// C2794.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::f();  // C2794
   }
};
```
