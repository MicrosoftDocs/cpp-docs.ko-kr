---
title: check_stack | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
dev_langs:
- C++
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b16a3d87741b8dda3b130c09d74e86a2350cd7be
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541471"
---
# <a name="checkstack"></a>check_stack
경우 스택 프로브를 해제 하려면 컴파일러에 지시 `off` (또는 `-`) 지정 된 경우 스택 프로브 하 `on` (또는 `+`) 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
#pragma check_stack([ {on | off}] )  
#pragma check_stack{+ | -}  
```  
  
## <a name="remarks"></a>설명 

인수를 지정하지 않으면 스택 프로브가 기본값에 따라 처리됩니다. 이 pragma는 pragma가 표시된 후 정의된 첫 번째 함수에서 적용됩니다. 스택 프로브는 인라인으로 생성된 함수의 일부나 매크로의 일부가 아닙니다.  
  
에 대 한 인수로 지정 하지 않으면 합니다 **check_stack** pragma를 명령줄에 지정 된 동작으로 돌아갑니다 스택 검사를 수행 합니다. 자세한 내용은 [컴파일러 참조](../build/reference/compiler-options.md)합니다. 상호 작용 합니다 `#pragma check_stack` 하며 [/Gs](../build/reference/gs-control-stack-checking-calls.md) 옵션 표에 요약 되어 있습니다.  
  
### <a name="using-the-checkstack-pragma"></a>check_stack Pragma 사용  
  
|구문|/Gs 옵션을 사용한<br /><br /> 컴파일 여부|작업|  
|------------|------------------------------------|------------|  
|`#pragma check_stack( )` 또는<br /><br /> `#pragma check_stack`|예|뒤에 오는 함수에 대한 스택 검사 해제|  
|`#pragma check_stack( )` 또는<br /><br /> `#pragma check_stack`|아니요|뒤에 오는 함수에 대한 스택 검사 설정|  
|`#pragma check_stack(on)`<br /><br /> 또는 `#pragma check_stack +`|예 또는 아니요|뒤에 오는 함수에 대한 스택 검사 설정|  
|`#pragma check_stack(off)`<br /><br /> 또는 `#pragma check_stack -`|예 또는 아니요|뒤에 오는 함수에 대한 스택 검사 해제|  
  
## <a name="see-also"></a>참고 항목  
 
[Pragma 지시문 및 __Pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)