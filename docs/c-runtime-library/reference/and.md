---
title: "및 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- And
- std.and
- std::and
dev_langs:
- C++
helpviewer_keywords:
- and macro
ms.assetid: 2644ab57-8e1b-48f0-9021-cafe3e26bdc4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3984925cbb40daecb66fb964e884197a7fb0f8c9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="and"></a>를 갖는
&& 연산자에 대한 대안입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
#define and &&  
  
```  
  
## <a name="remarks"></a>설명  
 매크로가 && 연산자를 생성합니다.  
  
## <a name="example"></a>예  
  
```  
// iso646_and.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   bool a = true, b = false, result;  
  
   boolalpha(cout);  
  
   result= a && b;  
   cout << result << endl;  
  
   result= a and b;  
   cout << result << endl;  
}  
```  
  
```Output  
false  
false  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<iso646.h>