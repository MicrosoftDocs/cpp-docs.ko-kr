---
description: '자세한 정보: wmain 사용에 대 한 지원'
title: wmain 사용 지원
ms.date: 11/04/2016
f1_keywords:
- wWinMain
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
ms.openlocfilehash: b6a954ab62c9bc675bd2b71275d615b3ee4c1376
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335742"
---
# <a name="support-for-using-wmain"></a>wmain 사용 지원

Visual C++는 **wmain** 함수를 정의 하 고 유니코드 응용 프로그램에 와이드 문자 인수를 전달 하는 것을 지원 합니다. 와 유사한 형식을 사용 하 여 **wmain** 에 대 한 정식 매개 변수를 선언 `main` 합니다. 와이드 문자 인수 또는 와이드 문자 환경 포인터를 프로그램에 전달할 수 있습니다. **wmain** 에 대한 `argv` 및 `envp` 매개 변수는 `wchar_t*` 형식입니다. 예를 들어:

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> MFC 유니코드 응용 프로그램은 `wWinMain` 진입점으로를 사용 합니다. 이 경우 `CWinApp::m_lpCmdLine` 는 유니코드 문자열입니다. /Entry 링커 옵션을 사용 하 여를 설정 해야 `wWinMainCRTStartup` 합니다. [](../build/reference/entry-entry-point-symbol.md)

프로그램이 **main** 함수를 사용하면 프로그램을 시작할 때 런타임 라이브러리에 의해 멀티바이트 문자 환경이 만들어집니다. 이 환경의 와이드 문자 복사본은 필요한 경우(예: `_wgetenv` 또는 `_wputenv` 함수를 호출하는 경우)에만 만들어집니다. 에 대 한 첫 번째 호출 `_wputenv` 또는 `_wgetenv` MBCS 환경이 이미 있는 경우 첫 번째 호출에서 해당 하는 와이드 문자 문자열 환경이 만들어집니다. 그러면 전역 변수는 `_wenviron` 전역 변수의 와이드 문자 버전인 전역 변수에 의해 가리킵니다 `_environ` . 이 시점에서 환경의 두 복사본 (MBCS 및 유니코드)이 동시에 존재 하며 프로그램의 수명 내내 런타임 시스템에서 유지 관리 됩니다.

마찬가지로 프로그램이 **wmain** 함수를 사용하면 프로그램이 시작될 때 와이드 문자 환경이 만들어지고 `_wenviron` 전역 변수가 해당 환경을 가리킵니다. MBCS (ASCII) 환경은 또는를 처음 호출할 때 만들어지며 `_putenv` `getenv` , 전역 변수가이를 가리킵니다 `_environ` .

## <a name="see-also"></a>참고 항목

[유니코드 지원](../text/support-for-unicode.md)<br/>
[유니코드 프로그래밍 요약](../text/unicode-programming-summary.md)<br/>
[WinMain 함수](/windows/win32/api/winbase/nf-winbase-winmain)
