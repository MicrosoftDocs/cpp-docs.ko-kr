---
title: "and_eq | Microsoft 문서"
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
- and_eq
- std.and_eq
- std::and_eq
dev_langs:
- C++
helpviewer_keywords:
- and_eq macro
ms.assetid: 11091772-e359-4c2b-95c6-00841ac04354
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ebe5ea2c4dc85adf5f194de39240eaa96c4ab321
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="andeq"></a>and_eq
&= 연산자에 대한 대안입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
#define and_eq &=  
  
```  
  
## <a name="remarks"></a>설명  
 매크로가 &= 연산자를 생성합니다.  
  
## <a name="example"></a>예  
  
```  
// iso646_and_eq.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   int a = 3, b = 2, result;  
  
   result= a &= b;  
   cout << result << endl;  
  
   result= a and_eq b;  
   cout << result << endl;  
}  
```  
  
```Output  
2  
2  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<iso646.h>