---
title: 'hash_map:: const_reverse_iterator (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::hash_map::const_reverse_iterator
dev_langs:
- C++
helpviewer_keywords:
- const_reverse_iterator member [STL/CLR]
ms.assetid: 0c31131a-6eb6-4b14-bab9-ebc8ff25f414
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b41d006df5c5d05dcc7ad4f7026109d543725df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="hashmapconstreverseiterator-stlclr"></a>hash_map::const_reverse_iterator(STL/CLR)
제어 되는 시퀀스에 대 한 상수 역방향 반복기의 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## <a name="remarks"></a>설명  
 이 형식은 지정 되지 않은 형식의 개체를 설명 `T4` 제어 되는 시퀀스에 대 한 상수 역방향 반복기로 사용할 수 있는 합니다.  
  
## <a name="example"></a>예  
  
```  
// cliext_hash_map_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Myhash_map::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" [{0} {1}]", crit->first, crit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map::reverse_iterator(STL/CLR)](../dotnet/hash-map-reverse-iterator-stl-clr.md)