---
title: "_aligned_offset_malloc | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_offset_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _aligned_offset_malloc
- aligned_offset_malloc
dev_langs:
- C++
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b192d8bf88ac40fffdbdf601e74ee1b265e7171
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc
지정된 맞춤 경계에 메모리를 할당합니다.  
  
## <a name="syntax"></a>구문  
  
```  
void * _aligned_offset_malloc(  
   size_t size,   
   size_t alignment,   
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [in] `size`  
 요청된 메모리 할당 크기입니다.  
  
 [in] `alignment`  
 맞춤 값으로 2의 정수 거듭제곱이어야 합니다.  
  
 [in] `offset`  
 맞춤을 강제하는 메모리 할당으로의 오프셋입니다.  
  
## <a name="return-value"></a>반환 값  
 할당된 메모리 블록에 대한 포인터로 작업 실패 시 `NULL`입니다.  
  
## <a name="remarks"></a>설명  
 `_aligned_offset_malloc`는 중첩된 요소에 맞춤이 필요한 상황에서 유용합니다(예: 중첩된 클래스에 맞춤이 필요한 경우).  
  
 `_aligned_offset_malloc`는 `malloc`를 기반으로 합니다. 자세한 내용은 [malloc](../../c-runtime-library/reference/malloc.md)를 참조하세요.  
  
 `_aligned_offset_malloc`는 `__declspec(noalias)` 및 `__declspec(restrict)`로 표시되며, 이는 함수가 전역 변수를 수정할 수 없도록 보장되고 반환된 포인터에 별칭이 지정되지 않음을 의미합니다. 자세한 내용은 [noalias](../../cpp/noalias.md) 및 [restrict](../../cpp/restrict.md)를 참조하세요.  
  
 이 함수는 메모리 할당에 실패한 경우 또는 요청된 크기가 `errno`보다 큰 경우 `ENOMEM`를 `_HEAP_MAXREQ`으로 설정합니다. `errno`에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요. 또한 `_aligned_offset_malloc`는 매개 변수의 유효성을 검사합니다. `alignment`가 2의 거듭제곱이 아니거나 `offset`이 `size`와 같거나 크고 0이 아닌 경우 이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에서 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속해서 실행하도록 허용한 경우 이 함수는 `NULL`을 반환하고 `errno`를 `EINVAL`로 설정합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`_aligned_offset_malloc`|\<malloc.h>|  
  
## <a name="example"></a>예  
 자세한 내용은 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 맞춤](../../c-runtime-library/data-alignment.md)