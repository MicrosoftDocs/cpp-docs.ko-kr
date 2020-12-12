---
description: '자세한 정보: 컴파일러 오류 C3280'
title: 컴파일러 오류 C3280
ms.date: 11/04/2016
f1_keywords:
- C3280
helpviewer_keywords:
- C3280
ms.assetid: 86dc5bbc-8818-4786-a728-9334268d308b
ms.openlocfilehash: f85731b20e98088fdfd8e894a942ce8d16b553bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194178"
---
# <a name="compiler-error-c3280"></a>컴파일러 오류 C3280

'class': 관리되는 형식의 멤버-함수는 관리되지 않는 함수로 컴파일할 수 없습니다.

관리되는 클래스 멤버 함수를 관리되지 않는 함수로 컴파일할 수 없습니다.

다음 샘플에서는 C3280을 생성합니다.

```cpp
// C3280_2.cpp
// compile with: /clr
ref struct A {
   void func();
};

#pragma managed(push,off)

void A::func()   // C3280
{
}

#pragma managed(pop)
```
