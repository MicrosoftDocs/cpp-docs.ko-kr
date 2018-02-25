---
title: __umulh | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __umulh
dev_langs:
- C++
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3c9ebcf5e512f75e6e9fc66d5019273e1626f6a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="umulh"></a>__umulh
**Microsoft 전용**  
  
 64비트 부호 없는 두 정수의 곱에서 상위 64비트를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
unsigned __int64 __umulh(   
   unsigned __int64 a,   
   unsigned __int64 b   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [in] `a`  
 곱할 첫 번째 숫자입니다.  
  
 [in] `b`  
 곱할 두 번째 숫자입니다.  
  
## <a name="return-value"></a>반환 값  
 곱셈의 128비트 결과에서 상위 64비트입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|내장 함수|아키텍처|  
|---------------|------------------|  
|`__umulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **헤더 파일** \<. h >  
  
## <a name="remarks"></a>설명  
 이러한 루틴은 내장 함수로만 사용할 수 있습니다.  
  
## <a name="example"></a>예  
  
```  
// umulh.cpp  
// processor: X64  
#include <cstdio>  
#include <intrin.h>  
  
int main()  
{  
    unsigned __int64 i = 0x10;  
    unsigned __int64 j = 0xFEDCBA9876543210;  
    unsigned __int64 k = i * j; // k has the low 64 bits  
                                // of the product.  
    unsigned __int64 result;  
    result = __umulh(i, j); // result has the high 64 bits  
                            // of the product.  
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);  
    return 0;  
}  
```  
  
```Output  
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100   
```  
  
**Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)