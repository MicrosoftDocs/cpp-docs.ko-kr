---
title: setjmp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- setjmp
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
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef5c4b0e026090718fc02dd109a1fccb91152010
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="setjmp"></a>setjmp
프로그램의 현재 상태를 저장합니다.  
  
## <a name="syntax"></a>구문  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `env`  
 환경이 저장되는 변수입니다.  
  
## <a name="return-value"></a>반환 값  
 스택 환경에 저장한 후 0을 반환합니다. `setjmp`는 `longjmp` 호출의 결과로 반환되는 경우 `longjmp`의 `value` 인수를 반환합니다. `longjmp`의 `value` 인수가 0이면 `setjmp`는 1을 반환합니다. 반환되는 오류가 없습니다.  
  
## <a name="remarks"></a>설명  
 `setjmp` 함수는 `longjmp`를 사용하여 나중에 복원할 수 있는 스택 환경을 저장합니다. `setjmp`와 `longjmp`를 함께 사용하면 비로컬 `goto`를 실행할 수 있습니다. setjmp와 longjmp는 일반 호출이나 반환 규칙을 사용하지 않고 전에 호출된 루틴에서 오류 처리 또는 복구 코드에 실행 제어를 전달하는 데 주로 사용됩니다.  
  
 `setjmp`에 대한 호출은 현재 스택 환경을 `env`에 저장합니다. `longjmp`에 대한 후속 호출은 저장된 환경을 복원하고 컨트롤을 해당 `setjmp` 호출 바로 다음에 오는 포인터로 반환합니다. 컨트롤을 받는 루틴에 액세스할 수 있는 모든 변수(레지스터 변수 제외)는 `longjmp`가 호출될 때 가지고 있던 값을 포함합니다.  
  
 `setjmp`를 사용하여 네이티브 코드에서 관리 코드로 이동할 수는 없습니다.  
  
 **참고** `setjmp` 및 `longjmp`는 C++ 개체 의미 체계를 지원하지 않습니다. C++ 프로그램에서는 C++ 예외 처리 메커니즘을 사용해야 합니다.  
  
 자세한 내용은 [setjmp 및 longjmp 사용](../../cpp/using-setjmp-longjmp.md)을 참조하세요.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`setjmp`|\<setjmp.h>|  
  
 호환성에 대한 자세한 내용은 소개 단원의 [호환성](../../c-runtime-library/compatibility.md) 부분을 참조하십시오.  
  
## <a name="example"></a>예  
 [_fpreset](../../c-runtime-library/reference/fpreset.md)에 대한 예제를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [_setjmp3](../../c-runtime-library/setjmp3.md)