---
title: 혼합형 어셈블리에 대한 라이브러리 지원
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: 42116c09d5b31cf669eb6d5d1e75eae60b2610a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474754"
---
# <a name="library-support-for-mixed-assemblies"></a>혼합형 어셈블리에 대한 라이브러리 지원

C + + 표준 라이브러리를 C 런타임 라이브러리 (CRT)의 사용을 지원 하는 visual c + + ATL 및 MFC 응용 프로그램을 사용 하 여 컴파일된 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)합니다. 따라서 이러한 라이브러리를 사용 하 여도.NET Framework 기능을 사용 하는 기존 응용 프로그램.

> [!IMPORTANT]
> **/clr: pure** 및 **/clr: safe** Visual Studio 2015에서 사용 되지 않고 Visual Studio 2017에서 지원 되지 않는 컴파일러 옵션입니다.

이 지원에는 다음 DLL 및 가져오기 라이브러리에 포함 됩니다.

- 로 컴파일하는 경우 [d] Msvcmrt.lib **/clr**합니다. 혼합형된 어셈블리 링크가 가져오기 라이브러리입니다.

이 지원을 통해 여러 관련 혜택:

- CRT 및 c + + 표준 라이브러리를 혼합된 코드에 사용할 수 있습니다. CRT 및 제공 하는 c + + 표준 라이브러리는 확인할 수 있습니다. 궁극적으로 네이티브 코드에서 사용 하는 호출은 여전히 동일한 CRT 및 c + + 표준 라이브러리에 라우팅됩니다 됩니다.

- 통합 된 예외 처리 혼합 이미지에서를 수정 합니다.

- 혼합된 이미지에서 c + + 변수의 정적 초기화 합니다.

- 관리 코드에서 프로세스별 및 AppDomain 별 변수를 지원 합니다.

- 및 이전 버전 Visual Studio 2003에서 컴파일된 혼합된 Dll에 적용 하는 로더 잠금 문제를 해결 합니다.

또한이 지원에는 다음 제한 사항을 제공합니다.

- 모델에만 해당 CRT DLL로 컴파일된 코드에 대 한 지원 됩니다 **/clr**합니다. 지 원하는 정적 CRT 라이브러리가 **/clr** 빌드합니다.

## <a name="see-also"></a>참고자료

- [혼합형(네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
