---
title: 'map:: reverse_iterator (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::reverse_iterator
dev_langs:
- C++
helpviewer_keywords:
- reverse_iterator member [STL/CLR]
ms.assetid: 50e461a5-61d1-455f-9c66-e0a8d88d54db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 09dd76510289be522e2df71946c493ad6367ddd8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="mapreverseiterator-stlclr"></a>map::reverse_iterator(STL/CLR)
제어되는 시퀀스에 대한 반대 반복기의 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef T3 reverse_iterator;  
```  
  
## <a name="remarks"></a>설명  
 이 형식은 제어된 시퀀스에 대해 반대 반복기로 사용될 수 있는 지정되지 않은 `T3` 형식의 개체를 설명합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_map_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymap::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" [{0} {1}]", rit->first, rit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/매핑 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [map (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map:: const_iterator (STL/CLR)](../dotnet/map-const-iterator-stl-clr.md)   
 [map:: const_reverse_iterator (STL/CLR)](../dotnet/map-const-reverse-iterator-stl-clr.md)   
 [map::iterator(STL/CLR)](../dotnet/map-iterator-stl-clr.md)