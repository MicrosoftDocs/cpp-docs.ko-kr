---
description: '자세한 정보: 컴파일러 오류 C3738'
title: 컴파일러 오류 C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: 7ec94d2be4faa0324563b723eb8a674c2d2d274f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244929"
---
# <a name="compiler-error-c3738"></a>컴파일러 오류 C3738

' calling_convention ': 명시적 인스턴스화의 호출 규칙은 인스턴스화되는 템플릿의 호출 규칙과 일치 해야 합니다.

명시적 인스턴스화에 대 한 호출 규칙을 지정 하지 않는 것이 좋습니다. 그러나 필요한 경우에는 호출 규칙이 일치 해야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3738를 생성 합니다.

```cpp
// C3738.cpp
// compile with: /clr
// processor: x86
#include <stdio.h>
template< class T >
void f ( T arg ) {   // by default calling convention is __cdecl
   printf ( "f: %s\n", __FUNCSIG__ );
}

template
void __stdcall f< int > ( int arg );   // C3738
// try the following line instead
// void f< int > ( int arg );

int main () {
   f(1);
   f< int > ( 1 );
}
```
