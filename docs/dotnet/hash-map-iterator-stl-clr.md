---
title: 'hash_map:: iterator (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator member [STL/CLR]
ms.assetid: fffbde89-dc72-40a9-95f2-eae7fd061c15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a4b41f3d6dd6483c30e09cbfb1c426f2b9604d1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106299"
---
# <a name="hashmapiterator-stlclr"></a>hash_map::iterator(STL/CLR)
제어되는 시퀀스에 대한 반복기의 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef T1 iterator;  
```  
  
## <a name="remarks"></a>설명  
 이 형식은 지정 되지 않은 형식의 개체를 설명 `T1` 제어 되는 시퀀스에 대 한 양방향 반복기로 사용할 수 있는 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_hash_map_iterator.cpp   
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
    Myhash_map::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" [{0} {1}]", it->first, it->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::const_iterator(STL/CLR)](../dotnet/hash-map-const-iterator-stl-clr.md)