---
title: _free_dbg | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _free_dbg
apilocation:
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
apitype: DLLExport
f1_keywords:
- _free_dbg
- free_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa485eea6f0ffda05b0ef33a808d5ec837255514
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400046"
---
# <a name="freedbg"></a>_free_dbg

힙의 메모리 블록을 해제합니다(디버그 버전에만 해당함).

## <a name="syntax"></a>구문

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>매개 변수

*userData* 해제에 할당 된 메모리 블록에 대 한 포인터입니다.

*blockType* 해제 될 할당 된 메모리 블록의 형식: **_CLIENT_BLOCK**, **_NORMAL_BLOCK**, 또는 **_IGNORE_BLOCK**합니다.

## <a name="remarks"></a>설명

**_free_dbg** 함수는 디버그 버전의는 [무료](free.md) 함수입니다. 때 [_DEBUG](../../c-runtime-library/debug.md) 를 정의 하지 않은를 호출할 때마다 **_free_dbg** 에 대 한 호출으로 줄어듭니다 **무료**합니다. 둘 다 **무료** 및 **_free_dbg** 기본 힙에서 메모리 블록 하지만 **_free_dbg** 두 디버깅 기능을 수용: 힙에서 차단 해제 된 상태로 유지 하는 기능 블록 형식 매개 변수로 특정 할당 형식 무료 및 메모리 부족 조건을 시뮬레이션 하는 연결 된 목록입니다.

**_free_dbg** 해제 작업을 수행 하기 전에 지정 된 모든 파일과 블록 위치에 대해 유효성 검사를 수행 합니다. 응용 프로그램에서는 이러한 유효성 검사 정보를 제공하지 않습니다. 메모리 블록이 해제되면 디버그 힙 관리자는 자동으로 사용자 부분 양쪽에 있는 버퍼의 무결성을 확인하며 덮어쓰기가 발생하면 오류 보고서를 만듭니다. 경우는 **_CRTDBG_DELAY_FREE_MEM_DF** 비트 필드는 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 플래그를 설정, 해제 된 블록이 할당 되는 값 0xDD, 채워집니다는 **_FREE_BLOCK** 블록 형식, 및 메모리 블록의 힙 연결된 리스트에 보관합니다.

메모리를 해제에서 오류가 발생 하는 경우 **errno** 오류의 성격에 운영 체제에서 정보를 사용 하 여 설정 합니다. 자세한 내용은 [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요. 할당 블록 형식과 이러한 형식의 사용 방법에 대한 자세한 내용은 [디버그 힙의 블록 형식](/visualstudio/debugger/crt-debug-heap-details)을 참조하세요. 응용 프로그램의 디버그 빌드에서 표준 힙 함수와 이 함수의 디버그 버전을 호출하는 경우의 차이점에 대한 자세한 내용은 [힙 할당 함수의 디버그 버전](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

샘플을 사용 하는 방법에 대 한 **_free_dbg**, 참조 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)합니다.

## <a name="see-also"></a>참고자료

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
