---
title: 'queue:: value_type (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: f1abde03-982c-4aaf-91a6-cc613df9690e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3faec40fb0e8c58de03b3fa24d75459a6ac208ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160617"
---
# <a name="queuevaluetype-stlclr"></a>queue::value_type(STL/CLR)
요소의 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef Value value_type;  
```  
  
## <a name="remarks"></a>설명  
 이 형식은 템플릿 매개 변수 `Value`의 동의어입니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Myqueue::value_type val = c1.front();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/queue >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [queue (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue:: const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)   
 [queue::reference(STL/CLR)](../dotnet/queue-reference-stl-clr.md)