---
title: 'hash_map:: end (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::end
dev_langs:
- C++
helpviewer_keywords:
- end member [STL/CLR]
ms.assetid: bda12a48-cc2b-426f-a4e8-992c88f61736
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 230c5a68ef4f8564769801d71a0d9bf7b0d602b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108340"
---
# <a name="hashmapend-stlclr"></a>hash_map::end(STL/CLR)
제어되는 시퀀스의 끝을 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
iterator end();  
```  
  
## <a name="remarks"></a>설명  
 멤버 함수는 제어 된 시퀀스의 끝 바로 다음을 가리키는 양방향 반복기를 반환합니다. 제어 된 시퀀스의 끝을 지정 하는 반복기를 가져올 사용 해당 상태 대상이 제어 된 시퀀스의 길이가 변경 하는 경우 변경 되지 않습니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_hash_map_end.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myhash_map::iterator it = c1.end();   
    --it;   
    --it;   
    System::Console::WriteLine("*-- --end() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*--end() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*-- --end() = [b 2]  
*--end() = [c 3]  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::begin(STL/CLR)](../dotnet/hash-map-begin-stl-clr.md)