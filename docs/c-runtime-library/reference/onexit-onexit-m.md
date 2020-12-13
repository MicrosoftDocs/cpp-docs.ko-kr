---
description: '자세히 알아보기: _onexit, _onexit_m'
title: _onexit, _onexit_m
ms.date: 11/04/2016
api_name:
- _onexit
- _onexit_m
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
- _onexit
- onexit_m
- onexit
- _onexit_m
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
ms.openlocfilehash: 0b79c521b04a4cb1597dda7c7ed2a19ae2dcf905
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151699"
---
# <a name="_onexit-_onexit_m"></a>_onexit, _onexit_m

종료 시 호출할 루틴을 등록합니다.

## <a name="syntax"></a>구문

```C
_onexit_t _onexit(
   _onexit_t function
);
_onexit_t_m _onexit_m(
   _onexit_t_m function
);
```

### <a name="parameters"></a>매개 변수

*function*<br/>
종료 시 호출할 함수에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

성공 하면 **_onexit** 함수에 대 한 포인터를 반환 하 고, 함수 포인터를 저장할 공간이 없는 경우 **NULL** 을 반환 합니다.

## <a name="remarks"></a>설명

**_Onexit** 함수는 프로그램이 정상적으로 종료 될 때 호출 되는 함수 (*함수*)의 주소를 전달 합니다. **_Onexit** 에 대 한 연속 호출은 LIFO (last in first out) 순서로 실행 되는 함수의 레지스터를 만듭니다. **_Onexit** 에 전달 된 함수는 매개 변수를 사용할 수 없습니다.

DLL 내에서 **_onexit** 를 호출 하는 경우 DLL_PROCESS_DETACH를 사용 하 여 **DllMain** 이 호출 된 후에 **_ONEXIT** 에 등록 된 루틴이 dll의 언로드에서 실행 됩니다.

**_onexit** 는 Microsoft 확장입니다. ANSI 이식성이 필요한 경우에는 [atexit](atexit.md)을 사용하세요. 함수의 **_onexit_m** 버전은 혼합 모드 사용을 위한 것입니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_onexit.c

#include <stdlib.h>
#include <stdio.h>

/* Prototypes */
int fn1(void), fn2(void), fn3(void), fn4 (void);

int main( void )
{
   _onexit( fn1 );
   _onexit( fn2 );
   _onexit( fn3 );
   _onexit( fn4 );
   printf( "This is executed first.\n" );
}

int fn1()
{
   printf( "next.\n" );
   return 0;
}

int fn2()
{
   printf( "executed " );
   return 0;
}

int fn3()
{
   printf( "is " );
   return 0;
}

int fn4()
{
   printf( "This " );
   return 0;
}
```

### <a name="output"></a>출력

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>참조

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
