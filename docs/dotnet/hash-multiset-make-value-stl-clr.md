---
title: 'hash_multiset:: make_value (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::make_value
dev_langs:
- C++
helpviewer_keywords:
- make_value member [STL/CLR]
ms.assetid: 33a4df1c-5451-44f2-af2e-a8419f9be3b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 695c515bd61fbc2c6d114f64a0715ed7996b8f92
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33126267"
---
# <a name="hashmultisetmakevalue-stlclr"></a>hash_multiset::make_value(STL/CLR)
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
// cliext_hash_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(Myhash_multiset::make_value(L'a'));   
    c1.insert(Myhash_multiset::make_value(L'b'));   
    c1.insert(Myhash_multiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset:: key_type (STL/CLR)](../dotnet/hash-multiset-key-type-stl-clr.md)   
 [hash_multiset::value_type(STL/CLR)](../dotnet/hash-multiset-value-type-stl-clr.md)