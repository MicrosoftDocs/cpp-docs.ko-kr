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
ms.openlocfilehash: 1bf54ba4114c0184871f1c79ca8f1757ae7e78b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3738"></a>컴파일러 오류 C3738
'calling_convention': 명시적 인스턴스화의 호출 규칙 인스턴스화할 서식 파일의 이름과 일치 해야 합니다  
  
 명시적 인스턴스화에서 호출 규칙을 지정 하지 않으면 것이 좋습니다. 그러나 필요한 경우 호출 규칙이 일치 해야 합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C3738 오류가 발생 합니다.  
  
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