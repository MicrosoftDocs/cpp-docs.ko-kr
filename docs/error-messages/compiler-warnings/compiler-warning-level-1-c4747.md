---
title: 컴파일러 경고 (수준 1) C4747 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 203943f3741d07e278652a7032a6dcdcb305a384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4747"></a>컴파일러 경고(수준 1) C4747
관리 되는 '진입점' 호출: DLL 진입점 및 DLL 진입점에서 접근 하는 호출을 포함 하 여 로더 잠금 상태에서 관리 되는 코드는 실행 되지 않을 수 있습니다  
  
 컴파일러 (예상) DLL 진입점을 MSIL로 컴파일된 발견 했습니다.  해당 진입점 MSIL로 컴파일된 DLL을 로드으로 잠재적인 문제 커지므로 한 DLL 진입점 함수를 MSIL로 컴파일 해서는 안 되는 합니다.  
  
 자세한 내용은 참조 [혼합형 어셈블리 초기화](../../dotnet/initialization-of-mixed-assemblies.md) 및 [링커 도구 오류 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1.  사용 하 여 모듈을 컴파일하지 않거나 **/clr**합니다.  
  
2.  표시 된 진입점 함수가 `#pragma unmanaged`합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C4747 경고가 발생 합니다.  
  
```  
// C4747.cpp  
// compile with: /clr /c /W1  
// C4747 expected  
#include <windows.h>  
  
// Uncomment the following line to resolve.  
// #pragma unmanaged  
  
BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {  
   return TRUE;  
};  
```