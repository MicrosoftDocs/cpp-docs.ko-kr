---
title: 'set:: generic_container (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::generic_container
dev_langs:
- C++
helpviewer_keywords:
- generic_container member [STL/CLR]
ms.assetid: 8677f211-7feb-4a23-ad02-6d4ab4713857
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2c57c191881b9ee9827c61381b920de46a1eb4d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161982"
---
# <a name="setgenericcontainer-stlclr"></a>set::generic_container(STL/CLR)
컨테이너에 대 한 제네릭 인터페이스의 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef Microsoft::VisualC::StlClr::  
    ITree<GKey, GValue>  
    generic_container;  
```  
  
## <a name="remarks"></a>설명  
 이 형식은이 서식 파일 컨테이너 클래스에 대 한 제네릭 인터페이스를 설명 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_set_generic_container.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(L'e');   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::generic_iterator(STL/CLR)](../dotnet/set-generic-iterator-stl-clr.md)