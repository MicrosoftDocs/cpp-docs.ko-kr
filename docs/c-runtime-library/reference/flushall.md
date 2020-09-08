---
title: _flushall
description: _Flushall에 대 한 API 참조 모든 스트림을 플러시하고 모든 버퍼를 지웁니다.
ms.date: 4/2/2020
api_name:
- _flushall
- _o__flushall
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
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: c93dddea50c182b86bd4d09ae9f214e87491e830
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556725"
---
# <a name="_flushall"></a>_flushall

모든 스트림을 플러시하고 모든 버퍼를 지웁니다.

## <a name="syntax"></a>구문

```C
int _flushall( void );
```

## <a name="return-value"></a>Return Value

**_flushall** 은 열려 있는 스트림 (입력 및 출력)의 수를 반환 합니다. 오류가 반환 되지 않습니다.

## <a name="remarks"></a>설명

기본적으로 **_flushall** 함수는 열려 있는 출력 스트림과 연결 된 모든 버퍼의 내용을 해당 파일에 씁니다. 열려 있는 입력 스트림과 연결된 모든 버퍼에서 현재 내용이 지워집니다. 이 버퍼는 대개 자동으로 디스크에 데이터를 쓸 수 있는 최적의 시간을 결정하는 운영 체제에서 유지 관리됩니다. 버퍼가 채워졌을 때 스트림이 닫히거나 스트림을 닫지 않고 프로그램이 정상적으로 종료됩니다.

읽기 **_flushall**에 대 한 호출을 수행 하면 입력 파일에서 버퍼로 새 데이터를 읽습니다. **_Flushall**를 호출한 후에는 모든 스트림이 열린 상태로 유지 됩니다.

런타임 라이브러리의 디스크에 커밋 기능을 사용하면 중요한 데이터가 운영 체제 버퍼 대신 디스크에 직접 기록되어 있는지 확인할 수 있습니다. 기존 프로그램을 다시 작성 하지 않고 프로그램의 개체 파일을 Commode와 연결 하 여이 기능을 사용 하도록 설정할 수 있습니다. 결과 실행 파일에서를 호출 하면 모든 버퍼의 내용이 디스크에 기록 **_flushall** . **_Flushall** 및 [Fflush](fflush.md) 만 commode .obj의 영향을 받습니다.

디스크에 커밋 기능을 제어하는 방법에 대한 자세한 내용은 [스트림 I/O](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) 및 [_fdopen](fdopen-wfdopen.md)을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|기능|필수 헤더|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
