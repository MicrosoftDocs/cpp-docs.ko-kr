---
description: '다음에 대 한 자세한 정보: _CrtSetDumpClient'
title: _CrtSetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: 89a2648aae62fc7f62b04519eacce4e0f67002f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319536"
---
# <a name="_crtsetdumpclient"></a>_CrtSetDumpClient

**_CLIENT_BLOCK** 형식 메모리 블록을 덤프 하는 응용 프로그램 정의 함수를 설치 합니다 (디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>매개 변수

*클라이언트 \ 클라이언트*<br/>
C 런타임 디버그 메모리 덤프 프로세스에 연결할 새로운 클라이언트 정의 메모리 덤프 함수입니다.

## <a name="return-value"></a>반환 값

이전에 정의된 클라이언트 블록 덤프 함수를 반환합니다.

## <a name="remarks"></a>설명

**_CrtSetDumpClient** 함수를 사용 하면 응용 프로그램에서 자체 함수를 사용 하 여 **_CLIENT_BLOCK** 메모리 블록에 저장 된 개체를 C 런타임 디버그 메모리 덤프 프로세스에 연결할 수 있습니다. 따라서 [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) 또는 [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) 같은 디버그 덤프 함수가 **_CLIENT_BLOCK** 메모리 블록을 덤프할 때마다 응용 프로그램의 dump 함수도 호출 됩니다. **_CrtSetDumpClient** 는 메모리 누수를 탐지 하 고 **_CLIENT_BLOCK** 블록에 저장 된 데이터의 내용을 확인 하거나 보고 하는 쉬운 방법을 응용 프로그램에 제공 합니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtSetDumpClient** 대 한 호출이 제거 됩니다.

**_CrtSetDumpClient** 함수는 덤프 *클라이언트* 에 지정 된 새 응용 프로그램 정의 덤프 함수를 설치 하 고 이전에 정의 된 덤프 함수를 반환 합니다. 클라이언트 블록 덤프 함수의 예제는 다음과 같습니다.

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

*Userportion* 인수는 메모리 블록의 사용자 데이터 부분에 대 한 포인터 *이 고 블록* 크기는 할당 된 메모리 블록의 크기 (바이트)를 지정 합니다. 클라이언트 블록 덤프 함수는를 반환 해야 합니다 **`void`** . **_CrtSetDumpClient** 에 전달 되는 클라이언트 덤프 함수에 대 한 포인터는 crtdbg.h에 정의 된 **_CRT_DUMP_CLIENT** 형식입니다.

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

**_CLIENT_BLOCK** 형식 메모리 블록에 대해 작동 하는 함수에 대 한 자세한 내용은 [클라이언트 블록 후크 함수](/visualstudio/debugger/client-block-hook-functions)를 참조 하세요. [_CrtReportBlockType](crtreportblocktype.md) 함수는 블록 형식과 하위 형식에 대한 정보를 반환하는 데 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
