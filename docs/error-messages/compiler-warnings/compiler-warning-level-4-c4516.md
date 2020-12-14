---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4516'
title: 컴파일러 경고(수준 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 945cf057b030a032afc2dd6dd3084df482f8a9a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241211"
---
# <a name="compiler-warning-level-4-c4516"></a>컴파일러 경고(수준 4) C4516

' class:: symbol ': 액세스 선언은 사용 되지 않습니다. 멤버를 사용 하는 것이 더 나은 대안을 제공 합니다.

ANSI c + + 위원회는 액세스 선언 ( [using](../../cpp/using-declaration.md) 키워드 없이 파생 된 클래스의 멤버 액세스를 변경 함)을 오래 된 것으로 선언 했습니다. 이후 버전의 c + +에서는 액세스 선언이 지원 되지 않을 수 있습니다.

다음 샘플에서는 C4516를 생성 합니다.

```cpp
// C4516.cpp
// compile with: /W4
class A
{
public:
   void x(char);
};

class B : protected A
{
public:
   A::x;  // C4516 on access-declaration
   // use the following line instead
   // using A::x; // using-declaration, ok
};

int main()
{
}
```
