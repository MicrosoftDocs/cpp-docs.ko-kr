---
title: 'multimap:: const_reference (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multimap::const_reference
dev_langs:
- C++
helpviewer_keywords:
- const_reference member [STL/CLR]
ms.assetid: ae963633-63a9-4f73-bc06-7bac13663f5a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 14b1becbbfdb9db8deeafb377bbf13fbcb71eb79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="multimapconstreference-stlclr"></a>multimap::const_reference(STL/CLR)
요소에 대한 상수 참조의 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef value_type% const_reference;  
```  
  
## <a name="remarks"></a>설명  
 이 형식은 요소에 대 한 상수 참조를 설명 합니다.  
  
## <a name="example"></a>예  
  
```  
// cliext_multimap_const_reference.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymultimap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Mymultimap::const_reference cref = *cit;   
        System::Console::Write(" [{0} {1}]", cref->first, cref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/매핑 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap:: reference (STL/CLR)](../dotnet/multimap-reference-stl-clr.md)   
 [multimap::value_type(STL/CLR)](../dotnet/multimap-value-type-stl-clr.md)