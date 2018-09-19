---
title: 컴파일러 오류 C3738 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3738
dev_langs:
- C++
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07a71ae25f62d50ec52860e61e195f1c19f78030
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096563"
---
# <a name="compiler-error-c3738"></a>컴파일러 오류 C3738

'calling_convention': 인스턴스화되는 템플릿의 명시적 인스턴스화의 호출 규칙이 일치 해야 합니다

명시적 인스턴스화에서 호출 규칙을 지정 하지 않으면 것이 좋습니다. 그러나 필요한 경우 호출 규칙 일치 해야 합니다.

## <a name="example"></a>예제

다음 샘플 C3738를 생성합니다.

```
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