---
title: 전역 변수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.variables
dev_langs:
- C++
helpviewer_keywords:
- global variables
- variables, global
- global variables, Microsoft run-time library
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2da3dd07c7088bee4be750b764b4a467bfebeae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="global-variables"></a>전역 변수
Microsoft C 런타임 라이브러리는 다음 전역 변수 또는 매크로를 제공합니다. 이러한 전역 변수 또는 매크로 중 일부는 보다 안전한 함수 버전으로 인해 사용되지 않고 있으므로 전역 변수 대신 이러한 함수 버전을 사용하는 것이 좋습니다.  
  
|변수|설명|  
|--------------|-----------------|  
|[__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)|명령줄 인수가 포함되어 있습니다.|  
|[_daylight, _dstbias, _timezone 및 _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|더 이상 사용되지 않습니다. 대신 `_get_daylight`, `_get_dstbias`, `_get_timezone` 및 `_get_tzname`을 사용합니다.<br /><br /> 현지 시간을 조정하고 일부 날짜 및 시간 함수에 사용합니다.|  
|[errno, _doserrno, _sys_errlist 및 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|더 이상 사용되지 않습니다. 대신 `_get_errno`, `_set_errno`, `_get_doserrno`, `_set_doserrno`, `perror` 및 `strerror`를 사용합니다.<br /><br /> 오류 코드 및 관련 정보를 저장합니다.|  
|[_environ, _wenviron](../c-runtime-library/environ-wenviron.md)|더 이상 사용되지 않습니다. 대신 `getenv_s`, `_wgetenv_s`, `_dupenv_s`, `_wdupenv_s`, `_putenv_s` 및 `_wputenv_s`를 사용합니다.<br /><br /> 프로세스 환경 문자열에 대한 포인터의 배열에 대한 포인터입니다. 시작 시 초기화됩니다.|  
|[_fmode](../c-runtime-library/fmode.md)|더 이상 사용되지 않습니다. 대신 `_get_fmode` 또는 `_set_fmode`를 사용합니다.<br /><br /> 기본 파일 변환 모드를 설정합니다.|  
|[_iob](../c-runtime-library/iob.md)|콘솔, 파일 및 장치에 대한 I/O 제어 구조 배열입니다.|  
|[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|문자 분류 함수에서 사용하는 정보가 들어 있습니다.|  
|[_pgmptr, _wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|더 이상 사용되지 않습니다. 대신 `_get_pgmptr` 또는 `_get_wpgmptr`를 사용합니다.<br /><br /> 프로그램 시작 시 프로그램이 호출된 방식에 따라 파일 확장명 없이 프로그램 이름, 전체 프로그램 이름 또는 프로그램의 정규화된 경로 또는 상대 경로로 초기화됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [C 런타임 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md)   
 [전역 상수](../c-runtime-library/global-constants.md)   
 [__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)   
 [_get_daylight](../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname](../c-runtime-library/reference/get-tzname.md)   
 [perror](../c-runtime-library/reference/perror-wperror.md)   
 [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [_get_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [_get_errno](../c-runtime-library/reference/get-errno.md)   
 [_set_errno](../c-runtime-library/reference/set-errno.md)   
 [_dupenv_s, _wdupenv_s](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)   
 [getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)   
 [_get_fmode](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)