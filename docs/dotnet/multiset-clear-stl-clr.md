---
title: 'multiset:: clear (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::clear
dev_langs:
- C++
helpviewer_keywords:
- clear member [STL/CLR]
ms.assetid: 63c21716-fa08-47b9-b457-0b76052c5079
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d86e3a45283ee59abb6de22931795d9f28b9260
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="multisetclear-stlclr"></a>multiset::clear(STL/CLR)
모든 요소를 제거합니다.  
  
## <a name="syntax"></a>구문  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>설명  
 멤버 함수 시그니처 [multiset:: erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md) `(` [multiset:: begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md) `(),` [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `())`. 제어 되는 시퀀스 비어 있는지 확인 하려면 사용 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_multiset_clear.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::erase(STL/CLR)](../dotnet/multiset-erase-stl-clr.md)