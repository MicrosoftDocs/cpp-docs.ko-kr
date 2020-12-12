---
description: '자세히 알아보기: 혼합형 어셈블리에 대 한 라이브러리 지원'
title: 혼합형 어셈블리에 대한 라이브러리 지원
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: d20069c2caa1cf46ebdb54907de586630d4ee71c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113716"
---
# <a name="library-support-for-mixed-assemblies"></a>혼합형 어셈블리에 대한 라이브러리 지원

Visual C++는 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)을 사용 하 여 컴파일된 응용 프로그램에 대 한 c + + 표준 라이브러리, CRT (C 런타임 라이브러리), ATL 및 MFC의 사용을 지원 합니다. 이렇게 하면 이러한 라이브러리를 사용 하는 기존 응용 프로그램 에서도 .NET Framework 기능을 사용할 수 있습니다.

> [!IMPORTANT]
> **/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

이 지원에는 다음 DLL 및 가져오기 라이브러리가 포함 됩니다.

- **/Clr** 을 사용 하 여 컴파일하는 경우에는 msvcmrt.lib [d] .lib를 사용 합니다. 혼합 어셈블리는이 가져오기 라이브러리에 연결 됩니다.

이 지원은 몇 가지 관련 된 이점을 제공 합니다.

- CRT 및 c + + 표준 라이브러리는 혼합 코드에서 사용할 수 있습니다. 제공 된 CRT 및 c + + 표준 라이브러리를 확인할 수 없습니다. 궁극적으로 호출은 네이티브 코드에서 사용 하는 것과 동일한 CRT 및 c + + 표준 라이브러리에 계속 라우팅됩니다.

- 혼합 이미지에서 통합 예외 처리를 수정 합니다.

- 혼합 이미지에서 c + + 변수를 정적으로 초기화 합니다.

- 관리 코드에서 AppDomain 별 및 프로세스별 변수를 지원 합니다.

- Visual Studio 2003 이전 버전에서 컴파일된 혼합 Dll에 적용 된 로더 잠금 문제를 해결 합니다.

또한이 지원에는 다음과 같은 제한 사항이 있습니다.

- **/Clr** 을 사용 하 여 컴파일된 코드에는 CRT DLL 모델만 지원 됩니다. **/Clr** 빌드를 지 원하는 정적 CRT 라이브러리가 없습니다.

## <a name="see-also"></a>참고 항목

- [혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
