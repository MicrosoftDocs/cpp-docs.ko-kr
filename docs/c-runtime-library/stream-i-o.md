---
description: '자세한 정보: 스트림 i/o'
title: 스트림 I/O
ms.date: 11/04/2016
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
ms.openlocfilehash: a787d83390239679ad48c2ca09b41f567a0a8c95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235673"
---
# <a name="stream-io"></a>스트림 I/O

이러한 함수는 단일 문자에서 대형 데이터 구조체에 이르기까지 다양한 크기 및 형식의 데이터를 처리합니다. 또한 버퍼링을 제공하여 성능을 향상시킬 수 있습니다. 스트림 버퍼의 기본 크기는 4K입니다. 이러한 루틴은 런타임 라이브러리 루틴에 의해 생성된 버퍼에만 영향을 주며 운영 체제에서 생성된 버퍼에는 영향을 주지 않습니다.

## <a name="stream-io-routines"></a>스트림 I/O 루틴

|루틴에서 반환된 값|기능|
|-------------|---------|
|[clearerr](../c-runtime-library/reference/clearerr.md), [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|스트림 오류 표시기를 지웁니다.|
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|스트림을 닫습니다.|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|**stdin**, **stdout** 및 **stderr** 을 제외한 열려 있는 모든 스트림을 닫습니다.|
|[_fdopen, wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|열려 있는 파일의 파일 설명자에 스트림을 연결합니다.|
|[feof](../c-runtime-library/reference/feof.md)|스트림에서 파일의 끝을 테스트합니다.|
|[ferror](../c-runtime-library/reference/ferror.md)|스트림에서 오류를 테스트합니다.|
|[fflush](../c-runtime-library/reference/fflush.md)|스트림을 버퍼 또는 스토리지 디바이스로 플러시합니다.|
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|스트림에서 문자를 읽습니다(**getc** 및 **getwc** 의 함수 버전).|
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|**stdin** 에서 문자를 읽습니다(**getchar** 및 **getwchar** 의 함수 버전).|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|스트림 위치 표시기를 가져옵니다.|
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|스트림에서 문자열을 읽습니다.|
|[_fileno](../c-runtime-library/reference/fileno.md)|스트림과 연결된 파일 설명자를 가져옵니다.|
|[_flushall](../c-runtime-library/reference/flushall.md)|모든 스트림을 버퍼 또는 스토리지 디바이스로 플러시합니다.|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|스트림을 엽니다.|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|스트림에 형식이 지정된 데이터를 씁니다.|
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|문자를 스트림에 씁니다(**putc** 및 **putwc** 의 함수 버전).|
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|문자를 **stdout** 에 씁니다(**putchar** 및 **putwchar** 의 함수 버전).|
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|스트림에 문자열을 씁니다.|
|[fread](../c-runtime-library/reference/fread.md)|스트림에서 형식이 지정되지 않은 데이터를 읽습니다.|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|**FILE** 스트림 포인터를 새 파일 또는 디바이스에 다시 할당합니다.|
|[fscanf, fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|스트림에서 형식이 지정된 데이터를 읽습니다.|
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|파일 위치를 지정된 위치로 이동합니다.|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|스트림 위치 표시기를 설정합니다.|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|파일 공유를 사용한 스트림을 엽니다.|
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|현재 파일 위치를 가져옵니다.|
|[fwrite](../c-runtime-library/reference/fwrite.md)|스트림에 형식이 지정되지 않은 데이터 항목을 씁니다.|
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|스트림에서 문자를 읽습니다(**fgetc** 및 **fgetwc** 의 매크로 버전).|
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|**stdin** 에서 문자를 읽습니다(**fgetchar** 및 **fgetwchar** 의 매크로 버전).|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|스트림 I/O 수준에서 허용되는 동시에 열리는 파일 수를 반환합니다.|
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|**stdin** 에서 줄을 읽습니다.|
|[_getw](../c-runtime-library/reference/getw.md)|스트림에서 이진 읽기 **`int`**|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|서식이 지정된 데이터를 **stdout** 에 씁니다.|
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|문자를 스트림에 씁니다(**fputc** 및 **fputwc** 의 매크로 버전).|
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|문자를 **stdout** 에 씁니다(**fputchar** 및 **fputwchar** 의 매크로 버전).|
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|스트림에 줄을 씁니다.|
|[_putw](../c-runtime-library/reference/putw.md)|스트림에 이진 쓰기 **`int`**|
|[되감습니다](../c-runtime-library/reference/rewind.md)|파일 위치를 스트림의 시작 부분으로 이동합니다.|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|**tmpfile** 에서 만든 임시 파일을 제거합니다.|
|[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|**stdin** 에서 서식이 지정된 데이터를 읽습니다.|
|[setbuf](../c-runtime-library/reference/setbuf.md)|스트림 버퍼링을 제어합니다.|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|스트림 I/O 수준에서 동시에 열려 있는 파일 수의 최대값을 설정합니다.|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|스트림 버퍼링 및 버퍼 크기를 제어합니다.|
|[_snprintf, _snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|문자열에 지정된 길이의 형식이 지정된 데이터를 씁니다.|
|[_snscanf, _snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|표준 입력 스트림에서 지정된 길이의 형식이 지정된 데이터를 읽습니다.|
|[sprintf, swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|문자열에 형식이 지정된 데이터를 씁니다.|
|[sscanf, swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|문자열에서 형식이 지정된 데이터를 읽습니다.|
|[_tempnam, _wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|지정된 디렉터리에 임시 파일 이름을 생성합니다.|
|[tmpfile](../c-runtime-library/reference/tmpfile.md), [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|임시 파일을 만듭니다.|
|[tmpnam, _wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md), [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|임시 파일 이름을 생성합니다.|
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|스트림으로 문자를 다시 푸시합니다.|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|콘솔에 형식이 지정된 데이터를 씁니다.|
|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|스트림에 형식이 지정된 데이터를 씁니다.|
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|서식이 지정된 데이터를 **stdout** 에 씁니다.|
|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|버퍼에 지정된 길이의 형식이 지정된 데이터를 씁니다.|
|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|버퍼에 형식이 지정된 데이터를 씁니다.|

프로그램 실행이 시작되면 시작 코드에서 여러 스트림, 즉 표준 입력(**stdin** 에서 지시), 표준 출력(**stdout** 에서 지시)과 표준 오류(**stderr** 에서 지시)를 자동으로 엽니다. 이러한 스트림은 기본적으로 콘솔(키보드 및 화면)으로 전송됩니다. **freopen** 을 사용하여 **stdin**, **stdout** 또는 **stderr** 을 디스크 파일 또는 디바이스로 리디렉션합니다.

스트림 루틴을 사용하여 열린 파일은 기본적으로 버퍼링됩니다. **stdout** 및 **stderr** 함수는 가득 찰 때마다 또는 문자 입출력 디바이스에 쓰는 경우 각 라이브러리 호출 후에 플러시됩니다. 프로그램이 비정상적으로 종료되면 출력 버퍼가 플러시되지 않아 데이터 손실이 발생할 수 있습니다. **fflush** 또는 **_flushall** 을 사용하여 지정된 파일과 연결된 버퍼 또는 열려 있는 모든 버퍼가 운영 체제로 플러시되도록 합니다. 그러면 디스크에 쓰기 전에 데이터를 캐시할 수 있습니다. 디스크에 커밋 기능은 시스템 오류 발생 시 플러시된 버퍼 내용이 손실되지 않도록 합니다.

버퍼 내용을 디스크에 커밋하는 방법에는 다음 두 가지가 있습니다.

- COMMODE.OBJ 파일에 연결하여 전역 커밋 플래그를 설정합니다. 전역 플래그의 기본 설정은 **n**("커밋 안 함")입니다.

- **fopen** 또는 **_fdopen** 을 사용하여 모드 플래그를 **c** 로 설정합니다.

**c** 또는 **n** 플래그를 사용하여 특별히 열린 파일은 전역 커밋/커밋 안 함 플래그 상태에 관계없이 플래그에 따라 동작합니다.

프로그램이 명시적으로 스트림을 닫지 않을 경우 프로그램이 종료되면 스트림이 자동으로 닫힙니다. 그러나 한 번에 열려 있을 수 있는 스트림 수가 제한되므로 프로그램이 작업을 마치면 스트림을 닫아야 합니다. 이 제한에 대한 자세한 내용은 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) 를 참조하세요.

**fflush** 또는 파일 위치 지정 함수(**fseek**, **fsetpos** 또는 **rewind**)에 대한 중간 호출을 통해서만 입력에서 출력을 직접 따라갈 수 있습니다. 입력 작업이 파일의 끝을 발견할 경우 파일 위치 지정 함수에 대한 중간 호출 없이 출력이 입력을 따를 수 있습니다.

## <a name="see-also"></a>참고 항목

[입력 및 출력](../c-runtime-library/input-and-output.md)<br/>
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
