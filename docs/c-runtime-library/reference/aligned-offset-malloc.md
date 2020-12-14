---
description: '다음에 대 한 자세한 정보: _aligned_offset_malloc'
title: _aligned_offset_malloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_malloc
- _o__aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 0a94a58abde85046e32ca50245e8b9878aeb9b92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312425"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

지정된 맞춤 경계에 메모리를 할당합니다.

## <a name="syntax"></a>구문

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>매개 변수

*size*<br/>
요청된 메모리 할당 크기입니다.

*할당*<br/>
맞춤 값으로 2의 정수 거듭제곱이어야 합니다.

*offset*<br/>
맞춤을 강제하는 메모리 할당으로의 오프셋입니다.

## <a name="return-value"></a>반환 값

할당 된 메모리 블록에 대 한 포인터 이거나, 작업에 실패 한 경우 **NULL** 입니다.

## <a name="remarks"></a>설명

**_aligned_offset_malloc** 는 중첩 된 요소에 맞춤이 필요한 경우에 유용 합니다. 예를 들어 중첩 된 클래스에 맞춤이 필요한 경우입니다.

**_aligned_offset_malloc** 는 **malloc** 를 기반으로 합니다. 자세한 내용은 [malloc](malloc.md)를 참조 하세요.

**_aligned_offset_malloc** 는 및로 표시 됩니다 `__declspec(noalias)` `__declspec(restrict)` . 즉, 함수는 전역 변수를 수정 하지 않고 반환 된 포인터에 별칭이 지정 되지 않도록 보장 합니다. 자세한 내용은 [noalias](../../cpp/noalias.md) 및 [restrict](../../cpp/restrict.md)를 참조하세요.

이 함수는 메모리 할당에 실패 한 경우 또는 요청 된 크기가 **_HEAP_MAXREQ** 보다 큰 경우 **Errno** 를 **enomem** 으로 설정 합니다. **Errno** 에 대 한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요. 또한 **_aligned_offset_malloc** 은 해당 매개 변수의 유효성을 검사 합니다. *Alignment* 가 2의 거듭제곱이 아니거나 *오프셋이* *size* 보다 크거나 같고 0이 아닌 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **NULL** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>예제

자세한 내용은 [_aligned_malloc](aligned-malloc.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[데이터 맞춤](../../c-runtime-library/data-alignment.md)<br/>
