---
title: 'hash_map:: rehash (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_map::rehash
dev_langs:
- C++
helpviewer_keywords:
- rehash member [STL/CLR]
ms.assetid: e894157c-4e31-4fbf-8020-b90f236da3e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3156d5102c4afdf9ec987b8c35870ad46d735b88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="hashmaprehash-stlclr"></a>hash_map::rehash(STL/CLR)
해시 테이블을 다시 빌드합니다.  
  
## <a name="syntax"></a>구문  
  
```  
void rehash();  
```  
  
## <a name="remarks"></a>설명  
 멤버 함수를 다시 작성 하는 해시 테이블 [hash_map:: load_factor (STL/CLR)](../dotnet/hash-map-load-factor-stl-clr.md) `() <=` [hash_map:: max_load_factor (STL/CLR)](../dotnet/hash-map-max-load-factor-stl-clr.md)합니다. 그렇지 않은 경우 삽입 후 필요에 따라만 해시 테이블의 크기가 늘어납니다. (자동으로 감소의 크기입니다.) 해시 테이블의 크기를 조정 하려면 사용 합니다.  
  
## <a name="example"></a>예  
  
```  
// cliext_hash_map_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1 = gcnew Myhash_map;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map:: bucket_count (STL/CLR)](../dotnet/hash-map-bucket-count-stl-clr.md)   
 [hash_map:: load_factor (STL/CLR)](../dotnet/hash-map-load-factor-stl-clr.md)   
 [hash_map::max_load_factor(STL/CLR)](../dotnet/hash-map-max-load-factor-stl-clr.md)