---
title: 'collection_adapter:: collection_adapter (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
dev_langs:
- C++
helpviewer_keywords:
- collection_adapter member [STL/CLR]
ms.assetid: 7e2bb75b-d735-4135-9523-719683e06fe9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 190379cbfeea0f1bbf747d537f9501f076f6bb0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="collectionadaptercollectionadapter-stlclr"></a>collection_adapter::collection_adapter(STL/CLR)
어댑터 개체를 생성 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>매개 변수  
 컬렉션  
 래핑할 BCL 핸들입니다.  
  
 오른쪽  
 복사할 개체입니다.  
  
## <a name="remarks"></a>설명  
 생성자:  
  
 `collection_adapter();`  
  
 저장 된 핸들을 초기화 `nullptr`합니다.  
  
 생성자:  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 저장 된 핸들을 초기화 `right.` [collection_adapter:: base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`합니다.  
  
 생성자:  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 저장 된 핸들을 초기화 `right->` [collection_adapter:: base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`합니다.  
  
 생성자:  
  
 `collection_adapter(Coll^ collection);`  
  
 사용 된 저장된 핸들 초기화 `collection`합니다.  
  
## <a name="example"></a>예  
  
```  
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
base() null = True  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<cliext/어댑터 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>참고 항목  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [collection_adapter::operator=(STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)