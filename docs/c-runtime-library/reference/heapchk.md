---
title: _heapchk | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _heapchk
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
- _heapchk
- heapchk
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3fc500ee86bde40def0e1e2d3dd3edad3127daf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399636"
---
# <a name="heapchk"></a>_heapchk

힙에서 일관성 확인을 실행합니다.

## <a name="syntax"></a>구문

```C
int _heapchk( void );
```

## <a name="return-value"></a>반환 값

**_heapchk** Malloc.h에 정의 된 다음 정수 매니페스트 상수 중 하나를 반환 합니다.

|반환 값|조건|
|-|-|
**_HEAPBADBEGIN**|초기 헤더 정보가 잘못되었거나 찾을 수 없습니다.
**_HEAPBADNODE**|잘못된 노드가 검색되었거나 힙이 손상되었습니다.
**_HEAPBADPTR**|힙 포인터가 잘못되었습니다.
**_HEAPEMPTY**|힙이 초기화되지 않았습니다.
**_HEAPOK**|힙이 일치하는 것 같습니다.

또한 오류가 발생 하는 경우 **_heapchk** 설정 **errno** 를 **ENOSYS**합니다.

## <a name="remarks"></a>설명

**_heapchk** 함수에 힙 최소한의 일관성을 확인 하 여 힙 관련 문제를 디버그 하는 데 도움이 됩니다. 운영 체제를 지원 하지 않는 경우 **_heapchk**함수 반환 (예: Windows 98) **_HEAPOK** 설정 **errno** 를 **ENOSYS**.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>참고자료

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
