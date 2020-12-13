---
description: '다음에 대 한 자세한 정보: _heapwalk'
title: _heapwalk
ms.date: 11/04/2016
api_name:
- _heapwalk
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapwalk
- _heapwalk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- heapwalk function
- _heapwalk function
ms.assetid: 2df67649-fb00-4570-a8b1-a4eca5738744
ms.openlocfilehash: 08d877757a443a52a94952032291e69f3466f007
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332777"
---
# <a name="_heapwalk"></a>_heapwalk

힙을 이동하고 다음 항목에 대한 정보를 반환합니다.

> [!IMPORTANT]
> 이 API는 디버그 빌드를 제외하고 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _heapwalk( _HEAPINFO *entryinfo );
```

### <a name="parameters"></a>매개 변수

*entryinfo*<br/>
힙 정보를 포함할 버퍼입니다.

## <a name="return-value"></a>반환 값

**_heapwalk** 는 Malloc에 정의 된 다음 정수 매니페스트 상수 중 하나를 반환 합니다.

|반환 값|의미|
|-|-|
|**_HEAPBADBEGIN**| 초기 헤더 정보가 잘못되었거나 없습니다.|
|**_HEAPBADNODE**| 힙이 손상되었거나 잘못된 노드가 있습니다.|
|**_HEAPBADPTR**| **_HEAPINFO** 구조체의 **_pentry** 필드가 힙에 대 한 올바른 포인터를 포함 하지 않거나 *entryinfo* 가 null 포인터입니다.|
|**_HEAPEND**| 힙 끝에 성공적으로 도달했습니다.|
|**_HEAPEMPTY**| 힙이 초기화되지 않았습니다.|
|**_HEAPOK**| 지금까지 오류가 발생 하지 않습니다. *entryinfo* 는 다음 힙 항목에 대 한 정보로 업데이트 됩니다.|

또한 오류가 발생 하는 경우에는 **_heapwalk** **errno** 를 **ENOSYS** 로 설정 합니다.

## <a name="remarks"></a>설명

**_Heapwalk** 함수는 프로그램에서 힙 관련 문제를 디버그 하는 데 도움이 됩니다. 함수는 힙을 단계별로 진행 하 고, 호출 당 하나의 항목을 순회 하 고, 다음 힙 항목에 대 한 정보를 포함 하는 **_HEAPINFO** 형식의 구조에 대 한 포인터를 반환 합니다. Malloc에 정의 된 **_HEAPINFO** 형식에는 다음 요소가 포함 됩니다.

|필드|의미|
|-|-|
|`int *_pentry`|힙 항목 포인터.|
|`size_t _size`|힙 항목의 크기.|
|`int _useflag`|힙 항목이 사용 중인지 여부를 나타내는 플래그.|

**_HEAPOK** 을 반환 하는 **_heapwalk** 에 대 한 호출은 **_size** 필드에 항목의 크기를 저장 하 고 **_useflag** 필드를 **_FREEENTRY** 또는 **_USEDENTRY** (둘 다 Malloc에 정의 된 상수)로 설정 합니다. 힙의 첫 번째 항목에 대 한이 정보를 가져오려면 **_pentry** 멤버가 **NULL** 인 **_HEAPINFO** 구조체에 대 한 포인터 **_heapwalk** 를 전달 합니다. 운영 체제에서 **_heapwalk**(예: Windows 98)를 지원 하지 않는 경우 함수는 **_HEAPEND** 을 반환 하 고 **errno** 를 **ENOSYS** 로 설정 합니다.

이 함수는 해당 매개 변수의 유효성을 검사합니다. *Entryinfo* 가 null 포인터인 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는 **_HEAPBADPTR** 를 반환 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_heapwalk**|\<malloc.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_heapwalk.c

// This program "walks" the heap, starting
// at the beginning (_pentry = NULL). It prints out each
// heap entry's use, location, and size. It also prints
// out information about the overall state of the heap as
// soon as _heapwalk returns a value other than _HEAPOK
// or if the loop has iterated 100 times.

#include <stdio.h>
#include <malloc.h>

void heapdump(void);

int main(void)
{
    char *buffer;

    heapdump();
    if((buffer = (char *)malloc(59)) != NULL)
    {
        heapdump();
        free(buffer);
    }
    heapdump();
}

void heapdump(void)
{
    _HEAPINFO hinfo;
    int heapstatus;
    int numLoops;
    hinfo._pentry = NULL;
    numLoops = 0;
    while((heapstatus = _heapwalk(&hinfo)) == _HEAPOK &&
          numLoops < 100)
    {
        printf("%8s block at %Fp of size %4.4X\n",
               (hinfo._useflag == _USEDENTRY ? "USED" : "FREE"),
               hinfo._pentry, hinfo._size);
        numLoops++;
    }

    switch(heapstatus)
    {
    case _HEAPEMPTY:
        printf("OK - empty heap\n");
        break;
    case _HEAPEND:
        printf("OK - end of heap\n");
        break;
    case _HEAPBADPTR:
        printf("ERROR - bad pointer to heap\n");
        break;
    case _HEAPBADBEGIN:
        printf("ERROR - bad start of heap\n");
        break;
    case _HEAPBADNODE:
        printf("ERROR - bad node in heap\n");
        break;
    }
}
```

```Output
    USED block at 00310650 of size 0100
    USED block at 00310758 of size 0800
    USED block at 00310F60 of size 0080
    FREE block at 00310FF0 of size 0398
    USED block at 00311390 of size 000D
    USED block at 003113A8 of size 00B4
    USED block at 00311468 of size 0034
    USED block at 003114A8 of size 0039
...
    USED block at 00312228 of size 0010
    USED block at 00312240 of size 1000
    FREE block at 00313250 of size 1DB0
OK - end of heap
```

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapchk](heapchk.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
