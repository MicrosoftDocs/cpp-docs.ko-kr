---
title: "_chdrive | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _chdrive
apilocation:
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chdrive
- _chdrive
dev_langs:
- C++
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1290f5a29ce2b6d80f98889fbb0fc5709cfa43e4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="chdrive"></a>_chdrive
현재 작업 드라이브를 변경합니다.  
  
> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 참조 [CRT 함수는 유니버설 Windows 플랫폼 앱에서 지원 되지 않습니다](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
int _chdrive(   
   int drive   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `drive`  
 현재 작업 드라이브를 지정하는 1부터 26까지의 정수입니다(1 = A, 2 = B 등).  
  
## <a name="return-value"></a>반환 값  
 현재 작업 드라이브가 변경된 경우 0이고, 변경되지 않으면 -1입니다.  
  
## <a name="remarks"></a>설명  
 `drive`가 1부터 26까지의 범위에 있지 않은 경우 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기가 호출됩니다. 계속 실행하도록 허용된 경우 **_chdrive** 함수는 -1을 반환하며 `errno`는 `EACCES`로 설정되고 `_doserrno`는 `ERROR_INVALID_DRIVE`로 설정됩니다.  
  
 **_chdrive** 함수는 그 자체가 스레드로부터 안전하지 않은 **SetCurrentDirectory** 함수에 종속되므로 스레드로부터 안전하지 않습니다. 다중 스레드 응용 프로그램에서 **_chdrive**를 안전하게 사용하려면 고유한 스레드 동기화를 제공해야 합니다. 자세한 내용을 보려면 [MSDN 라이브러리](http://go.microsoft.com/fwlink/p/?linkid=150542)로 이동한 후 **SetCurrentDirectory**를 검색하세요.  
  
 **_chdrive** 함수는 현재 작업 드라이브만 변경합니다. **_chdir** 함수는 현재 작업 디렉터리를 변경합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|**_chdrive**|\<direct.h>|  
  
 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="example"></a>예  
 [_getdrive](../../c-runtime-library/reference/getdrive.md)의 예제를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [디렉터리 제어](../../c-runtime-library/directory-control.md)   
 [_chdir, _wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getcwd, _wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [_mkdir, _wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir, _wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)