---
title: 'deque:: pop_back (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::pop_back
dev_langs:
- C++
helpviewer_keywords:
- pop_back member [STL/CLR]
ms.assetid: 528d2c89-104c-45f7-8f05-41fe217ee37c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 74ee3030b203c66f63e87ac4a9725785078a7017
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107118"
---
# <a name="dequepopback-stlclr"></a>deque::pop_back(STL/CLR)
마지막 요소를 제거 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
void pop_back();  
```  
  
## <a name="remarks"></a>설명  
 멤버 함수는 비어 있어야 하는 제어 된 시퀀스의 마지막 요소를 제거 합니다. 뒤에 한 요소 deque를 줄이기 위해 사용 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_deque_pop_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/q u e >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)   
 [deque:: push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)   
 [deque::push_front(STL/CLR)](../dotnet/deque-push-front-stl-clr.md)