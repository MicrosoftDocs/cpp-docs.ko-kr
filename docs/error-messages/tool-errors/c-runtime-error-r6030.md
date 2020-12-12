---
description: '자세한 정보: C 런타임 오류 R6030'
title: C 런타임 오류 R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: e3c945df043f8702d75db56c28b50b8b00f4df8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297215"
---
# <a name="c-runtime-error-r6030"></a>C 런타임 오류 R6030

CRT가 초기화 되지 않았습니다.

> [!NOTE]
> 앱을 실행 하는 동안이 오류 메시지가 표시 되 면 내부 문제가 있기 때문에 앱이 종료 되었습니다. 이 문제는 일반적으로 특정 보안 소프트웨어 프로그램에 의해 발생 하거나 프로그램의 버그로 드물게 발생 합니다.
>
> 이 오류를 해결하려면 다음 단계를 시도할 수 있습니다.
>
> - 보안 소프트웨어에는이 문제를 완화 하기 위한 특정 지침이 있을 수 있습니다. 자세한 내용은 보안 소프트웨어 공급 업체의 웹 사이트를 확인 하세요. 또는 업데이트 된 버전의 보안 소프트웨어를 확인 하거나 다른 보안 소프트웨어를 사용해 보세요.
> - **제어판** 의 **앱 및 기능** 또는 **프로그램 및 기능** 페이지를 사용 하 여 프로그램을 복구 하거나 다시 설치 합니다.
> - **제어판** 의 소프트웨어 업데이트에 대 한 **Windows 업데이트** 를 확인 합니다.
> - 앱의 업데이트 된 버전을 확인 합니다. 문제가 지속 되 면 앱 공급 업체에 문의 하세요.

**프로그래머를 위한 정보**

이 오류는 CRT (C 런타임)를 사용 하지만 CRT 시작 코드가 실행 되지 않은 경우에 발생 합니다. 링커 스위치 [/entry](../../build/reference/entry-entry-point-symbol.md) 를 사용 하 여 기본 시작 주소 (일반적으로 **mainCRTStartup**, **wmainCRTStartup** , Windows **_DllMainCRTStartup** EXE의 경우 **WinMainCRTStartup** 또는 **wWinMainCRTStartup** , DLL의 경우)를 재정의 하는 경우이 오류가 발생할 수 있습니다. 시작 시 위의 함수 중 하나가 호출 되지 않으면 C 런타임이 초기화 되지 않습니다. 이러한 시작 함수는 일반적으로 C 런타임 라이브러리에 연결 하 고 일반 **main**, **wmain**, **WinMain** 또는 **DllMain** 진입점을 사용 하는 경우 기본적으로 호출 됩니다.

다른 프로그램에서 코드 삽입 기술을 사용 하 여 특정 DLL 라이브러리 호출을 트랩할 때이 오류가 나타날 수도 있습니다. 일부 방해가 되는 보안 프로그램은이 방법을 사용 합니다. Visual Studio 2015 이전의 Visual C++ 버전에서는 정적으로 연결 된 CRT 라이브러리를 사용 하 여 문제를 해결할 수 있지만이는 보안 및 응용 프로그램 업데이트의 이유로 권장 되지 않습니다. 이 문제를 해결 하려면 최종 사용자 작업이 필요할 수 있습니다.
