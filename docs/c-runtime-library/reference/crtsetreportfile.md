---
description: '다음에 대 한 자세한 정보: _CrtSetReportFile'
title: _CrtSetReportFile
ms.date: 11/04/2016
api_name:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: 6b22a76a1a168239210a9f2b93d5cf17d073ec51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206957"
---
# <a name="_crtsetreportfile"></a>_CrtSetReportFile

[_CrtSetReportMode](crtsetreportmode.md) 를 사용 하 여 **_CRTDBG_MODE_FILE** 를 지정한 후에는 메시지 텍스트를 받을 파일 핸들을 지정할 수 있습니다. **_CrtSetReportFile** 는 텍스트의 대상을 지정 하는 [_CrtDbgReportW _CrtDbgReport](crtdbgreport-crtdbgreportw.md) 에도 사용 됩니다 (디버그 버전에만 해당).

## <a name="syntax"></a>구문

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>매개 변수

*reportType*<br/>
보고서 유형: **_CRT_WARN**, **_CRT_ERROR** 및 **_CRT_ASSERT** 합니다.

*reportFile*<br/>
*ReportType* 에 대 한 새 보고서 파일입니다.

## <a name="return-value"></a>반환 값

성공적으로 완료 되 면 **_CrtSetReportFile** *reportType* 에 지정 된 보고서 형식에 대해 정의 된 이전 보고서 파일을 반환 합니다. *ReportType* 에 대해 잘못 된 값이 전달 되 면이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 **errno** 은 **EINVAL** 로 설정 되 고 함수는 **_CRTDBG_HFILE_ERROR** 를 반환 합니다. 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_CrtSetReportFile** 은 [_CrtSetReportMode](crtsetreportmode.md) 함수와 함께 사용 되어 **_CrtDbgReport** 에서 생성 되는 특정 보고서 종류의 대상을 정의 합니다. 특정 보고서 **_CrtSetReportFile** 유형에 대 한 **_CRTDBG_MODE_FILE** 보고 모드를 할당 하기 위해 **_CrtSetReportMode** 를 호출한 경우 대상으로 사용할 특정 파일 또는 스트림을 정의 하기 위해를 호출 해야 합니다. [_DEBUG](../../c-runtime-library/debug.md) 정의 되지 않은 경우 전처리 중에 **_CrtSetReportFile** 대 한 호출이 제거 됩니다.

다음 목록에서는 *Reportfile* 에 사용할 수 있는 선택 항목 및 **_CrtDbgReport** 의 결과 동작을 보여 줍니다. 이러한 옵션은 Crtdbg.h에서 비트 플래그로 정의되어 있습니다.

- **파일 핸들**

   메시지의 대상이 될 파일에 대한 핸들입니다. 핸들의 유효성이 확인되지는 않습니다. 파일에 대한 핸들을 열고 닫아야 합니다. 예를 들어:

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   다음과 같이 리디렉션될 수 있는 **stderr** 에 메시지를 씁니다.

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   사용자가 리디렉션할 수 있는 **stdout** 에 메시지를 씁니다.

- **_CRTDBG_REPORT_FILE**

   현재 보고서 모드를 반환합니다.

각 보고서 형식에 사용되는 보고서 파일을 개별적으로 제어할 수 있습니다. 예를 들어 **_CRT_ERROR** 의 *reportType* 를 **stderr** 로 보고 하 고, *reportType* **_CRT_ASSERT** 사용자 정의 파일 핸들 또는 스트림에 보고 하도록 지정할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

이 콘솔은 UWP (유니버설 Windows 플랫폼) 앱에서 지원 되지 않습니다. 콘솔, **stdin**, **stdout** 및 **stderr** 에 연결 된 표준 스트림 핸들은 C 런타임 함수가 UWP 앱에서 사용할 수 있으려면 먼저 리디렉션해야 합니다. 호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

**라이브러리:** 디버그 버전의 [CRT 라이브러리 기능](../../c-runtime-library/crt-library-features.md)만 해당합니다.

## <a name="see-also"></a>참고 항목

[디버그 루틴](../../c-runtime-library/debug-routines.md)<br/>
