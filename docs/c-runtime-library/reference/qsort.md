---
title: qsort
description: Microsoft C 런타임 quick sort API에 대해 설명 합니다. `qsort`
ms.date: 10/23/2020
api_name:
- qsort
- _o_qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: c658ffae69cd662809eb4dac09c06b6a13f4e051
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639122"
---
# <a name="qsort"></a>qsort

빠른 정렬을 수행합니다. 이 함수의 더 안전한 버전을 사용할 수 있습니다. [qsort_s](qsort-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>매개 변수

*`base`*\
대상 배열의 시작 부분입니다.

*`number`*\
요소의 배열 크기입니다.

*`width`*\
요소 크기(바이트)입니다.

*`compare`*\
두 배열 요소를 비교하여 해당 관계를 지정하는 값을 반환하는 사용자가 제공한 루틴에 대한 포인터입니다.

## <a name="remarks"></a>설명

**`qsort`** 함수는 *`number`* 각 바이트의 요소 배열을 정렬 하기 위해 빠른 정렬 알고리즘을 구현 합니다 *`width`* . 인수는 *`base`* 정렬할 배열의 기준에 대 한 포인터입니다. **`qsort`** 정렬 된 요소를 사용 하 여이 배열을 덮어씁니다.

**`qsort`** 는 *`compare`* 정렬 중에 루틴을 한 번 이상 호출 하 고 각 호출에서 두 배열 요소에 포인터를 전달 합니다. *`compare`* 에서 두 요소가 같은 것으로 표시 되 면 정렬 된 정렬 된 배열에서 순서가 지정 되지 않습니다.

```C
compare( (void *) & elem1, (void *) & elem2 );
```

루틴은 요소를 비교한 후에 다음 값 중 하나를 반환합니다.

|비교 함수 반환 값|Description|
|-----------------------------------|-----------------|
|< 0|**`elem1`** 보다 작음 **`elem2`**|
|0|**`elem1`** 와 동일 합니다. **`elem2`**|
|> 0|**`elem1`** 보다 큼 **`elem2`**|

비교 함수에 정의된 대로 배열은 오름차순으로 정렬됩니다. 배열을 내림차순으로 정렬하려면 비교 함수에서 "보다 큼"과 "보다 작음"의 의미를 반전하면 됩니다.

이 함수는 해당 매개 변수의 유효성을 검사합니다. *`compare`* 또는이 이거나,가이 고가 0이 아닌 경우 또는가 *`number`* **`NULL`** *`base`* **`NULL`** *`number`* *`width`* 0 보다 작은 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는를 반환 하 고 **`errno`** 는로 설정 됩니다 **`EINVAL`** .

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`qsort`**|\<stdlib.h> 및 \<search.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_qsort.c
// arguments: every good boy deserves favor

/* This program reads the command-line
* parameters and uses qsort to sort them. It
* then displays the sorted arguments.
*/

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main( int argc, char **argv )
{
   int i;
   /* Eliminate argv[0] from sort: */
   argv++;
   argc--;

   /* Sort remaining args using Quicksort algorithm: */
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );

   /* Output sorted list: */
   for( i = 0; i < argc; ++i )
      printf( " %s", argv[i] );
   printf( "\n" );
}

int compare( const void *arg1, const void *arg2 )
{
   /* Compare all of both strings: */
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );
}
```

```Output
boy deserves every favor good
```

## <a name="see-also"></a>참고 항목

[검색 및 정렬](../../c-runtime-library/searching-and-sorting.md)\
[`bsearch`](bsearch.md)\
[`_lsearch`](lsearch.md)
