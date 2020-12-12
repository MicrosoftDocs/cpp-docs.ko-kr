---
description: '다음에 대 한 자세한 정보: _get_fmode'
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: 56716b7e8c12c5a3de79098a8227be31148ae386
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303650"
---
# <a name="_get_fmode"></a>_get_fmode

파일 I/O 연산에 대한 기본 파일 변환 모드를 가져옵니다.

## <a name="syntax"></a>구문

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>매개 변수

*pmode*<br/>
**_O_TEXT** 또는 **_O_BINARY** 현재 기본 모드로 채워질 정수에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

성공하는 경우 0을 반환하고, 실패하는 경우 오류 코드를 반환합니다. *Pmode* 가 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 는 **EINVAL** 로 설정 되 고 함수는 **EINVAL** 를 반환 합니다.

## <a name="remarks"></a>설명

이 함수는 [_fmode](../../c-runtime-library/fmode.md) 전역 변수의 값을 가져옵니다. 이 변수는 **_open**, **_pipe**, **fopen** 및 [freopen](freopen-wfreopen.md)과 같은 하위 수준 및 스트림 파일 i/o 작업에 대 한 기본 파일 변환 모드를 지정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_set_fmode](set-fmode.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[텍스트 및 이진 모드 파일 i/o](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
