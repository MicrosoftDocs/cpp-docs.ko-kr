---
description: '다음에 대 한 자세한 정보: _matherr'
title: _matherr
ms.date: 04/05/2018
api_name:
- _matherr
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
- _matherr
- matherr
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: 406f9fe43ed64b24637f94cc5bf1ef01d4c94567
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299633"
---
# <a name="_matherr"></a>_matherr

수학 오류를 처리합니다.

## <a name="syntax"></a>구문

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>매개 변수

*남기고*<br/>
오류 정보를 포함하는 구조에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

**_matherr** 는 오류를 나타내는 0을 반환 하 고 성공 여부를 나타내는 0이 아닌 값을 반환 합니다. **_Matherr** 에서 0을 반환 하는 경우 오류 메시지가 표시 되 고 **errno** 가 적절 한 오류 값으로 설정 됩니다. **_Matherr** 0이 아닌 값을 반환 하는 경우에는 오류 메시지가 표시 되지 않고 **errno** 는 변경 되지 않은 상태로 유지 됩니다.

반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Matherr** 함수는 수학 라이브러리의 부동 소수점 함수에 의해 생성 된 오류를 처리 합니다. 이러한 함수는 오류가 검색 될 때 **_matherr** 를 호출 합니다.

특수 한 오류 처리를 위해 다른 **_matherr** 정의를 제공할 수 있습니다. 동적으로 연결 된 CRT (C 런타임 라이브러리) 버전을 사용 하는 경우 클라이언트 실행 파일에서 기본 **_matherr** 루틴을 사용자 정의 버전으로 바꿀 수 있습니다. 그러나 CRT DLL의 DLL 클라이언트에서 기본 **_matherr** 루틴을 대체할 수는 없습니다.

수학 루틴에서 오류가 발생 하면 **_matherr** 는에 정의 된 **_exception** 형식 구조체에 대 한 포인터를 인수로 사용 하 여 호출 됩니다 \<math.h> . **_exception** 구조체에는 다음 요소가 포함되어 있습니다.

```C
struct _exception
{
    int    type;   // exception type - see below
    char*  name;   // name of function where error occurred
    double arg1;   // first argument to function
    double arg2;   // second argument (if any) to function
    double retval; // value to be returned by function
};
```

**형식** 멤버는 수학 오류의 유형을 지정 합니다. 에 정의 된 다음 값 중 하나입니다 \<math.h> .

|매크로|의미|
|-|-|
| **_DOMAIN** | 인수 도메인 오류 |
| **_SING** | 인수 특이성 |
| **_OVERFLOW** | 오버플로 범위 오류 |
| **_PLOSS** | 중요 한 부분 손실 |
| **_TLOSS** | 중요 한 총 손실 |
| **_UNDERFLOW** | 결과가 너무 작아 나타낼 수 없습니다. 이 조건은 현재 지원되지 않습니다. |

구조체 멤버 **name** 은 오류를 발생시킨 함수의 이름을 포함하는 null로 종료되는 문자열에 대한 포인터입니다. 구조체 멤버 **arg1** 및 **arg2** 는 오류를 발생시킨 값을 지정합니다. 인수가 하나만 지정 된 경우 **arg1** 에 저장 됩니다.

지정된 오류의 기본 반환 값은 **retval** 입니다. 반환 값을 변경하는 경우 오류가 실제로 발생했는지 여부를 해당 값이 지정해야 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_matherr**|\<math.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_matherr.c
/* illustrates writing an error routine for math
* functions. The error function must be:
*      _matherr
*/

#include <math.h>
#include <string.h>
#include <stdio.h>

int main()
{
    /* Do several math operations that cause errors. The _matherr
     * routine handles _DOMAIN errors, but lets the system handle
     * other errors normally.
     */
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );
}

/* Handle several math errors caused by passing a negative argument
* to log or log10 (_DOMAIN errors). When this happens, _matherr
* returns the natural or base-10 logarithm of the absolute value
* of the argument and suppresses the usual error message.
*/
int _matherr( struct _exception *except )
{
    /* Handle _DOMAIN errors for log or log10. */
    if( except->type == _DOMAIN )
    {
        if( strcmp( except->name, "log" ) == 0 )
        {
            except->retval = log( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
        else if( strcmp( except->name, "log10" ) == 0 )
        {
            except->retval = log10( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
    }
    printf( "Normal: " );
    return 0;    /* Else use the default actions */
}
```

```Output
Special: using absolute value: log: _DOMAIN error
log( -2.0 ) = 6.931472e-01
Special: using absolute value: log10: _DOMAIN error
log10( -5.0 ) = 6.989700e-01
Normal: log( 0.0 ) = -inf
```

## <a name="see-also"></a>참고 항목

[부동 소수점 지원](../../c-runtime-library/floating-point-support.md)<br/>
