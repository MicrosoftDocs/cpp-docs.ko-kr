---
title: 디렉터리 제어 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c0ab24a55cddc13b743a28a022475b0c0b84e77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="directory-control"></a>디렉터리 제어

이러한 루틴은 디렉터리 구조를 액세스 및 수정하고 관련 정보를 가져옵니다.

## <a name="directory-control-routines"></a>디렉터리 제어 루틴

|루틴에서 반환된 값|사용|
|-------------|---------|
|[_chdir, _wchdir](../c-runtime-library/reference/chdir-wchdir.md)|현재 작업 디렉터리를 변경합니다.|
|[_chdrive](../c-runtime-library/reference/chdrive.md)|현재 드라이브를 변경합니다.|
|[_getcwd, _wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|기본 드라이브의 현재 작업 디렉터리를 가져옵니다.|
|[_getdcwd, _wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|지정된 드라이브의 현재 작업 디렉터리를 가져옵니다.|
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|디스크 드라이브에 대한 정보로 **_diskfree_t** 구조체를 채웁니다.|
|[_getdrive](../c-runtime-library/reference/getdrive.md)|현재(기본) 드라이브 가져오기|
|[_getdrives](../c-runtime-library/reference/getdrives.md)|현재 사용 가능한 디스크 드라이브를 나타내는 비트 마스크를 반환합니다.|
|[_mkdir, _wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|새 디렉터리를 만듭니다.|
|[_rmdir, _wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|디렉터리를 제거합니다.|
|[_searchenv, _wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md), [_searchenv_s, _wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|지정된 경로에서 지정된 파일을 검색합니다.|

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [파일 처리](../c-runtime-library/file-handling.md)<br/>
 [시스템 호출](../c-runtime-library/system-calls.md)<br/>
