---
title: 'priority_queue:: value_type (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: 0d81ef75-8bd1-44f5-8753-4b42a505d8c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cb46becfe9ba9afb46cee644ed0cbb1205f9e3e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="priorityqueuevaluetype-stlclr"></a>priority_queue::value_type(STL/CLR)
요소의 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef Value value_type;  
```  
  
## <a name="remarks"></a>설명  
 이 형식은 템플릿 매개 변수 `Value`의 동의어입니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_priority_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mypriority_queue::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/queue >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue:: const_reference (STL/CLR)](../dotnet/priority-queue-const-reference-stl-clr.md)   
 [priority_queue::reference(STL/CLR)](../dotnet/priority-queue-reference-stl-clr.md)