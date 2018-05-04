---
title: Dll 지연 로드의 제약 조건 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 532d5ba64288fb70b19f10386186c0b520e67661
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="constraints-of-delay-loading-dlls"></a>DLL 지연 로드의 제약 조건
가져오기 지연 로드에 대한 제약 조건이 있습니다.  
  
-   데이터 가져오기를 지원할 수 없습니다. 해결 방법은 `LoadLibrary`(또는 지연 로드 도우미가 DLL을 로드한 사실을 안 후에는 `GetModuleHandle`) 및 `GetProcAddress`를 사용하여 데이터 가져오기를 명시적으로 처리하는 것입니다.  
  
-   Kernel32.dll 지연 로드는 지원되지 않습니다. 이 DLL은 지연 로드 수행을 위한 지연 로드 도우미 루틴에 필요합니다.  
  
-   [바인딩](../../build/reference/binding-imports.md) 항목의 전달 된 지원 되지 않습니다.  
  
-   지연 로드된 DLL의 진입점에서 프로세스별 초기화가 발생하는 경우 DLL 지연 로드로 인해 동일한 동작의 프로세스가 발생하지 않을 수 있습니다. 다른 사례에는 정적 TLS (스레드 로컬 저장소)를 사용 하 여 선언 [__declspec (thread)](../../cpp/thread.md)를 통해 DLL이 로드 되는 경우 처리 되지 않은 있는 `LoadLibrary`합니다. `TlsAlloc`, `TlsFree`, `TlsGetValue` 및 `TlsSetValue`를 사용하는 동적 TLS는 정적 또는 지연 로드된 DLL에 계속해서 사용할 수 있습니다.  
  
-   정적(전역) 함수 포인터는 첫 번째 함수 호출 후 가져온 함수로 다시 초기화해야 합니다. 이는 함수 포인터의 첫 번째 사용이 썽크를 가리키기 때문입니다.  
  
-   현재로써는 일반적인 가져오기 메커니즘을 사용하면서 DLL에서 특정 프로시저만 지연 로드할 수 있는 방법이 없습니다.  
  
-   사용자 지정 호출 규칙(예: x86 아키텍처에 조건 코드 사용)은 지원되지 않습니다. 또한 어떤 플랫폼에서도 부동 소수점 레지스터는 저장되지 않습니다. 사용자 지정 도우미 루틴 또는 후크 루틴이 부동 소수점 형식을 사용하는 경우 이러한 루틴은 부동 소수점 매개 변수와 함께 레지스터 호출 규칙을 사용하여 컴퓨터에서 부동 소수점 상태를 완벽하게 저장 및 복원해야 합니다. 도움말 함수의 NDP(수치 데이터 프로세서) 스택에 부동 소수점 매개 변수를 사용하는 CRT 함수를 호출하는 경우 CRT DLL 지연 로드에 주의하세요.  
  
## <a name="see-also"></a>참고 항목  
 [링커의 지연 로드 된 Dll 지원](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [LoadLibrary 함수](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [GetModuleHandle 함수](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [GetProcAddress 함수](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [TlsAlloc 함수](http://msdn.microsoft.com/library/windows/desktop/ms686801.aspx)   
 [TlsFree 함수](http://msdn.microsoft.com/library/windows/desktop/ms686804.aspx)   
 [TlsGetValue 함수](http://msdn.microsoft.com/library/windows/desktop/ms686812.aspx)   
 [TlsSetValue 함수](http://msdn.microsoft.com/library/windows/desktop/ms686818.aspx)