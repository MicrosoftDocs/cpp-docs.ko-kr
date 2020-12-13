---
description: '다음에 대 한 자세한 정보: _heapchk'
title: _heapchk
ms.date: 4/2/2020
api_name:
- _heapchk
- _o__heapchk
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: 57cde789c8d6e6b8c8da91adf4a6f274ce557ed7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332797"
---
# <a name="_heapchk"></a>_heapchk

힙에서 일관성 확인을 실행합니다.

## <a name="syntax"></a>구문

```C
int _heapchk( void );
```

## <a name="return-value"></a>Return Value

**_heapchk** 는 Malloc에 정의 된 다음 정수 매니페스트 상수 중 하나를 반환 합니다.

|반환 값|조건|
|-|-|
| **_HEAPBADBEGIN** | 초기 헤더 정보가 잘못되었거나 찾을 수 없습니다. |
| **_HEAPBADNODE** | 잘못된 노드가 검색되었거나 힙이 손상되었습니다. |
| **_HEAPBADPTR** | 힙 포인터가 잘못되었습니다. |
| **_HEAPEMPTY** | 힙이 초기화되지 않았습니다. |
| **_HEAPOK** | 힙이 일치하는 것 같습니다. |

또한 오류가 발생 하는 경우에는 **_heapchk** **errno** 를 **ENOSYS** 로 설정 합니다.

## <a name="remarks"></a>설명

**_Heapchk** 함수는 힙의 최소 일관성을 검사 하 여 힙 관련 문제를 디버그 하는 데 도움이 됩니다. 운영 체제에서 **_heapchk**(예: Windows 98)를 지원 하지 않는 경우 함수는 **_HEAPOK** 을 반환 하 고 **errno** 를 **ENOSYS** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

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

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
