---
title: _putenv_s, _wputenv_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wputenv_s
- _putenv_s
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
apitype: DLLExport
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
dev_langs:
- C++
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 035afd354bd41ce3c9dc0c6bed44a25b03a09e6f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="putenvs-wputenvs"></a>_putenv_s, _wputenv_s
환경 변수를 생성, 수정 또는 제거합니다. 이러한 버전의 [_putenv, _wputenv](../../c-runtime-library/reference/putenv-wputenv.md)에는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 향상된 보안 기능이 포함되어 있습니다.  
  
> [!IMPORTANT]
>  이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 참조 [CRT 함수는 유니버설 Windows 플랫폼 앱에서 지원 되지 않습니다](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
errno_t _putenv_s(  
   const char *name,  
   const char *value   
);  
errno_t _wputenv_s(  
   const wchar_t *name,  
   const wchar_t *value  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `name`  
 환경 변수 이름입니다.  
  
 `value`  
 환경 변수를 설정할 값입니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 0을 반환하고, 그렇지 않으면 오류 코드를 반환합니다.  
  
### <a name="error-conditions"></a>오류 조건  
  
|`name`|`value`|반환 값|  
|------------|-------------|------------------|  
|`NULL`|any|`EINVAL`|  
|any|`NULL`|`EINVAL`|  
  
 오류 조건 중 하나가 발생할 경우 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속해서 실행하도록 허용된 경우, 이러한 함수는 `EINVAL`를 반환하고 `errno`를 `EINVAL`로 설정합니다.  
  
## <a name="remarks"></a>설명  
 `_putenv_s` 함수는 새 환경 변수를 추가하거나 기존 환경 변수의 값을 수정합니다. 환경 변수는 프로세스가 실행되는 환경을 정의합니다(예: 프로그램에 연결할 라이브러리의 기본 검색 경로). `_wputenv_s`은 `_putenv_s`의 와이드 문자 버전이며, `envstring`에 대한 `_wputenv_s` 인수는 와이드 문자열입니다.  
  
### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑  
  
|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tputenv_s`|`_putenv_s`|`_putenv_s`|`_wputenv_s`|  
  
 `name`은 추가 또는 수정할 환경 변수의 이름이고 `value`는 변수의 값입니다. `name`이 이미 환경의 일부이면 해당 값이 `value`로 대체되고, 그렇지 않으면 새로운 `name` 변수 및 해당 `value`가 환경에 추가됩니다. `value`에 대한 빈 문자열("")을 지정하여 환경에서 변수를 제거할 수 있습니다.  
  
 `_putenv_s` 및 `_wputenv_s`는 현재 프로세스에 로컬인 환경에만 영향을 줍니다. 명령 수준 환경을 수정하는 데 사용할 수 없습니다. 이러한 함수는 운영 체제가 프로세스에 대해 만드는 환경 "세그먼트"가 아니라 런타임 라이브러리에 액세스할 수 있는 데이터 구조에서만 작동합니다. 현재 프로세스가 종료되면 환경이 호출 프로세스의 수준(대부분의 경우 운영 체제 수준)으로 되돌아갑니다. 그러나 수정된 환경을 `_spawn`, `_exec` 또는 `system`에 의해 생성되는 모든 새로운 프로세스에 전달할 수 있으며, 이러한 새로운 프로세스는 `_putenv_s` 및 `_wputenv_s`에 의해 추가되는 모든 새로운 항목을 가져옵니다.  
  
 환경 항목을 직접 변경하지 말고 대신 `_putenv_s` 또는 `_wputenv_s`를 사용하여 변경하세요. 특히 `_environ[]` 전역 배열의 요소를 직접 해제하면 잘못된 메모리가 처리될 수 있습니다.  
  
 `getenv` 및 `_putenv_s`는 전역 변수 `_environ`을 사용하여 환경 테이블에 액세스하고, `_wgetenv` 및 `_wputenv_s`는 `_wenviron`을 사용합니다. `_putenv_s` 및 `_wputenv_s`는 `_environ` 및 `_wenviron`의 값을 변경하여 `envp`에 대한 `main` 인수와 `_wenvp`에 대한 `wmain` 인수를 무효화할 수 있습니다. 따라서 `_environ` 또는 `_wenviron`을 사용하여 환경 정보에 액세스하는 것이 더 안전합니다. `_putenv_s` 및 `_wputenv_s`와 전역 변수의 관계에 대한 자세한 내용은 [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md)을 참조하세요.  
  
> [!NOTE]
>  함수의 `_putenv_s` 및 `_getenv_s` 패밀리는 스레드로부터 안전하지 않습니다. `_getenv_s`는 `_putenv_s`가 문자열을 수정하는 동안 문자열 포인터를 반환할 수 있으므로 임의의 오류를 발생시킵니다. 이러한 함수에 대한 호출은 동기화해야 합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`_putenv_s`|\<stdlib.h>|  
|`_wputenv_s`|\<stdlib.h> 또는 \<wchar.h>|  
  
 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="example"></a>예  
 `_putenv_s`를 사용하는 방법을 보여 주는 샘플은 [getenv_s, _wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)   
 [getenv, _wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv, _wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)