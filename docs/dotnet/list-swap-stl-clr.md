---
title: 'list:: swap (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::swap
dev_langs:
- C++
helpviewer_keywords:
- swap member [STL/CLR]
ms.assetid: 188b66c2-0a08-4001-a566-41d0955c89bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 298744c52e7cf68b8da9d1503014f72b695fe464
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132377"
---
# <a name="listswap-stlclr"></a>list::swap(STL/CLR)
두 컨테이너의 내용을 바꿉니다.  
  
## <a name="syntax"></a>구문  
  
```  
void swap(list<Value>% right);  
```  
  
#### <a name="parameters"></a>매개 변수  
 오른쪽  
 콘텐츠와 바꿀 컨테이너입니다.  
  
## <a name="remarks"></a>설명  
 멤버 함수는 `*this` 와 `right`간에 제어되는 시퀀스를 교환합니다. 일정 한 시간에 작업을 수행 하 고 예외가 throw 됩니다. 두 컨테이너의 내용을 교환에 신속 하 게 사용 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_list_swap.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::list<wchar_t> c2(5, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x x x x x  
x x x x x  
a b c  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/목록 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [list (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [list::operator=(STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)