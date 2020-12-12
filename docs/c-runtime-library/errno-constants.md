---
description: Errno 상수에 대해 자세히 알아보세요.
title: errno 상수
ms.date: 09/17/2018
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
ms.openlocfilehash: 4eb92b66970f1ef9455a0d7dd741ad02a60c26d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329340"
---
# <a name="errno-constants"></a>errno 상수

## <a name="syntax"></a>구문

```
#include <errno.h>
```

## <a name="remarks"></a>설명

**errno** 값은 여러 오류 조건에서 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)에 할당된 상수입니다.

ERRNO.H는 **errno** 값의 정의를 포함합니다. 그러나 ERRNO.H에서 지정된 정의 중 일부는 32비트 Windows 운영 체제에서 사용되지 않습니다. ERRNO.H에 있는 값 중 일부는 UNIX 운영 체제군과의 호환성을 유지하기 위해 제공됩니다.

32비트 Windows 운영 체제의 **errno** 값은 XENIX 시스템 내 **errno** 에 대한 값의 하위 집합입니다. 따라서 **errno** 값은 Windows 운영 체제의 시스템 호출에 의해 반환되는 실제 오류 코드와 동일할 필요는 없습니다. 실제 운영 체제 오류 코드에 액세스하려면 이 값을 포함하는 [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 변수를 사용하세요.

다음과 같은 **errno** 값이 지원됩니다.

|상수|설명|
|-|-|
|**ECHILD**|생성된 프로세스가 없습니다.|
|**EAGAIN**|더 이상 프로세스가 없습니다. 더 이상 프로세스 슬롯이 없거나, 메모리가 부족하거나, 최대 중첩 수준에 도달했기 때문에 새 프로세스를 만들려는 시도가 실패했습니다.|
|**E2BIG**|인수 목록이 너무 깁니다.|
|**EACCES**|사용 권한이 거부되었습니다. 파일의 권한 설정이 지정된 액세스를 허용하지 않습니다. 이 오류는 파일의 특성과 호환되지 않는 방식으로 파일(또는 일부 경우 디렉터리)에 액세스하려는 시도가 있었음을 의미합니다.<br/><br/>예를 들어 열려 있지 않은 파일로부터 읽거나, 기존 읽기 전용 파일을 쓰기 위해 열거나, 파일 대신 디렉터리를 열려는 시도가 있는 경우 오류가 발생할 수 있습니다. MS-DOS 운영 체제 버전 3.0 이상에서 **EACCES** 는 잠금 또는 공유 위반을 나타낼 수도 있습니다.<br/><br/>파일 또는 디렉터리의 이름을 바꾸거나 기존 디렉터리를 제거하려는 동안 오류가 발생할 수도 있습니다.|
|**EBADF**|잘못된 파일 번호입니다. 가능한 원인은 두 가지입니다. 1) 지정한 파일 설명자가 잘못된 값이거나 열려 있는 파일을 참조하지 않습니다. 2) 읽기 전용으로 열린 파일 또는 디바이스에 쓰려는 시도가 있었습니다.|
|**EDEADLOCK**|리소스 교착 상태가 발생합니다. 수학 함수에 대한 인수는 함수의 도메인에 포함되지 않습니다.|
|**EDOM**|수학 인수입니다.|
|**EEXIST**|파일이 존재합니다. 이미 존재하는 파일을 만들려는 시도가 있었습니다. 예를 들어 **_O_CREAT** 및 **_O_EXCL** 플래그가 **_open** 호출에서 지정되지만 명명된 파일이 이미 있습니다.|
|**EILSEQ**|잘못된 바이트의 시퀀스(예: MBCS 문자열에 있음)입니다.|
|**EINVAL**|인수가 잘못되었습니다. 함수의 인수 중 하나에 대해 잘못된 값이 지정되었습니다. 예를 들어 **fseek** 에 대한 호출을 통해 파일 포인터의 위치를 지정할 때 원본에 대해 지정된 값이 파일의 시작 부분 앞에 있습니다.|
|**EMFILE**|열려 있는 파일이 너무 많습니다. 더 이상 사용 가능한 파일 설명자가 없으므로 더 이상 파일을 열 수 없습니다.|
|**ENOENT (**|이러한 파일 또는 디렉터리가 없습니다. 지정된 파일 또는 디렉터리가 존재하지 않거나 찾을 수 없습니다. 지정한 파일이 존재하지 않거나 경로의 구성 요소에서 기존 디렉터리를 지정하지 않을 때마다 이 메시지가 나타날 수 있습니다.|
|**ENOEXEC**|실행 형식 오류입니다. 실행 파일이 아니거나 잘못된 형식의 실행 파일을 실행하려는 시도가 있었습니다.|
|**ENOMEM**|코어가 부족합니다. 시도된 연산자에 대한 메모리가 부족합니다. 예를 들어 자식 프로세스를 실행하기 위한 메모리가 부족하거나 **_getcwd** 호출의 할당 요청이 만족되지 않을 때 이 메시지가 나타날 수 있습니다.|
|**ENOSPC**|디바이스에 남은 공간이 없습니다. 디바이스에 더 이상 쓸 공간이 없습니다(예: 디스크가 꽉 찬 경우).|
|**ERANGE**|결과가 너무 큽니다. 수학 함수의 인수가 너무 커서 결과에서 중요 전체 또는 부분 손실이 발생했습니다. 이 오류는 인수가 예상보다 클 때 다른 함수에서도 발생할 수 있습니다(예: **_getcwd** 에 대한 *buffer* 인수가 예상보다 긴 경우).|
|**EXDEV**|디바이스 간 연결입니다. 파일을 다른 디바이스로 이동하려는 시도가 있었습니다(**rename** 함수 사용).|
|**STRUNCATE**|문자열 복사 또는 연결에 의해 문자열이 잘렸습니다. [_TRUNCATE](../c-runtime-library/truncate.md)를 참조하세요.

다음 값은 POSIX와의 호환성을 위해 지원 됩니다. 이러한 값은 비 POSIX 시스템에 필요한 값입니다.

```C
#define E2BIG /* argument list too long */
#define EACCES /* permission denied */
#define EADDRINUSE /* address in use */
#define EADDRNOTAVAIL /* address not available */
#define EAFNOSUPPORT /* address family not supported */
#define EAGAIN /* resource unavailable try again */
#define EALREADY /* connection already in progress */
#define EBADF /* bad file descriptor */
#define EBADMSG /* bad message */
#define EBUSY /* device or resource busy */
#define ECANCELED /* operation canceled */
#define ECHILD /* no child process */
#define ECONNABORTED /* connection aborted */
#define ECONNREFUSED /* connection refused */
#define ECONNRESET /* connection reset */
#define EDEADLK /* resource deadlock would occur */
#define EDESTADDRREQ /* destination address required */
#define EDOM /* argument out of domain */
#define EEXIST /* file exists */
#define EFAULT /* bad address */
#define EFBIG /* file too large */
#define EHOSTUNREACH /* host unreachable */
#define EIDRM /* identifier removed */
#define EILSEQ /* illegal byte sequence */
#define EINPROGRESS /* operation in progress */
#define EINTR /* interrupted */
#define EINVAL /* invalid argument */
#define EIO /* io error */
#define EISCONN /* already connected */
#define EISDIR /* is a directory */
#define ELOOP /* too many synbolic link levels */
#define EMFILE /* too many files open */
#define EMLINK /* too many links */
#define EMSGSIZE /* message size */
#define ENAMETOOLONG /* filename too long */
#define ENETDOWN /* network down */
#define ENETRESET /* network reset */
#define ENETUNREACH /* network unreachable */
#define ENFILE /* too many files open in system */
#define ENOBUFS /* no buffer space */
#define ENODATA /* no message available */
#define ENODEV /* no such device */
#define ENOENT /* no such file or directory */
#define ENOEXEC /* executable format error */
#define ENOLCK /* no lock available */
#define ENOLINK /* no link */
#define ENOMEM /* not enough memory */
#define ENOMSG /* no message */
#define ENOPROTOOPT /* no protocol option */
#define ENOSPC /* no space on device */
#define ENOSR /* no stream resources */
#define ENOSTR /* not a stream */
#define ENOSYS /* function not supported */
#define ENOTCONN /* not connected */
#define ENOTDIR /* not a directory */
#define ENOTEMPTY /* directory not empty */
#define ENOTRECOVERABLE /* state not recoverable */
#define ENOTSOCK /* not a socket */
#define ENOTSUP /* not supported */
#define ENOTTY /* inappropriate io control operation */
#define ENXIO /* no such device or address */
#define EOPNOTSUPP /* operation not supported */
#define EOTHER /* other */
#define EOVERFLOW /* value too large */
#define EOWNERDEAD /* owner dead */
#define EPERM /* operation not permitted */
#define EPIPE /* broken pipe */
#define EPROTO /* protocol error */
#define EPROTONOSUPPORT /* protocol not supported */
#define EPROTOTYPE /* wrong protocol type */
#define ERANGE /* result out of range */
#define EROFS /* read only file system */
#define ESPIPE /* invalid seek */
#define ESRCH /* no such process */
#define ETIME /* stream timeout */
#define ETIMEDOUT /* timed out */
#define ETXTBSY /* text file busy */
#define EWOULDBLOCK /* operation would block */
#define EXDEV /* cross device link */
```

## <a name="see-also"></a>참고 항목

[전역 상수](../c-runtime-library/global-constants.md)
