---
description: '자세한 정보: 컴파일러 오류 C2691'
title: 컴파일러 오류 C2691
ms.date: 11/04/2016
f1_keywords:
- C2691
helpviewer_keywords:
- C2691
ms.assetid: 6925f8f3-ea60-4909-91e6-b781492c645d
ms.openlocfilehash: 575651d1da871a0514585fea010ef3fe98e8a3cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344330"
---
# <a name="compiler-error-c2691"></a>컴파일러 오류 C2691

' 데이터 형식 ': 관리 되는 또는 WinRTarray에는이 요소 형식을 사용할 수 없습니다.

관리되는 배열 또는 WinRT 배열의 요소 형식은 값 형식이나 참조 형식일 수 있습니다.

다음 샘플에서는 C2691 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2691a.cpp
// compile with: /clr
class A {};

int main() {
   array<A>^ a1 = gcnew array<A>(20);   // C2691
   array<int>^ a2 = gcnew array<int>(20);   // value type OK
}
```
