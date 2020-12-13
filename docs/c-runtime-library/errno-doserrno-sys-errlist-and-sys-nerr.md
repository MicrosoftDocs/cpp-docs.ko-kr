---
description: Errno, _doserrno, _sys_errlist 및 _sys_nerr에 대해 자세히 알아보세요.
title: errno, _doserrno, _sys_errlist 및 _sys_nerr
ms.date: 11/04/2016
api_name:
- _errno
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sys_errlist
- errno
- _sys_nerr
- _doserrno
helpviewer_keywords:
- error codes, printing
- sys_errlist global variable
- doserrno global variable
- errno global variable
- _doserrno global variable
- _sys_errlist global variable
- _sys_nerr global variable
- sys_nerr global variable
ms.assetid: adbec641-6d91-4e19-8398-9a34046bd369
ms.openlocfilehash: b15091ebfffec891b09f5024b14a8ca7fe0d02e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331172"
---
# <a name="errno-_doserrno-_sys_errlist-and-_sys_nerr"></a>errno, _doserrno, _sys_errlist 및 _sys_nerr

프로그램을 실행하는 동안 설정된 오류 코드를 보유한 전역 매크로와 표시용 오류 코드의 문자열에 해당하는 값입니다.

## <a name="syntax"></a>구문

```
#define errno   (*_errno())
#define _doserrno   (*__doserrno())
#define _sys_errlist (__sys_errlist())
#define _sys_nerr (*__sys_nerr())
```

## <a name="remarks"></a>설명

`errno`와 `_doserrno`는 모두 프로그램을 시작하는 동안 런타임에 0으로 설정됩니다. `errno`는 오류가 발생한 시스템 수준 호출에서 설정됩니다. `errno`에 설정된 마지막 호출에 대한 값이 있으므로 이후 호출에 의해 이 값이 변경될 수도 있습니다. 오류에 대해 `errno`를 설정하는 런타임 라이브러리 호출은 성공 시 `errno`를 지우지 않습니다. 설정할 수 있는 호출 바로 전에 `errno`를 호출하여 항상 `_set_errno(0)`를 지우고 호출 후 바로 확인하세요.

오류 발생 시 `errno`를 시스템 호출에서 반환된 오류 코드와 동일한 값으로 설정할 필요가 없습니다. I/O 작업의 경우 `_doserrno`는 `errno` 코드에 대등한 운영 체제 오류 코드를 저장합니다. 대부분의 비I/O 작업의 경우 `_doserrno` 값이 설정되지 않습니다.

각 `errno` 값은 [perror](../c-runtime-library/reference/perror-wperror.md) 함수 중 하나를 사용하여 인쇄하거나 [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) 또는 [strerror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) 함수 중 하나를 사용하여 문자열에 저장할 수 있는 `_sys_errlist`의 오류 메시지와 연결되어 있습니다. `perror` 및 `strerror` 함수에서 `_sys_errlist` 배열 및 `_sys_nerr`(`_sys_errlist`에서 요소 수)을 사용하여 오류 정보를 처리합니다. `_sys_errlist` 및 `_sys_nerr`에 대한 직접 액세스는 코드 보안상의 이유로 사용되지 않습니다. 다음과 같이 전역 매크로 대신 더욱 안전한 기능 버전을 사용하는 것이 좋습니다.

