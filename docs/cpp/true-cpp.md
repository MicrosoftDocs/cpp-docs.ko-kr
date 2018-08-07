---
title: true (c + +) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- true_cpp
dev_langs:
- C++
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb810f880ac86651059d71a59040e34810c7e167
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464774"
---
# <a name="true-c"></a>true (C++)
## <a name="syntax"></a>구문  
  
```  
bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## <a name="remarks"></a>설명  
 이 키워드는 형식의 변수에 대 한 두 값 중 하나 [bool](../cpp/bool-cpp.md) 또는 조건식 (조건식은 true 부울 식을 이제). 경우 `i` 유형임 **bool**, then 문 `i = true;` 할당 **true** 에 `i`입니다.  
  
## <a name="example"></a>예  
  
```cpp 
// bool_true.cpp  
#include <stdio.h>  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
```Output  
1  
0  
```  
  
## <a name="see-also"></a>참고자료  
 [키워드](../cpp/keywords-cpp.md)