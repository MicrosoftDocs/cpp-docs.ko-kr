---
description: '자세한 정보: 컴파일러 경고 (수준 2) C4150'
title: 컴파일러 경고 (수준 2) C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: 9b0296b94bbb2aab18b579898f053e002397c04e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177252"
---
# <a name="compiler-warning-level-2-c4150"></a>컴파일러 경고 (수준 2) C4150

불완전 한 ' type ' 형식에 대 한 포인터를 삭제 합니다. 소멸자를 호출 하지 않았습니다.

**`delete`** 선언 되었지만 정의 되지 않은 형식을 삭제 하기 위해 연산자가 호출 되므로 컴파일러가 소멸자를 찾을 수 없습니다.

다음 샘플에서는 C4150를 생성 합니다.

```cpp
// C4150.cpp
// compile with: /W2
class  IncClass;

void NoDestruct( IncClass* pIncClass )
{
   delete pIncClass;
} // C4150, define class to resolve

int main()
{
}
```
