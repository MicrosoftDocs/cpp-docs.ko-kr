---
title: 컴파일러 경고 (수준 1) C4346 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4346
dev_langs:
- C++
helpviewer_keywords:
- C4346
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 090c7ba576973c2dfb2e5fd7e117cddc379b4dfe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276265"
---
# <a name="compiler-warning-level-1-c4346"></a>컴파일러 경고(수준 1) C4346
'name': 종속 이름이 형식이 아닙니다  
  
 [typename](../../cpp/typename.md) 키워드는 종속 이름 형식으로 처리 하는 경우에 필요 합니다. 모든 버전의 Visual c + +에서 동일 하 게 작동 하는 코드에 대 한 추가 `typename` 선언에 있습니다.  
  
 다음 샘플에서는 C4346 오류가 생성 됩니다.  
  
```  
// C4346.cpp  
// compile with: /WX /LD  
template<class T>  
struct C {  
   T::X* x;   // C4346  
   // try the following line instead  
   // typename T::X* x;  
};  
```  
  
 다음 샘플에서는 다른 예를 보여 줍니다. 여기서는 **typename** 키워드를 사용 합니다.  
  
```  
// C4346b.cpp  
// compile with: /LD /W1  
template<class T>  
const typename T::X& f(typename T::Z* p);   // Required in both places  
  
template<class T, int N>  
struct L{};  
  
template<class T>  
struct M : public L<typename T::Type, T::Value>   
{   // required on type argument, not on non-type argument  
   typedef typename T::X   Type;  
   Type f();   // OK: "Type" is a type-specifer  
   typename T::X g();   // typename required  
   operator typename T::Z();   // typename required      
};  
```  
  
 및이  
  
```  
// C4346c.cpp  
// compile with: /LD /WX  
struct Y {  
   typedef int Y_t;  
};  
  
template<class T>  
struct A {  
   typedef Y A_t;  
};  
  
template<class T>  
struct B {  
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here  
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here  
};  
```