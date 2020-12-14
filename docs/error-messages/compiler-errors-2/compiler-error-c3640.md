---
description: '자세한 정보: 컴파일러 오류 C3640'
title: 컴파일러 오류 C3640
ms.date: 11/04/2016
f1_keywords:
- C3640
helpviewer_keywords:
- C3640
ms.assetid: fcc56894-0f98-48af-8561-3bf7c7b2b93f
ms.openlocfilehash: 7f26a824cc39f2b5509c6d935a95cbc5af48aca0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239183"
---
# <a name="compiler-error-c3640"></a>컴파일러 오류 C3640

' member ': 지역 클래스의 참조 또는 가상 멤버 함수를 정의 해야 합니다.

컴파일러가 특정 함수를 정의 해야 합니다.

다음 샘플에서는 C3640를 생성 합니다.

```cpp
// C3640.cpp
void f()
{
   struct S
   {
      virtual void f1();   // C3640
      // Try the following line instead:
      // virtual void f1(){}
   };
}
```
