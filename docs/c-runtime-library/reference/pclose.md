---
description: '다음에 대 한 자세한 정보: _pclose'
title: _pclose
ms.date: 4/2/2020
api_name:
- _pclose
- _o__pclose
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
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: 529af8ccdd1c6cc27f9039adef5d75c8b977aa54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258709"
---
# <a name="_pclose"></a>_pclose

새 명령 프로세서가 실행될 때까지 기다렸다가 연결된 파이프에서 스트림을 닫습니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**_Popen** 에 대 한 이전 호출에서 반환 된 값입니다.

## <a name="return-value"></a>반환 값

종료 명령 프로세서의 종료 상태를 반환 하거나, 오류가 발생 하면-1을 반환 합니다. 반환 값의 형식은 하위 바이트와 상위 바이트를 교환 하는 것을 제외 하 고 **_cwait** 와 동일 합니다. Stream이 _pclose **NULL** 인  경우 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

이 오류 및 다른 오류 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="remarks"></a>설명

**_Pclose** 함수는 연결 된 **_popen** 호출에 의해 시작 된 명령 프로세서 (Cmd.exe)의 프로세스 ID를 조회 하 고, 새 명령 프로세서에서 [_cwait](cwait.md) 호출을 실행 하 고, 연결 된 파이프에서 스트림을 닫습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen, _wpopen](popen-wpopen.md)<br/>
