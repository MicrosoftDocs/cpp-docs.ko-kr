---
description: '자세한 정보: 컴파일러 오류 C2589'
title: 컴파일러 오류 C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: b874988f65ef41a9cde19e4c0229a6cb54859b28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177499"
---
# <a name="compiler-error-c2589"></a>컴파일러 오류 C2589

' identifier ': ':: ' 오른쪽에 잘못 된 토큰이 있습니다.

클래스, 구조체 또는 공용 구조체 이름이 범위 결정 연산자 (이중 콜론)의 왼쪽에 나타나는 경우 오른쪽에 있는 토큰은 클래스, 구조체 또는 공용 구조체 멤버 여야 합니다. 그렇지 않으면 모든 전역 식별자가 오른쪽에 표시 될 수 있습니다.

범위 결정 연산자를 오버 로드할 수 없습니다.

다음 샘플에서는 C2589를 생성 합니다.

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
