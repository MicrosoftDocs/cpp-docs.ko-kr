---
description: '다음에 대 한 자세한 정보: _CrtCheckMemory'
title: _CrtCheckMemory
ms.date: 11/04/2016
api_name:
- _CrtCheckMemory
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: f2537997a9adc1c2346560d3b65eecc633933616
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221594"
---
# <a name="_crtcheckmemory"></a>_CrtCheckMemory

디버그 힙에서 할당된 메모리 블록의 무결성을 확인합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Return Value

성공 하면 **_CRTCHECKMEMORY** TRUE를 반환 합니다. 그렇지 않으면 함수는 FALSE를 반환 합니다.

## <a name="remarks"></a>설명

**_CrtCheckMemory** 함수는 기본 힙을 확인 하 고 모든 메모리 블록을 검사 하 여 디버그 힙 관리자에 의해 할당 된 메모리의 유효성을 검사 합니다. 기본 힙, 디버그 헤더 정보 또는 덮어쓰기 버퍼에서 오류 또는 메모리 불일치가 발생 하면 **_CrtCheckMemory** 는 오류 조건을 설명 하는 정보가 포함 된 디버그 보고서를 생성 합니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtCheckMemory** 대 한 호출이 제거 됩니다.

[_CrtSetDbgFlag](crtsetdbgflag.md) 함수를 사용 하 여 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 플래그의 비트 필드를 설정 하 여 **_CrtCheckMemory** 의 동작을 제어할 수 있습니다. **_CRTDBG_CHECK_ALWAYS_DF** 비트 필드를 켜면 메모리 할당 작업이 요청 될 때마다 호출 되는 **_CrtCheckMemory** . 이 메서드는 실행 속도를 늦추지만, 오류를 신속하게 catch하는 데 유용합니다. **_CRTDBG_ALLOC_MEM_DF** 비트 필드를 OFF로 설정 하면 **_CrtCheckMemory** 힙을 확인 하지 않고 즉시 **TRUE** 를 반환 합니다.

이 함수는 **TRUE** 또는 **FALSE** 를 반환 하므로 [_ASSERT](assert-asserte-assert-expr-macros.md) 매크로 중 하나로 전달 하 여 간단한 디버깅 오류 처리 메커니즘을 만들 수 있습니다. 다음 예제에서는 힙에서 손상이 검색된 경우 어설션 실패가 발생합니다.

```C
_ASSERTE( _CrtCheckMemory( ) );
```

다른 디버그 함수와 함께 **_CrtCheckMemory** 를 사용 하는 방법에 대 한 자세한 내용은 [힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)를 참조 하세요. 메모리 관리 및 디버그 힙의 개요는 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

**_CrtCheckMemory** 사용 방법에 대 한 샘플은 [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
