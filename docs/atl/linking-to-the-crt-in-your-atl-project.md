---
description: '자세히 알아보기: ATL 프로젝트에서 CRT에 연결'
title: ATL 프로젝트에서 CRT에 링크
ms.date: 11/04/2016
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
ms.openlocfilehash: e54301332d9a83546e41ab42169f06d305bbc6a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147630"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>ATL 프로젝트에서 CRT에 링크

CRT ( [C Run-Time 라이브러리](../c-runtime-library/crt-library-features.md) )는 ATL을 개발 하는 동안 프로그래밍을 훨씬 쉽게 만들 수 있는 많은 유용한 함수를 제공 합니다. 모든 ATL 프로젝트는 CRT 라이브러리에 연결 됩니다. [CRT에 연결 하는 데 사용 되는 방법의 이점 및 장단점](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md)에 대 한 링크 방법의 장점과 단점을 확인할 수 있습니다.

## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>프로그램 이미지에서 CRT에 연결 하는 경우의 효과

CRT에 정적으로 연결 하는 경우 CRT의 코드가 실행 가능한 이미지에 배치 되 고 이미지를 실행 하기 위해 시스템에 CRT DLL이 없어도 됩니다. CRT에 동적으로 연결 하는 경우 CRT DLL의 코드에 대 한 참조는 이미지에 있지만 코드 자체에는 포함 되지 않습니다. 지정 된 시스템에서 이미지를 실행 하려면 해당 시스템에 CRT DLL이 있어야 합니다. CRT에 동적으로 연결 하는 경우에도 일부 코드는 정적으로 연결 될 수 있습니다 (예: `DllMainCRTStartup` ).

이미지를 연결할 때 운영 체제가 이미지를 로드 한 후에 호출 하는 진입점을 명시적으로 지정 하거나 암시적으로 지정 합니다. DLL의 기본 진입점은 `DllMainCRTStartup` 입니다. EXE의 경우 `WinMainCRTStartup` 입니다. /ENTRY 링커 옵션을 사용 하 여 기본값을 재정의할 수 있습니다. CRT는 `DllMainCRTStartup` , `WinMainCRTStartup` 및 `wWinMainCRTStartup` (EXE의 유니코드 진입점)에 대 한 구현을 제공 합니다. 이러한 CRT 제공 진입점은 전역 개체에 대 한 생성자를 호출 하 고 일부 CRT 함수에서 사용 하는 다른 데이터 구조를 초기화 합니다. 이 시작 코드는 정적으로 연결 된 경우 25,000에 대 한 정보를 이미지에 추가 합니다. 동적으로 연결 된 경우 대부분의 코드는 DLL에 있으므로 이미지 크기는 작게 유지 됩니다.

자세한 내용은 링커 항목 [/entry (진입점 기호)](../build/reference/entry-entry-point-symbol.md)를 참조 하세요.

## <a name="optimization-options"></a>최적화 옵션

링커 옵션/OPT: NOWIN98를 사용 하면 Windows 98 시스템에서 로드 시간이 증가 하는 대신 10K로 기본 ATL 컨트롤을 더 줄일 수 있습니다. 연결 옵션에 대 한 자세한 내용은 [/opt (최적화)](../build/reference/opt-optimizations.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[ATL 및 C Run-Time 코드를 사용한 프로그래밍](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[DLL 및 Visual C++ 런타임 라이브러리 동작](../build/run-time-library-behavior.md)
