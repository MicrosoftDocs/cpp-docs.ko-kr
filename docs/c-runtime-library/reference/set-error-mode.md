---
description: '다음에 대 한 자세한 정보: _set_error_mode'
title: _set_error_mode
ms.date: 11/04/2016
api_name:
- _set_error_mode
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: f21983702adb0ae080443e5869485fe581a65f85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334086"
---
# <a name="_set_error_mode"></a>_set_error_mode

프로그램이 종료 될 수 있는 오류에 대해 C 런타임이 오류 메시지를 기록 하는 기본이 아닌 위치를 확인 하기 위해 **__error_mode** 를 수정 합니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>매개 변수

*mode_val*<br/>
오류 메시지의 대상입니다.

## <a name="return-value"></a>반환 값

오류가 발생하면 이전 설정 또는 -1을 반환합니다.

## <a name="remarks"></a>설명

**__Error_mode** 값을 설정 하 여 오류 출력 싱크를 제어 합니다. 예를 들어 출력을 표준 오류로 보내거나 **MessageBox** API를 사용할 수 있습니다.

*Mode_val* 매개 변수는 다음 값 중 하나로 설정할 수 있습니다.

|값|설명|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|오류 싱크는 **__app_type** 에 의해 결정 됩니다.|
|**_OUT_TO_STDERR**|오류 싱크가 표준 오류입니다.|
|**_OUT_TO_MSGBOX**|오류 싱크가 메시지 상자입니다.|
|**_REPORT_ERRMODE**|현재 **__error_mode** 값을 보고 합니다.|

나열된 값 이외의 값이 전달되면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 해 서 실행 하도록 허용한 경우 **_set_error_mode** 는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

[Assert](assert-macro-assert-wassert.md)와 함께 사용 하는 경우 **_set_error_mode** 는 대화 상자에 실패 한 문을 표시 하 고 프로그램을 계속 실행할 수 있도록 **무시** 단추를 선택할 수 있는 옵션을 제공 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_set_error_mode**|\<stdlib.h>|

## <a name="example"></a>예제

```C
// crt_set_error_mode.c
// compile with: /c
#include <stdlib.h>
#include <assert.h>

int main()
{
   _set_error_mode(_OUT_TO_STDERR);
   assert(2+2==5);
}
```

```Output
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>참고 항목

[assert 매크로, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
