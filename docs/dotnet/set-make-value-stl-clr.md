---
title: 'set:: make_value (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::make_value
dev_langs:
- C++
helpviewer_keywords:
- make_value member [STL/CLR]
ms.assetid: 2f71515e-7de1-4139-a68e-72ff2a96aa4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9c881a0d7986a628778c63a6a954938db7b8945d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="setmakevalue-stlclr"></a>set::make_value(STL/CLR)
값 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>매개 변수  
 key  
 사용할 키 값입니다.  
  
## <a name="remarks"></a>설명  
 멤버 함수가 반환 하는 `value_type` 개체 키가 `key`합니다. 여러 다른 멤버 함수 사용에 적합 한 개체를 작성 하려면 사용 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_set_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(Myset::make_value(L'a'));   
    c1.insert(Myset::make_value(L'b'));   
    c1.insert(Myset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set:: key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)   
 [set::value_type(STL/CLR)](../dotnet/set-value-type-stl-clr.md)