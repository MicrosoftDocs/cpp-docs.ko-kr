---
title: _aligned_offset_realloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_realloc
- _o__aligned_offset_realloc
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
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: c719f62a089b1c233bac193f3431d0375af826eb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910255"
---
# <a name="_aligned_offset_realloc"></a>_aligned_offset_realloc

[_aligned_malloc](aligned-malloc.md) 또는 [_aligned_offset_malloc](aligned-offset-malloc.md)를 사용하여 할당된 메모리 블록의 크기를 변경합니다.

## <a name="syntax"></a>구문

```C
void * _aligned_offset_realloc(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
현재 메모리 블록 포인터입니다.

*size*<br/>
메모리 할당의 크기입니다.

*정렬(alignment)*<br/>
맞춤 값으로 2의 정수 거듭제곱이어야 합니다.

*offset*<br/>
맞춤을 강제하는 메모리 할당으로의 오프셋입니다.

## <a name="return-value"></a>Return Value

**_aligned_offset_realloc** 는 다시 할당 된 (그리고 이동 가능한) 메모리 블록에 대 한 void 포인터를 반환 합니다. 크기가 0이 고 버퍼 인수가 **null**이 아닌 경우 또는 블록을 지정 된 크기로 확장 하는 데 사용할 수 있는 메모리가 부족 한 경우 반환 값은 **null** 입니다. 첫 번째 경우 원래 블록이 해제됩니다. 두 번째 경우 원래 블록은 변경되지 않습니다. 반환 값은 모든 형식의 개체 스토리지를 위해 적절하게 맞도록 보장되어 있는 스토리지 공간을 가리킵니다. void가 아닌 형식의 포인터를 얻으려면 반환 값에 형식 캐스팅을 사용합니다.

**_aligned_offset_realloc** 는 및 `__declspec(noalias)` `__declspec(restrict)`로 표시 됩니다. 즉, 함수는 전역 변수를 수정 하지 않고 반환 된 포인터에 별칭이 지정 되지 않도록 보장 합니다. 자세한 내용은 [noalias](../../cpp/noalias.md) 및 [restrict](../../cpp/restrict.md)를 참조하세요.

## <a name="remarks"></a>설명

[_Aligned_offset_malloc](aligned-offset-malloc.md)와 마찬가지로 **_aligned_offset_realloc** 를 사용 하면 구조 내의 오프셋에서 구조체를 맞출 수 있습니다.

**_aligned_offset_realloc** 는 **malloc**를 기반으로 합니다. **_Aligned_offset_malloc**사용에 대 한 자세한 내용은 [malloc](malloc.md)를 참조 하세요. *Memblock* 이 **NULL**인 경우 함수는 내부적으로 **_aligned_offset_malloc** 를 호출 합니다.

이 함수는 메모리 할당에 실패 한 경우 또는 요청 된 크기가 **_HEAP_MAXREQ**보다 큰 경우 **Errno** 를 **enomem** 으로 설정 합니다. **Errno**에 대 한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요. 또한 **_aligned_offset_realloc** 은 해당 매개 변수의 유효성을 검사 합니다. *Alignment* 가 2의 거듭제곱이 아니거나 *오프셋이* *size* 보다 크거나 같고 0이 아닌 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **NULL** 을 반환 하 고 **errno** 를 **EINVAL**로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h>|

## <a name="example"></a>예제

자세한 내용은 [_aligned_malloc](aligned-malloc.md)를 참조하세요.

## <a name="see-also"></a>참조

[데이터 맞춤](../../c-runtime-library/data-alignment.md)<br/>
