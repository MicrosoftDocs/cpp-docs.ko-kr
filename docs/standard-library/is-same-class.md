---
title: "is_same 클래스 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_same
dev_langs:
- C++
helpviewer_keywords:
- is_same class
- is_same
ms.assetid: d9df6c1d-c270-4ec2-802a-af275648dd1d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a00f60ddaf50f1f175e48422c735e846b04b9d24
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="issame-class"></a>is_same 클래스
두 형식이 동일한지 테스트합니다.  
  
## <a name="syntax"></a>구문  
  
```  
template <class Ty1, class Ty2>  
struct is_same;  
```  
  
#### <a name="parameters"></a>매개 변수  
 `Ty1`  
 쿼리할 첫 번째 형식입니다.  
  
 `Ty2`  
 쿼리할 두 번째 형식입니다.  
  
## <a name="remarks"></a>설명  
 형식 조건자의 인스턴스는 `Ty1` 및 `Ty2` 형식이 동일한 형식인 경우 true이고 그렇지 않은 경우 false입니다.  
  
## <a name="example"></a>예  
  
```cpp  
// std__type_traits__is_same.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct base   
    {   
    int val;   
    };   
  
struct derived   
    : public base   
    {   
    };   
  
int main()   
    {   
    std::cout << "is_same<base, base> == " << std::boolalpha   
        << std::is_same<base, base>::value << std::endl;   
    std::cout << "is_same<base, derived> == " << std::boolalpha   
        << std::is_same<base, derived>::value << std::endl;   
    std::cout << "is_same<derived, base> == " << std::boolalpha   
        << std::is_same<derived, base>::value << std::endl;   
    std::cout << "is_same<int, int> == " << std::boolalpha   
        << std::is_same<int, int>::value << std::endl;   
    std::cout << "is_same<int, const int> == " << std::boolalpha   
        << std::is_same<int, const int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_same<base, base> == true  
is_same<base, derived> == false  
is_same<derived, base> == false  
is_same<int, int> == true  
is_same<int, const int> == false  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<type_traits>  
  
 **네임스페이스:** std  
  
## <a name="see-also"></a>참고 항목  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_convertible 클래스](../standard-library/is-convertible-class.md)   
 [is_base_of 클래스](../standard-library/is-base-of-class.md)
