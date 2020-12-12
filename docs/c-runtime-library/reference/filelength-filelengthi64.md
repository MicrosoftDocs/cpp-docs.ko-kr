---
description: '자세히 알아보기: _filelength, _filelengthi64'
title: _filelength, _filelengthi64
ms.date: 4/2/2020
api_name:
- _filelengthi64
- _filelength
- _o__filelength
- _o__filelengthi64
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
- _filelength
- _filelengthi64
- filelengthi64
helpviewer_keywords:
- filelengthi64 function
- lengths, file
- filelength function
- _filelength function
- files [C++], length
- _filelengthi64 function
ms.assetid: 3ab83d5a-543c-4079-b9d9-0abfc7da0275
ms.openlocfilehash: 21004112e731827240b66c343b69cc00133aa6ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329279"
---
# <a name="_filelength-_filelengthi64"></a>_filelength, _filelengthi64

파일의 길이를 가져옵니다.

## <a name="syntax"></a>구문

```C
long _filelength(
   int fd
);
__int64 _filelengthi64(
   int fd
);
```

### <a name="parameters"></a>매개 변수

*fd*<br/>
파일 설명자를 대상으로 지정합니다.

## <a name="return-value"></a>반환 값

**_Filelength** 와 **_filelengthi64** 는 모두 *fd* 와 연결 된 대상 파일의 파일 길이 (바이트)를 반환 합니다. *Fd* 가 잘못 된 파일 설명자 인 경우이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기를 호출 합니다. 계속 해 서 실행 하도록 허용한 경우 두 함수 모두-1L을 반환 하 여 오류를 나타내고 **errno** 를 **ebadf** 로 설정 합니다.

## <a name="remarks"></a>설명

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_filelength**|\<io.h>|
|**_filelengthi64**|\<io.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_chsize](chsize.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_fileno](fileno.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_stat, _wstat 함수](stat-functions.md)<br/>
