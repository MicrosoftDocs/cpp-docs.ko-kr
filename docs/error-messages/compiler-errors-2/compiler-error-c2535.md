---
description: '자세한 정보: 컴파일러 오류 C2535'
title: 컴파일러 오류 C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: 149ddabcde7364513379701c55d4801fd403206b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258085"
---
# <a name="compiler-error-c2535"></a>컴파일러 오류 C2535

' identifier ': 멤버 함수를 이미 정의 했거나 선언 했습니다.

이 오류는 오버 로드 된 함수의 여러 정의 또는 선언에서 동일한 형식 매개 변수 목록을 사용 하 여 발생할 수 있습니다.

Dispose 함수로 인해 C2535를 가져오는 경우 자세한 내용은 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) 를 참조 하세요.

다음 샘플에서는 C2535를 생성 합니다.

```cpp
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```
