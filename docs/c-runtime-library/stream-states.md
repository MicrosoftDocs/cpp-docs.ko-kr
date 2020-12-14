---
description: '자세한 정보: 스트림 상태'
title: 스트림 상태
ms.date: 11/19/2018
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
ms.openlocfilehash: c691c1fd01feb9f78ff0929775505f08cb625ecc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224181"
---
# <a name="stream-states"></a>스트림 상태

스트림의 유효한 상태 및 상태 변화가 다음 그림에 표시됩니다.

![스트림 상태 다이어그램](../c-runtime-library/media/stream.gif "스트림 상태 다이어그램")

각 원은 안정적인 상태를 나타냅니다. 각 줄은 스트림에서 동작하는 함수 호출의 결과로 일어날 수 있는 전환을 나타냅니다. 5개 그룹의 함수가 상태 전환을 일으킬 수 있습니다.

처음 세 그룹의 함수는에 선언 됩니다 \<stdio.h> .

- 바이트 읽기 함수 - [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md), [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fread](../c-runtime-library/reference/fread.md), [fscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getc](../c-runtime-library/reference/getc-getwc.md), [getchar](../c-runtime-library/reference/getc-getwc.md), [gets](../c-runtime-library/gets-getws.md), [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 및 [ungetc](../c-runtime-library/reference/ungetc-ungetwc.md)

- 바이트 쓰기 함수 - [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputc](../c-runtime-library/reference/fputc-fputwc.md), [fputs](../c-runtime-library/reference/fputs-fputws.md), [fwrite](../c-runtime-library/reference/fwrite.md), [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [putc](../c-runtime-library/reference/putc-putwc.md), [putchar](../c-runtime-library/reference/putc-putwc.md), [puts](../c-runtime-library/reference/puts-putws.md), [vfprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) 및 [vprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)

- 위치 함수 - [fflush](../c-runtime-library/reference/fflush.md), [fseek](../c-runtime-library/reference/fseek-fseeki64.md), [fsetpos](../c-runtime-library/reference/fsetpos.md) 및 [rewind](../c-runtime-library/reference/rewind.md)

나머지 두 그룹의 함수는에 선언 됩니다 \<wchar.h> .

- 와이드 읽기 함수 - [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getwc](../c-runtime-library/reference/getc-getwc.md), [getwchar](../c-runtime-library/reference/getc-getwc.md), [ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md) 및 [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)

- 와이드 쓰기 함수 - [fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputwc](../c-runtime-library/reference/fputc-fputwc.md), [fputws](../c-runtime-library/reference/fputs-fputws.md), [putwc](../c-runtime-library/reference/putc-putwc.md), [putwchar](../c-runtime-library/reference/fputc-fputwc.md), [vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md) 및 [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)

상태 다이어그램은 대부분의 쓰기 및 읽기 작업에서 위치 함수 중 하나를 호출해야만 한다는 것을 보여 줍니다.

- 스트림의 마지막 작업이 쓰기이면 읽기 함수를 호출할 수 없습니다.

- 스트림의 마지막 작업이 읽기이고 읽기 작업이 파일 끝 표시기를 설정하지 않은 경우 쓰기 함수를 호출할 수 없습니다.

마지막으로 상태 다이어그램은 위치 작업이 따를 수 있는 유효한 함수 호출 수를 감소시키지 않는다는 것을 보여 줍니다.

## <a name="see-also"></a>참고 항목

[파일 및 스트림](../c-runtime-library/files-and-streams.md)
