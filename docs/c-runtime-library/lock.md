---
title: _lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _lock
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- lock
- _lock
dev_langs:
- C++
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9a518402d027ae128fcf403752fafb448461628
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="lock"></a>_lock
다중 스레드 잠금을 가져옵니다.  
  
> [!IMPORTANT]
>  이 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```  
void __cdecl _lock  
   int locknum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [in] `locknum`  
 가져올 잠금의 식별자입니다.  
  
## <a name="remarks"></a>설명  
 잠금을 이미 가져온 경우 이 메서드는 잠금을 가져오고 내부 CRT(C 런타임) 오류를 발생시킵니다. 이 메서드가 잠금을 가져올 수 없는 경우 오류가 발생한 상태로 종료되고 오류 코드가 `_RT_LOCK`으로 설정됩니다.  
  
## <a name="requirements"></a>요구 사항  
 **소스:** mlock.c  
  
## <a name="see-also"></a>참고 항목  
 [사전순 함수 참조](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_unlock](../c-runtime-library/unlock.md)