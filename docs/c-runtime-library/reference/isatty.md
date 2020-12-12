---
description: '다음에 대 한 자세한 정보: _isatty'
title: _isatty
ms.date: 4/2/2020
api_name:
- _isatty
- _o__isatty
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
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: 354cb0ba66c0c25291626cf4278935571357d058
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303624"
---
# <a name="_isatty"></a>_isatty

파일 설명자가 문자 디바이스와 연결되어 있는지 여부를 확인합니다.

## <a name="syntax"></a>구문

```C
int _isatty( int fd );
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
테스트할 디바이스를 나타내는 파일 설명자입니다.

## <a name="return-value"></a>반환 값

설명자가 문자 장치와 연결 되어 있으면 **_isatty** 은 0이 아닌 값을 반환 합니다. 그렇지 않으면 **_isatty** 0을 반환 합니다.

## <a name="remarks"></a>설명

**_Isatty** 함수는 *fd* 가 문자 장치 (터미널, 콘솔, 프린터 또는 직렬 포트)와 연결 되어 있는지 여부를 확인 합니다.

이 함수는 *fd* 매개 변수의 유효성을 검사 합니다. *Fd* 가 잘못 된 파일 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 함수는 0을 반환 하 고 **errno** 를 **ebadf** 로 설정 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_isatty**|\<io.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>샘플 출력

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
