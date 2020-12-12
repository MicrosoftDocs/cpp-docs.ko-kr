---
description: '다음에 대 한 자세한 정보: _CrtIsValidHeapPointer'
title: _CrtIsValidHeapPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidHeapPointer
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
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
ms.openlocfilehash: 71a281cdf63ad1c37162da1b1be099764085f739
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319705"
---
# <a name="_crtisvalidheappointer"></a>_CrtIsValidHeapPointer

지정된 포인터가 일부 C 런타임 라이브러리에서 할당된 힙에 있는지 확인하지만 호출자의 CRT 라이브러리에서 할당된 힙에 있는지는 확인하지 않을 수 있습니다. Visual Studio 2010 이전 CRT 버전에서 이 멤버는 지정된 포인터가 로컬 힙에 있는지 확인합니다(디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
int _CrtIsValidHeapPointer(
   const void *userData
);
```

### <a name="parameters"></a>매개 변수

*Data*<br/>
할당된 메모리 블록의 시작 부분에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

지정 된 포인터가 모든 CRT 라이브러리 인스턴스에서 공유 되는 힙에 있으면 **_CRTISVALIDHEAPPOINTER** TRUE를 반환 합니다. Visual Studio 2010 이전 CRT 버전에서 이 멤버는 지정된 포인터가 로컬 힙에 있으면 true를 반환합니다. 그렇지 않은 경우 이 함수는 FALSE를 반환합니다.

## <a name="remarks"></a>설명

이 함수는 사용하지 않는 것이 좋습니다. Visual Studio 2010 CRT 라이브러리부터 모든 CRT 라이브러리에서는 하나의 OS 힙인 *프로세스 힙* 을 공유합니다. **_CrtIsValidHeapPointer** 함수는 포인터가 crt 힙에서 할당 되었는지 여부를 보고 하지만 호출자의 crt 라이브러리에서 할당 되었는지는 보고 하지 않습니다. 예를 들어 CRT 라이브러리의 Visual Studio 2010 버전을 사용하여 할당된 블록을 살펴보겠습니다. CRT 라이브러리의 Visual Studio 2012 버전에서 내보낸 **_CrtIsValidHeapPointer** 함수가 포인터를 테스트 하는 경우 TRUE를 반환 합니다. 이 테스트는 더 이상 유용한 테스트가 아닙니다. Visual Studio 2010 이전 CRT 라이브러리 버전에서 이 함수는 특정 메모리 주소가 로컬 힙 내에 있는지 확인하는 데 사용됩니다. 로컬 힙은 C 런타임 라이브러리의 특정 인스턴스에서 만들어지고 관리되는 힙을 나타냅니다. DLL(동적 연결 라이브러리)에는 런타임 라이브러리에 대한 정적 링크가 들어 있으면 애플리케이션의 로컬 힙과 관계없이 런타임 힙의 고유한 인스턴스가 포함되고 이에 따라 고유한 힙이 포함됩니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtIsValidHeapPointer** 대 한 호출이 제거 됩니다.

이 함수는 TRUE 또는 FALSE를 반환하므로 이를 [_ASSERT](assert-asserte-assert-expr-macros.md) 매크로 중 하나로 전달하여 간단한 디버깅 오류 처리 메커니즘을 만들 수 있습니다. 다음 예제에서는 지정된 주소가 로컬 힙 내에 없을 경우 어설션 오류가 발생하는 경우를 보여 줍니다.

```C
_ASSERTE( _CrtIsValidHeapPointer( userData ) );
```

다른 디버그 함수 및 매크로와 **_CrtIsValidHeapPointer** 를 사용 하는 방법에 대 한 자세한 내용은 [보고 매크로](/visualstudio/debugger/macros-for-reporting)를 참조 하세요. 기본 힙의 디버그 버전에서 메모리 블록을 할당, 초기화 및 관리하는 방법에 대한 자세한 내용은 [CRT 디버그 힙 정보](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_CrtIsValidHeapPointer**|\<crtdbg.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

[C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)의 디버그 버전만 해당됩니다.

## <a name="example"></a>예제

다음 예제에서는 메모리가 Visual Studio 2010 이전 C 런타임 라이브러리에서 사용될 때 유효한지 테스트하는 방법을 보여 줍니다. 이 예제는 레거시 CRT 라이브러리 코드 사용자를 위해 제공됩니다.

```C
// crt_isvalid.c
// This program allocates a block of memory using _malloc_dbg
// and then tests the validity of this memory by calling
// _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

#define  TRUE   1
#define  FALSE  0

int main( void )
{
    char *my_pointer;

    // Call _malloc_dbg to include the filename and line number
    // of our allocation request in the header information
    my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,
        _NORMAL_BLOCK, __FILE__, __LINE__ );

    // Ensure that the memory got allocated correctly
    _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,
        NULL, NULL, NULL );

    // Test for read/write accessibility
    if (_CrtIsValidPointer((const void *)my_pointer,
        sizeof(char) * 10, TRUE))
        printf("my_pointer has read and write accessibility.\n");
    else
        printf("my_pointer only has read access.\n");

    // Make sure my_pointer is within the local heap
    if (_CrtIsValidHeapPointer((const void *)my_pointer))
        printf("my_pointer is within the local heap.\n");
    else
        printf("my_pointer is not located within the local"
               " heap.\n");

    free(my_pointer);
}
```

```Output
my_pointer has read and write accessibility.
my_pointer is within the local heap.
```

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
