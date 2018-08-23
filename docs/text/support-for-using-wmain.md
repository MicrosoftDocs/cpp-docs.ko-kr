---
title: Wmain 사용 지원 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- wWinMain
dev_langs:
- C++
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b82c233d1f03ae4679a355b6782bb9e7dd9dad15
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604065"
---
# <a name="support-for-using-wmain"></a>wmain 사용 지원
Visual c + +에서는 정의 **wmain** 함수와 유니코드 응용 프로그램에 와이드 문자 인수를 전달 합니다. 정식 매개 변수를 선언 **wmain**, 비슷한 형식으로 사용 하 여 `main`입니다. 와이드 문자 인수 또는 와이드 문자 환경 포인터를 프로그램에 전달할 수 있습니다. **wmain**에 대한 `argv` 및 `envp` 매개 변수는 `wchar_t*` 형식입니다. 예를 들어:  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  유니코드 MFC 응용 프로그램 사용 `wWinMain` 진입점으로 합니다. 이 경우 `CWinApp::m_lpCmdLine` 는 유니코드 문자열입니다. 설정 해야 `wWinMainCRTStartup` 사용 하 여 합니다 [/ENTRY](../build/reference/entry-entry-point-symbol.md) 링커 옵션입니다.  
  
 프로그램을 사용 하는 경우는 `main` 함수는 멀티 바이트 문자 환경이 프로그램을 시작할 때 런타임 라이브러리에 의해 만들어집니다. 이 환경의 와이드 문자 복사본은 필요한 경우(예: `_wgetenv` 또는 `_wputenv` 함수를 호출하는 경우)에만 만들어집니다. 첫 번째 호출에서 `_wputenv`, 또는 첫 번째 호출은 `_wgetenv` MBCS 환경이 이미 있는 경우 해당 와이드 문자 문자열 환경이 만들어집니다. 환경에서 가리키는 다음 합니다 `_wenviron` 전역 변수는 와이드 문자 버전의를 `_environ` 전역 변수입니다. 이 시점에서 두 개의 복사본 (MBCS 및 유니코드) 환경 동시에 존재 하 고 프로그램의 수명 동안 런타임 시스템에서 유지 됩니다.  
  
 마찬가지로 프로그램이 **wmain** 함수를 사용하면 프로그램이 시작될 때 와이드 문자 환경이 만들어지고 `_wenviron` 전역 변수가 해당 환경을 가리킵니다. 첫 번째 호출에서 MBCS (ASCII) 환경을 만드는 `_putenv` 하거나 `getenv` 이 가리키는 및는 `_environ` 전역 변수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [유니코드에 대 한 지원](../text/support-for-unicode.md)   
 [유니코드 프로그래밍 요약](../text/unicode-programming-summary.md)   
 [WinMain 함수](http://msdn.microsoft.com/library/windows/desktop/ms633559)