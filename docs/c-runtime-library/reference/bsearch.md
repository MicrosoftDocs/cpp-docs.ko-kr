---
title: bsearch
ms.date: 4/2/2020
api_name:
- bsearch
- _o_bsearch
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: 3a6083f39e12182ae512f5327b5f7d8d89deb2a2
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039549"
---
# <a name="bsearch"></a>bsearch

정렬된 배열의 이진 검색을 수행합니다. 이 함수의 더 안전한 버전을 사용할 수 있습니다. [bsearch_s](bsearch-s.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>매개 변수

*키인지*\
검색할 키에 대 한 포인터입니다.

*하단*\
검색 데이터의 기준에 대 한 포인터입니다.

*수많은*\
요소의 수입니다.

*너비*\
요소의 너비입니다.

*과*\
두 요소를 비교하는 콜백 함수입니다. 첫 번째는 검색 키에 대 한 포인터이 고, 두 번째는 키와 비교할 배열 요소에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

**b** i s e >는 *base*에서 가리키는 배열의 *키* 발생에 대 한 포인터를 반환 합니다. *키* 를 찾을 수 없는 경우이 함수는 **NULL**을 반환 합니다. 배열이 오름차순 정렬이 아니거나 동일한 키를 가진 중복 레코드를 포함하는 경우에는 결과를 예측할 수 없습니다.

## <a name="remarks"></a>설명

검색 **함수는** 각 *너비가* 바이트 인 *number* 요소의 정렬 된 배열에 대해 이진 검색을 수행 합니다. *기준* 값은 검색할 배열 기준에 대 한 포인터이 고 *key* 는 검색 중인 값입니다. *Compare* 매개 변수는 요청 된 키를 배열 요소와 비교 하는 사용자 제공 루틴에 대 한 포인터입니다. 해당 관계를 지정 하는 다음 값 중 하나를 반환 합니다.

|*비교* 루틴에서 반환 된 값|Description|
|-----------------------------------------|-----------------|
|`< 0`|키가 배열 요소보다 작습니다.|
|`0`|키가 배열 요소와 같습니다.|
|`> 0`|키가 배열 요소보다 큽니다.|

이 함수는 해당 매개 변수의 유효성을 검사합니다. *Compare*, *key* 또는 *number* 가 **null**이거나 *base* 가 **null** 이 고 *숫자가* 0이 아닌 경우 또는 *width* 가 0 인 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은로 설정 되 `EINVAL` 고 함수는 **NULL**을 반환 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> 및 \<search.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

이 프로그램은 qsort를 사용하여 문자열 배열을 정렬한 다음 bsearch를 사용하여 "cat" 단어를 찾습니다.

```C
// crt_bsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( char **arg1, char **arg2 )
{
   /* Compare all of both strings: */
   return _strcmpi( *arg1, *arg2 );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};
   char **result;
   char *key = "cat";
   int i;

   /* Sort using Quicksort algorithm: */
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const
   void*, const void*))compare );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),
                              sizeof( char * ), (int (*)(const void*, const void*))compare );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>참고 항목

[검색 및 정렬](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
