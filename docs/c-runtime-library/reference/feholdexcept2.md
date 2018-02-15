---
title: "feholdexcept2 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- feholdexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feholdexcept
- fenv/feholdexcept
dev_langs:
- C++
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbfef5db5871740744e370d7e1ac86cf7abac8ac
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="feholdexcept"></a>feholdexcept
현재 부동 소수점 환경을 지정된 개체에 저장하고, 부동 소수점 상태 플래그를 지우고, 가능한 경우 부동 소수점 환경을 무중단 모드로 전환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `penv`  
 부동 소수점 환경의 복사본을 포함할 `fenv_t` 개체에 대한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 경우에 함수를 성공적으로 중단 없이 부동 소수점 예외 처리를 설정할 수는 0을 반환 합니다.  
  
## <a name="remarks"></a>설명  
 `feholdexcept` 함수는 현재 부동 소수점 환경의 상태를 `penv`가 가리키는 `fenv_t` 개체에 저장하고 해당 환경이 부동 소수점 예외에 대한 실행을 중단하지 않도록 설정하는 데 사용됩니다. 이를 무중단 모드라고 합니다.  이 모드는 [fesetenv](fesetenv1.md) 또는 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)를 통해 환경이 복원될 때까지 계속됩니다.  
  
 호출자로부터 하나 이상의 부동 소수점 예외를 숨겨야 하는 하위 루틴의 시작 부분에서 이 함수를 사용할 수 있습니다. 예외를 보고하기 위해 간단히 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)를 사용하여 원하지 않는 예외를 지우고 `feupdateenv`를 호출하여 무중단 모드를 종료할 수 있습니다.  
  
 이 함수를 사용하려면 호출 전에 `#pragma fenv_access(on)` 지시문을 사용하여 액세스를 방지할 수 있는 부동 소수점 최적화를 꺼야 합니다. 자세한 내용은 [fenv_access](../../preprocessor/fenv-access.md)을 참조하세요.  
  
## <a name="requirements"></a>요구 사항  
  
|함수|C 헤더|C++ 헤더|  
|--------------|--------------|------------------|  
|`feholdexcept`|\<fenv.h>|\<cfenv>|  
  
 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [사전순 함수 참조](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](fesetenv1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)