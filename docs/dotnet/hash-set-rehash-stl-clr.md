---
title: 'hash_set:: rehash (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::rehash
dev_langs:
- C++
helpviewer_keywords:
- rehash member [STL/CLR]
ms.assetid: f62bae81-4321-44e1-97d0-77174a13e0de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c4a90a2429f1c35e6a5617a2eeb145acb2f7239c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33126046"
---
# <a name="hashsetrehash-stlclr"></a>hash_set::rehash(STL/CLR)
해시 테이블을 다시 빌드합니다.  
  
## <a name="syntax"></a>구문  
  
```  
void rehash();  
```  
  
## <a name="remarks"></a>설명  
 멤버 함수를 다시 작성 하는 해시 테이블 [hash_set:: load_factor (STL/CLR)](../dotnet/hash-set-load-factor-stl-clr.md) `() <=` [hash_set:: max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)합니다. 그렇지 않은 경우 삽입 후 필요에 따라만 해시 테이블의 크기가 늘어납니다. (자동으로 감소의 크기입니다.) 해시 테이블의 크기를 조정 하려면 사용 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_hash_set_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
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
 a b c  
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
 **헤더:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set:: bucket_count (STL/CLR)](../dotnet/hash-set-bucket-count-stl-clr.md)   
 [hash_set:: load_factor (STL/CLR)](../dotnet/hash-set-load-factor-stl-clr.md)   
 [hash_set::max_load_factor(STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)