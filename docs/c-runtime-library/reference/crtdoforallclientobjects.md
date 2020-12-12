---
description: '다음에 대 한 자세한 정보: _CrtDoForAllClientObjects'
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
api_name:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 73d2718aa4bfb68752a8424a385638a48aba2e36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319793"
---
# <a name="_crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

힙의 모든 **_CLIENT_BLOCK** 형식에 대해 응용 프로그램에서 제공 하는 함수를 호출 합니다 (디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>매개 변수

*pfn*<br/>
애플리케이션에서 제공하는 함수 콜백 함수에 대한 포인터입니다. 이 함수에 대한 첫 번째 매개 변수는 데이터를 가리킵니다. 두 번째 매개 변수는 **_CrtDoForAllClientObjects** 에 대 한 호출에 전달 되는 컨텍스트 포인터입니다.

*context*<br/>
애플리케이션에서 제공하는 함수에 전달되는 애플리케이션에서 제공하는 컨텍스트에 대한 포인터입니다.

## <a name="remarks"></a>설명

**_CrtDoForAllClientObjects** 함수는 **_CLIENT_BLOCK** 형식의 메모리 블록에 대 한 힙의 연결 된 목록을 검색 하 고이 형식의 블록을 찾으면 응용 프로그램에서 제공 하는 함수를 호출 합니다. 찾은 블록과 *컨텍스트* 매개 변수는 응용 프로그램에서 제공 하는 함수에 인수로 전달 됩니다. 디버깅 하는 동안 응용 프로그램은 디버그 힙 함수를 명시적으로 호출 하 여 메모리를 할당 하 고 블록에 **_CLIENT_BLOCK** 블록 형식을 할당 하도록 지정 하 여 특정 할당 그룹을 추적할 수 있습니다. 그런 다음 이러한 블록을 개별적으로 추적하여 누수 검색 및 메모리 상태 보고 시 다르게 보고할 수 있습니다.

[_CrtDbgFlag](../../c-runtime-library/crtdbgflag.md) 플래그의 **_CRTDBG_ALLOC_MEM_DF** 비트 필드를 설정 하지 않으면 **_CrtDoForAllClientObjects** 즉시 반환 됩니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtDoForAllClientObjects** 대 한 호출이 제거 됩니다.

**_CLIENT_BLOCK** 형식 및 다른 디버그 함수에서 사용할 수 있는 방법에 대 한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조 하세요. 기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

*Pfn* 이 **NULL** 인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용 된 경우 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 가 **EINVAL** 로 설정 되 고 함수는을 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 디버그 버전의 유니버설 C 런타임 라이브러리만 해당합니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
