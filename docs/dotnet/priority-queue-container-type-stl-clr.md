---
title: 'priority_queue:: container_type (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::container_type
dev_langs:
- C++
helpviewer_keywords:
- container_type member [STL/CLR]
ms.assetid: 97d79791-53cb-48f9-a139-69502517569f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 21d4287ab888d20a1c82ba4602c1d69df18b6afd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="priorityqueuecontainertype-stlclr"></a>priority_queue::container_type(STL/CLR)
기본 컨테이너의 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef Container value_type;  
```  
  
## <a name="remarks"></a>설명  
 이 형식은 템플릿 매개 변수 `Container`의 동의어입니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_priority_queue_container_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Mypriority_queue::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/queue >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::get_container(STL/CLR)](../dotnet/priority-queue-get-container-stl-clr.md)