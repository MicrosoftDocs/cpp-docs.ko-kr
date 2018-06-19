---
title: 'map:: make_value (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::make_value
dev_langs:
- C++
helpviewer_keywords:
- make_value member [STL/CLR]
ms.assetid: a0bc4081-b8b7-450e-b041-a49ac42b279f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 14d238d8ecfbbff4675c3a46da8afb46561cec6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133125"
---
# <a name="mapmakevalue-stlclr"></a>map::make_value(STL/CLR)
값 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### <a name="parameters"></a>매개 변수  
 key  
 사용할 키 값입니다.  
  
 매핑된  
 매핑된 검색할 값입니다.  
  
## <a name="remarks"></a>설명  
 멤버 함수가 반환 하는 `value_type` 개체 키가 `key` 고 매핑된 값이 `mapped`합니다. 여러 다른 멤버 함수 사용에 적합 한 개체를 작성 하려면 사용 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_map_make_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
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
 [map (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map:: key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)   
 [map:: mapped_type (STL/CLR)](../dotnet/map-mapped-type-stl-clr.md)   
 [map::value_type(STL/CLR)](../dotnet/map-value-type-stl-clr.md)