---
description: '자세한 정보: 컴파일러 오류 C3269'
title: 컴파일러 오류 C3269
ms.date: 11/04/2016
f1_keywords:
- C3269
helpviewer_keywords:
- C3269
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
ms.openlocfilehash: 041a0af061e4ddd1a691c396cdd15e86085124c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113702"
---
# <a name="compiler-error-c3269"></a>컴파일러 오류 C3269

' function ': 관리 되는 또는 WinRTtype의 멤버 함수는 ' ... '로 선언할 수 없습니다.

관리되는 클래스 멤버 함수와 WinRT 클래스 멤버 함수는 변수 길이 매개 변수 목록을 선언할 수 없습니다.

다음 샘플에서는 C3269 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3269_2.cpp
// compile with: /clr

ref struct A
{
   void func(int i, ...)   // C3269
   // try the following line instead
   // void func(int i )
   {
   }
};

int main()
{
}
```
