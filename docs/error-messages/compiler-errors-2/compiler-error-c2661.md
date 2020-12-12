---
description: '자세한 정보: 컴파일러 오류 C2661'
title: 컴파일러 오류 C2661
ms.date: 11/04/2016
f1_keywords:
- C2661
helpviewer_keywords:
- C2661
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
ms.openlocfilehash: 524d270fd15b529bad13a5ff1e5e46f3d5d9dd04
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170024"
---
# <a name="compiler-error-c2661"></a>컴파일러 오류 C2661

' function ': 오버 로드 된 함수에는 숫자 매개 변수를 사용 하지 않습니다.

가능한 원인:

1. 함수 호출의 실제 매개 변수가 잘못 되었습니다.

1. 함수 선언이 없습니다.

다음 샘플에서는 C2661를 생성 합니다.

```cpp
// C2661.cpp
void func( int ){}
void func( int, int ){}
int main() {
   func( );   // C2661 func( void ) was not declared
   func( 1 );   // OK func( int ) was declared
}
```
