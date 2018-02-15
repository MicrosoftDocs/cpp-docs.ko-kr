---
title: "_CrtIsValidPointer | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
dev_langs:
- C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e81cd074c9bd69386b300d307525a76515e02522
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer
포인터가 null이 아닌지 확인합니다. Visual Studio 2010 이전 버전의 C 런타임 라이브러리에서 지정된 메모리 범위가 읽기 및 쓰기(디버그 버전에만 해당)에 유효한지 확인합니다.  
  
## <a name="syntax"></a>구문  
  
```  
int _CrtIsValidPointer(   
   const void *address,  
   unsigned int size,  
   int access   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 주소  
 유효성 테스트를 위한 메모리 범위의 시작 부분을 가리킵니다.  
  
 `size`  
 지정된 메모리 범위의 크기입니다(바이트).  
  
 access  
 메모리 범위 확인을 위한 읽기/쓰기 접근성입니다.  
  
## <a name="return-value"></a>반환 값  
 `_CrtIsValidPointer`는 지정된 포인터가 null이 아닌 경우 TRUE를 반환합니다. Visual Studio 2010 이전의 CRT 라이브러리 버전에서, 메모리 범위가 지정된 작업에 유효한 경우 TRUE가 반환됩니다. 그렇지 않은 경우 이 함수는 FALSE를 반환합니다.  
  
## <a name="remarks"></a>설명  
 Visual Studio 2010의 CRT 라이브러리부터는 `_CrtIsValidPointer`가 크기 및 액세스 매개 변수는 무시하고 지정된 주소가 null이 아닌지만 확인합니다. 이 테스트는 직접 수행하기 쉽기 때문에, 이 함수를 사용하지 않는 것이 좋습니다. Visual Studio 2010 이전 버전에서 이 함수는 `address`에서 시작하는 메모리 범위와 `size`바이트에 대한 확장이 지정된 액세스 가능 작업에 유효한지 확인합니다. `access`가 TRUE로 설정되면 메모리 범위는 읽기 및 쓰기 둘 다에 대해 유효합니다. `access`가 FALSE이면 메모리 범위는 읽기에 대해서만 유효합니다. [_DEBUG](../../c-runtime-library/debug.md)가 정의되지 않은 경우 전처리 중 `_CrtIsValidPointer` 호출이 제거됩니다.  
  
 이 함수는 TRUE 또는 FALSE를 반환하므로 이를 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 매크로 중 하나로 전달하여 간단한 디버깅 오류 처리 메커니즘을 만들 수 있습니다. 다음 예제에서는 메모리 범위가 읽기 및 쓰기 작업 둘 다에 대해 유효하지 않은 경우 어설션 실패를 발생하게 합니다.  
  
```  
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );  
```  
  
 `_CrtIsValidPointer`를 다른 디버그 함수 및 매크로와 함께 사용할 수 있는 방법에 대한 자세한 내용은 [보고서 매크로](/visualstudio/debugger/macros-for-reporting)를 참조하세요. 기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`_CrtIsValidPointer`|\<crtdbg.h>|  
  
 `_CrtIsValidPointer`는 Microsoft 확장입니다. 호환성에 대한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="libraries"></a>라이브러리  
 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.  
  
## <a name="example"></a>예  
 [_CrtIsValidHeapPointer](../../c-runtime-library/reference/crtisvalidheappointer.md) 항목에 대한 예제를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [디버그 루틴](../../c-runtime-library/debug-routines.md)