---
title: 파일 읽기/쓰기 액세스 상수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.constants.file
dev_langs:
- C++
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f57ac6ffc3c13c640d7bdf6a2ec64912148bfbc3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="file-readwrite-access-constants"></a>파일 읽기/쓰기 액세스 상수
## <a name="syntax"></a>구문  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>설명  
 이러한 상수는 파일에 대해 요청된 액세스 형식("a", "r" 또는 "w")을 지정합니다. [변환 모드](../c-runtime-library/file-translation-constants.md)("b" 또는 "t") 및 [디스크에 커밋 모드](../c-runtime-library/commit-to-disk-constants.md)("c" 또는 "n") 둘 다 액세스 형식으로 지정할 수 있습니다.  
  
 액세스 형식에 대한 설명은 다음과 같습니다.  
  
 **"a"**  
 파일 끝에 쓰기(추가) 위해 엽니다. 파일이 존재하지 않는 경우 먼저 파일을 만듭니다. 모든 쓰기 작업이 파일의 끝에서 발생합니다. `fseek` 또는 **rewind**를 사용하여 파일 포인터의 위치를 변경할 수 있지만, 파일 포인터는 쓰기 작업을 수행하기 전에 항상 파일 끝으로 다시 이동합니다.  
  
 **"a+"**  
 위와 동일할 뿐만 아니라 읽기를 허용합니다.  
  
 **"r"**  
 읽기 위해 엽니다. 파일이 없거나 찾을 수 없는 경우 파일 열기 호출이 실패합니다.  
  
 **"r+"**  
 읽고 쓰기 위해 엽니다. 파일이 없거나 찾을 수 없는 경우 파일 열기 호출이 실패합니다.  
  
 **"w"**  
 쓰기 위해 빈 파일을 엽니다. 지정한 파일이 있으면 이 파일의 내용은 삭제됩니다.  
  
 **"w+"**  
 읽고 쓰기 위해 빈 파일을 엽니다. 지정한 파일이 있으면 이 파일의 내용은 삭제됩니다.  
  
 "r+", "w+" 또는 "a+"액세스 형식을 지정한 경우 읽기와 쓰기가 모두 허용됩니다. 즉, 파일이 “업데이트”용으로 열립니다. 그러나 읽기와 쓰기를 전환할 때는 사이에 `fflush`, `fsetpos`, `fseek`또는 **rewind** 작업이 있어야 합니다. `fsetpos` 또는 `fseek` 작업에 대한 현재 위치를 지정할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)   
 [전역 상수](../c-runtime-library/global-constants.md)