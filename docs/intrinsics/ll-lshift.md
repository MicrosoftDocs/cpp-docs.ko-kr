---
title: __ll_lshift | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
dev_langs:
- C++
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bfb567774191edb86a9eb34a38be69344f19575
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702080"
---
# <a name="lllshift"></a>__ll_lshift
**Microsoft 전용**  
  
 제공된 된 64 비트 값 왼쪽에 지정 된 비트 수 만큼 이동합니다.  
  
## <a name="syntax"></a>구문  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
*마스크*<br/>
[in] 시프트 레프트 64 비트 정수 값입니다.  
  
*nBit*<br/>
[in] 이동할 비트 수입니다.  
  
## <a name="return-value"></a>반환 값  
 왼쪽으로 이동 하 여 마스크 `nBit` 비트입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|내장 함수|아키텍처|  
|---------------|------------------|  
|`__ll_lshift`|x86, x64|  
  
 **헤더 파일** \<intrin.h >  
  
## <a name="remarks"></a>설명  
 64 비트 아키텍처를 사용 하 여 프로그램을 컴파일하는 경우 및 `nBit` 63 보다 크면 이동할 비트 수는 `nBit` 64 모듈로. 32 비트 아키텍처를 사용 하 여 프로그램을 컴파일하는 경우 및 `nBit` 31, 보다 크면 이동할 비트 수는 `nBit` 32 모듈로.  
  
 합니다 `ll` 이름에서에 작업 임을 나타냅니다 `long long` (`__int64`).  
  
## <a name="example"></a>예제  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## <a name="output"></a>출력  
  
```  
10000  
```  
  
 **참고** 왼쪽된 시프트 연산의 부호 없는 버전이 없습니다. 왜냐하면 `__ll_lshift` 이미 서명 되지 않은 입력된 매개 변수를 사용 합니다. 오른쪽 시프트는 달리 왼쪽된 shift에 대 한 로그인 종속 되지 않습니다 결과의 최하위 비트 0의 값 이동 부호에 관계 없이 항상 설정 되어 있기 때문입니다.  
  
**Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)   
 [컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)