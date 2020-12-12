---
description: '다음에 대 한 자세한 정보: _aligned_recalloc'
title: _aligned_recalloc
ms.date: 4/2/2020
api_name:
- _aligned_recalloc
- _o__aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
ms.openlocfilehash: 6e7ae7cb41781a480018aa8f5f9e056b84fef45c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275219"
---
# <a name="_aligned_recalloc"></a>_aligned_recalloc

[_aligned_malloc](aligned-malloc.md) 또는 [_aligned_offset_malloc](aligned-offset-malloc.md)를 사용하여 할당된 메모리 블록의 크기를 변경하고 메모리를 0으로 초기화합니다.

## <a name="syntax"></a>구문

```C
void * _aligned_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>매개 변수

*memblock*<br/>
현재 메모리 블록 포인터입니다.

*number*<br/>
요소의 수입니다.

*size*<br/>
각 요소의 크기입니다(바이트).

*할당*<br/>
맞춤 값으로 2의 정수 거듭제곱이어야 합니다.

## <a name="return-value"></a>반환 값

**_aligned_recalloc** 는 다시 할당 된 (그리고 이동 가능한) 메모리 블록에 대 한 void 포인터를 반환 합니다. 크기가 0이 고 버퍼 인수가 **null** 이 아닌 경우 또는 블록을 지정 된 크기로 확장 하는 데 사용할 수 있는 메모리가 부족 한 경우 반환 값은 **null** 입니다. 첫 번째 경우 원래 블록이 해제됩니다. 두 번째 경우 원래 블록은 변경되지 않습니다. 반환 값은 모든 형식의 개체 스토리지를 위해 적절하게 맞도록 보장되어 있는 스토리지 공간을 가리킵니다. void가 아닌 형식의 포인터를 얻으려면 반환 값에 형식 캐스팅을 사용합니다.

메모리를 다시 할당하고 블록의 맞춤을 변경하면 오류가 발생합니다.

## <a name="remarks"></a>설명

**_aligned_recalloc** 는 **malloc** 를 기반으로 합니다. **_Aligned_offset_malloc** 사용에 대 한 자세한 내용은 [malloc](malloc.md)를 참조 하세요.

이 함수는 메모리 할당에 실패 한 경우 또는 요청 된 크기가 **_HEAP_MAXREQ** 보다 큰 경우 **Errno** 를 **enomem** 으로 설정 합니다. **Errno** 에 대 한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조 하세요. 또한 **_aligned_recalloc** 은 해당 매개 변수의 유효성을 검사 합니다. *Alignment* 가 2의 거듭제곱이 아닌 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우이 함수는 **NULL** 을 반환 하 고 **errno** 를 **EINVAL** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_aligned_recalloc**|\<malloc.h>|

## <a name="see-also"></a>참고 항목

[데이터 맞춤](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