|전역 매크로|해당 기능|
|------------------|----------------------------|
|`_doserrno`|[_get_doserrno](../c-runtime-library/reference/get-doserrno.md), [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)|
|`errno`|[_get_errno](../c-runtime-library/reference/get-errno.md), [_set_errno](../c-runtime-library/reference/set-errno.md)|
|`_sys_errlist`, `_sys_nerr`|[strerror_s, _strerror_s, _wcserror_s, \_ _wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|

라이브러리 수학 루틴이 [_matherr](../c-runtime-library/reference/matherr.md)을 호출하여 `errno`를 설정합니다. 수학 오류를 다르게 처리하려면 `_matherr` 참조 설명에 따라 고유한 루틴을 작성하고 이름을 `_matherr`로 지정합니다.

`errno`다음 표의 모든 값은에서 미리 정의 된 상수 \<errno.h> 이며 UNIX와 호환 됩니다. `ERANGE`, `EILSEQ` 및 `EDOM`만 ISO C99 표준에 지정되어 있습니다.

|상수|시스템 오류 메시지|값|
|--------------|--------------------------|-----------|
|`EPERM`|작업이 허용되지 않음|1|
|`ENOENT`|해당하는 파일이나 디렉터리가 없습니다.|2|
|`ESRCH`|해당 프로세스 없음|3|
|`EINTR`|중단된 함수|4|
|`EIO`|I/O 오류|5|
|`ENXIO`|해당 디바이스 또는 주소 없음|6|
|`E2BIG`|인수 목록이 너무 김|7|
|`ENOEXEC`|실행 형식 오류|8|
|`EBADF`|잘못된 파일 번호|9|
|`ECHILD`|생성된 프로세스 없음|10|
|`EAGAIN`|추가 프로세스가 없거나 메모리가 부족하거나 최대 중첩 수주에 도달함|11|
|`ENOMEM`|메모리 부족|12|
|`EACCES`|사용 권한이 거부됨|13|
|`EFAULT`|잘못된 주소|14|
|`EBUSY`|디바이스 또는 리소스 사용 중|16|
|`EEXIST`|파일 존재 여부|17|
|`EXDEV`|디바이스 간 연결|18|
|`ENODEV`|해당 디바이스 없음|19|
|`ENOTDIR`|디렉터리가 아님|20|
|`EISDIR`|디렉터리임|21|
|`EINVAL`|잘못된 인수|22|
|`ENFILE`|시스템에 너무 많은 파일이 열려 있음|23|
|`EMFILE`|열려 있는 파일이 너무 많음|24|
|`ENOTTY`|부적절한 I/O 제어 작업|25|
|`EFBIG`|파일이 너무 큼|27|
|`ENOSPC`|디바이스에 남은 공간이 없음|28|
|`ESPIPE`|잘못된 검색|29|
|`EROFS`|읽기 전용 파일 시스템|30|
|`EMLINK`|링크가 너무 많음|31|
|`EPIPE`|파이프가 끊어짐|32|
|`EDOM`|산술 인수|33|
|`ERANGE`|결과가 너무 큼|34|
|`EDEADLK`|리소스 교착 상태가 발생함|36|
|`EDEADLOCK`|이전 Microsoft C 버전과의 호환성을 위해 EDEADLK와 동일|36|
|`ENAMETOOLONG`|파일 이름이 너무 김|38|
|`ENOLCK`|잠금을 사용할 수 없음|39|
|`ENOSYS`|함수가 지원되지 않음|40|
|`ENOTEMPTY`|디렉터리가 비어 있음|41|
|`EILSEQ`|바이트 시퀀스가 잘못됨|42|
|`STRUNCATE`|문자열이 잘림|80|

## <a name="requirements"></a>요구 사항

|전역 매크로|필수 헤더|선택적 헤더|
|------------------|---------------------|---------------------|
|`errno`|\<errno.h> or \<stdlib.h> , \<cerrno> or \<cstdlib> (c + +)||
|`_doserrno`, `_sys_errlist`, `_sys_nerr`|\<stdlib.h>, \<cstdlib> (C + +)|\<errno.h>, \<cerrno> (C + +)|

`_doserrno`, `_sys_errlist` 및 `_sys_nerr` 매크로는 Microsoft 확장입니다. 호환성에 대한 자세한 내용은 [Compatibility](../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[전역 변수](../c-runtime-library/global-variables.md)<br/>
[errno 상수](../c-runtime-library/errno-constants.md)<br/>
[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)<br/>
[strerror, _strerror, _wcserror, \_ _wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)<br/>
[strerror_s, _strerror_s, _wcserror_s, \_ _wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)<br/>
[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)<br/>
[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)<br/>
[_get_errno](../c-runtime-library/reference/get-errno.md)<br/>
[_set_errno](../c-runtime-library/reference/set-errno.md)
