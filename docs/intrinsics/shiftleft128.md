---
title: __shiftleft128 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __shiftleft128
dev_langs:
- C++
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57846bab53e50f1644dcdc3ec817472e47793840
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725207"
---
# <a name="shiftleft128"></a>__shiftleft128
**Microsoft 전용**  
  
 두 개의 64비트 수량 `LowPart` 및 `HighPart`로 표현되는 128비트 수량을 `Shift`로 지정된 비트 수만큼 왼쪽으로 이동하고 결과 중 상위 64비트를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
unsigned __int64 __shiftleft128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
*LowPart*<br/>
[in] 이동할 128 비트 수량 중 하위 64 비트입니다.  
  
*HighPart*<br/>
[in] 이동할 128 비트 수량 중 상위 64 비트입니다.  
  
*Shift*<br/>
[in] 이동할 비트 수입니다.  
  
## <a name="return-value"></a>반환 값  
 결과의 상위 64비트입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|내장 함수|아키텍처|  
|---------------|------------------|  
|`__shiftleft128`|X64|  
  
 **헤더 파일** \<intrin.h >  
  
## <a name="remarks"></a>설명  
 `Shift` 값은 항상 64로 나눈 나머지이므로 예를 들어 `__shiftleft128(1, 0, 64)`를 호출하면 함수는 하위 부분의 `0`비트를 왼쪽으로 이동하고 일반적인 경우에 반환되는 `0`이 아닌 상위 부분 `1`을 반환합니다.  
  
## <a name="example"></a>예제  
  
```  
// shiftleft128.c  
// processor: IPF, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__shiftleft128, __shiftright128)  
  
int main()  
{  
    unsigned __int64 i = 0x1I64;  
    unsigned __int64 j = 0x10I64;  
    unsigned __int64 ResultLowPart;  
    unsigned __int64 ResultHighPart;  
  
    ResultLowPart = i << 1;  
    ResultHighPart = __shiftleft128(i, j, 1);  
  
    // concatenate the low and high parts padded with 0's  
    // to display correct hexadecimal 128 bit values  
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);  
  
    ResultHighPart = j >> 1;  
    ResultLowPart = __shiftright128(i, j, 1);  
  
    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);    
}  
```  
  
```Output  
0x100000000000000001 << 1 = 0x200000000000000002  
0x100000000000000001 >> 1 = 0x080000000000000000  
```  
  
**Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [__shiftright128](../intrinsics/shiftright128.md)   
 [컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)