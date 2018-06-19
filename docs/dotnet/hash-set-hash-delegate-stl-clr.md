---
title: 'hash_set:: hash_delegate (STL/CLR) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::hash_delegate
dev_langs:
- C++
helpviewer_keywords:
- hash_delegate member [STL/CLR]
ms.assetid: 34e39d2d-f2ef-4755-9201-3cdb4e41ea56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e636ce4e508b4ea6ae2b681dd915e016817cd0ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135549"
---
# <a name="hashsethashdelegate-stlclr"></a>hash_set::hash_delegate(STL/CLR)
지정된 키와 일치하는 요소를 찾습니다.  
  
## <a name="syntax"></a>구문  
  
```  
hasher^ hash_delegate();  
```  
  
## <a name="remarks"></a>설명  
 멤버 함수는 키 값을 정수로 변환 하는 데 사용 되는 대리자를 반환 합니다. 키 해시를 사용 합니다.  
  
## <a name="example"></a>예제  
  
```  
// cliext_hash_set_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::hasher(STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)