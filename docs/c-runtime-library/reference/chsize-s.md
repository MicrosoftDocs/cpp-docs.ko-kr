---
description: '다음에 대 한 자세한 정보: _chsize_s'
title: _chsize_s
ms.date: 4/2/2020
api_name:
- _chsize_s
- _o__chsize_s
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
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: b3fa28923b558dc9b396cffc3418ff679349000d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253093"
---
# <a name="_chsize_s"></a>_chsize_s

파일 크기를 변경합니다. [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 보안 기능이 향상된 [_chsize](chsize.md) 버전입니다.

## <a name="syntax"></a>구문

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
열려 있는 파일을 참조하는 파일 설명자입니다.

*size*<br/>
파일의 새 길이(바이트)입니다.

## <a name="return-value"></a>반환 값

파일 크기가 성공적으로 변경 되 면 **_chsize_s** 는 값 0을 반환 합니다. 0이 아닌 반환 값은 오류를 나타냅니다. 지정 된 파일이 액세스에 대해 잠겨 있는 경우 반환 값은 **eacces** , 지정 된 파일이 읽기 전용 이거나 설명자가 잘못 된 경우 **ebadf** , 장치에 남아 있는 공간이 없는 경우 **ENOSPC** , 크기가 0 보다 작은 경우 **EINVAL** 입니다. **errno** 는 동일한 값으로 설정 됩니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**_Chsize_s** 함수는 *fd* 와 연결 된 파일을 *size* 로 지정 된 길이로 확장 하거나 자릅니다. 파일은 쓰기를 허용하는 모드로 열려 있어야 합니다. 파일이 확장되는 경우 Null 문자('\0')가 추가됩니다. 파일이 잘린 경우 짧아진 파일의 끝부터 파일의 원래 길이까지의 모든 데이터가 손실됩니다.

**_chsize_s** 는 파일 크기로 64 비트 정수를 사용 하므로 4gb 보다 큰 파일 크기를 처리할 수 있습니다. **_chsize** 는 32 비트 파일 크기로 제한 됩니다.

이 함수는 해당 매개 변수의 유효성을 검사합니다. *Fd* 가 올바른 파일 설명자가 아니거나 크기가 0 보다 작은 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
