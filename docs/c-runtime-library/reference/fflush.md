---
description: '자세히 알아보기: fflush'
title: fflush
ms.date: 4/2/2020
api_name:
- fflush
- _o_fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: a23b4f580e0ed258bb111064b8564a6603562f64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289259"
---
# <a name="fflush"></a>fflush

스트림을 플러시합니다.

## <a name="syntax"></a>구문

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

## <a name="return-value"></a>반환 값

버퍼가 성공적으로 플러시되 면 **fflush** 는 0을 반환 합니다. 지정된 스트림에 버퍼가 없거나 해당 스트림이 읽기 전용으로 열린 경우에도 값 0이 반환됩니다. **EOF** 의 반환 값은 오류를 나타냅니다.

> [!NOTE]
> **Fflush** 가 **EOF** 를 반환 하는 경우 쓰기 오류로 인해 데이터가 손실 되었을 수 있습니다. 심각한 오류 처리기를 설정 하는 경우 **setvbuf** 함수를 사용 하 여 버퍼링을 해제 하거나 스트림 i/o 함수 대신 **_open**, **_close** 및 **_write** 와 같은 하위 수준 i/o 루틴을 사용 하는 것이 가장 안전 합니다.

## <a name="remarks"></a>설명

**Fflush** 함수는 스트림 *스트림을* 플러시합니다. 스트림이 쓰기 모드에서 열렸거나 업데이트 모드에서 열리고 마지막 작업이 쓰기였던 경우 스트림 버퍼의 콘텐츠가 기본 파일 또는 디바이스에 기록되고 버퍼가 삭제됩니다. 스트림이 읽기 모드에서 열리거나 스트림에 버퍼가 없는 경우 **fflush** 에 대 한 호출은 아무런 효과가 없으며 모든 버퍼가 유지 됩니다. **Fflush** 에 대 한 호출은 스트림의 **ungetc** 에 대 한 이전 호출의 결과를 부정 합니다. 스트림은 호출 후에 열려 있습니다.

*Stream* 이 **NULL** 이면 각 열린 스트림에 대해 **fflush** 를 호출 하는 것과 동작이 동일 합니다. 쓰기 모드로 열린 모든 스트림과 마지막 작업이 쓰기인 업데이트 모드로 열린 모든 스트림이 플러시됩니다. 이 호출은 다른 스트림에 영향을 미치지 않습니다.

버퍼는 보통 운영 체제에서 유지 관리됩니다. 운영 체제에서는 버퍼가 가득 찼을 때, 스트림이 닫혀 있을 때, 스트림을 닫지 않고 프로그램이 정상적으로 종료될 때 등 디스크에 데이터를 자동으로 쓰는 최적의 시간을 결정합니다. 런타임 라이브러리의 디스크에 커밋 기능을 사용하면 중요한 데이터가 운영 체제 버퍼 대신 디스크에 직접 기록되어 있는지 확인할 수 있습니다. 기존 프로그램을 다시 작성하지 않고 프로그램의 개체 파일을 COMMODE.OBJ에 연결하여 이 기능을 사용할 수 있습니다. 결과 실행 파일에서를 호출 하면 모든 버퍼의 내용이 디스크에 기록 **_flushall** . **_Flushall** 및 **FFLUSH** 만 commode .obj의 영향을 받습니다.

디스크에 커밋 기능을 제어하는 방법에 대한 자세한 내용은 [스트림 I/O](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) 및 [_fdopen](fdopen-wfdopen.md)을 참조하세요.

이 함수는 호출 스레드를 잠그므로 스레드로부터 안전합니다. 잠기지 않는 버전은 **_fflush_nolock** 를 참조 하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_fflush.c
// Compile with: cl /W4 crt_fflush.c
// This sample gets a number from the user, then writes it to a file.
// It ensures the write isn't lost on crash by calling fflush.
#include <stdio.h>

int * crash_the_program = 0;

int main(void)
{
    FILE * my_file;
    errno_t err = fopen_s(&my_file, "myfile.txt", "w");
    if (my_file && !err)
    {
        printf("Write a number: ");

        int my_number = 0;
        scanf_s("%d", &my_number);

        fprintf(my_file, "User selected %d\n", my_number);

        // Write data to a file immediately instead of buffering.
        fflush(my_file);

        if (my_number == 5)
        {
            // Without using fflush, no data was written to the file
            // prior to the crash, so the data is lost.
            *crash_the_program = 5;
        }

        // Normally, fflush is not needed as closing the file will write the buffer.
        // Note that files are automatically closed and flushed during normal termination.
        fclose(my_file);
    }
    return 0;
}
```

```Input
5
```

```myfile.txt
User selected 5
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
