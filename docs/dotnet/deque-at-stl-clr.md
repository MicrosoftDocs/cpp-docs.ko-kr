---
title: 'deque:: at (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::at
dev_langs:
- C++
helpviewer_keywords:
- at member [STL/CLR]
ms.assetid: 9af83d8a-c519-4b2a-a25f-d3dc8bbb87fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8388f6428d31cce2993e7c90db66f430564d347e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="dequeat-stlclr"></a>deque::at(STL/CLR)
지정된 위치에 있는 요소에 액세스합니다.  
  
## <a name="syntax"></a>구문  
  
```  
reference at(size_type pos);  
```  
  
#### <a name="parameters"></a>매개 변수  
 위치  
 액세스할 요소의 위치입니다.  
  
## <a name="remarks"></a>설명  
 멤버 함수는 위치에서 제어 된 시퀀스의 요소에 대 한 참조를 반환 `pos`합니다. 읽기 또는 쓰기 요소 위치를 알아야 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_deque_at.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/q u e >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::operator(STL/CLR)](../dotnet/deque-operator-stl-clr.md)