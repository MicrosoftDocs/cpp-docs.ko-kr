---
description: '자세히 알아보기: 혼합형 (네이티브 및 관리) 어셈블리'
title: 혼합형(네이티브 및 관리) 어셈블리
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: b96ccb5a521cf009f7feabef01a292ac805b0b4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253640"
---
# <a name="mixed-native-and-managed-assemblies"></a>혼합형(네이티브 및 관리형) 어셈블리

혼합 어셈블리에는 관리 되지 않는 컴퓨터 지침과 MSIL 명령이 모두 포함 될 수 있습니다. 이렇게 하면 네이티브 c + + 라이브러리와의 호환성을 유지 하면서 .NET 구성 요소에서를 호출 하 고 호출할 수 있습니다. 개발자는 혼합 어셈블리를 사용 하 여 .NET 및 네이티브 c + + 코드를 혼합 하 여 응용 프로그램을 제작할 수 있습니다.

예를 들어, 네이티브 c + + 코드로 구성 된 기존 라이브러리는 **/clr** 컴파일러 스위치를 사용 하 여 모듈을 하나만 다시 컴파일하여 .net 플랫폼으로 가져올 수 있습니다. 이 모듈은 .NET 기능을 사용할 수 있지만 응용 프로그램의 나머지 부분과 호환 됩니다. 동일한 파일 내에서 함수 별로 관리 되는 컴파일 및 네이티브 컴파일을 결정할 수도 있습니다 (관리 되는 [, 관리 되지 않음](../preprocessor/managed-unmanaged.md)참조).

Visual C++ **/clr** 컴파일러 옵션을 사용 하 여 혼합 된 관리 되는 어셈블리의 생성만 지원 합니다. **/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다. 순수 하거나 안정형으로 관리 되는 어셈블리를 사용 해야 하는 경우 c #을 사용 하 여 만드는 것이 좋습니다.

이전 버전의 Microsoft c + + 컴파일러 도구 집합에서는 혼합, 순수형 및 안정형의 세 가지 관리 되는 어셈블리 형식이 생성 되었습니다. 두 번째는 [순수형 및 안정형 코드 (c + +/cli)](../dotnet/pure-and-verifiable-code-cpp-cli.md)에서 설명 합니다.

## <a name="in-this-section"></a>섹션 내용

[방법:/clr로 마이그레이션](../dotnet/how-to-migrate-to-clr.md)<br/>
응용 프로그램에서 .NET 기능을 도입 하거나 업그레이드 하는 데 권장 되는 단계에 대해 설명 합니다.

[방법:/clr을 사용 하 여 MFC 및 ATL 코드 컴파일](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
공용 언어 런타임을 대상으로 하는 기존 MFC 및 ATL 프로그램을 컴파일하는 방법에 대해 설명 합니다.

[혼합 어셈블리 초기화](../dotnet/initialization-of-mixed-assemblies.md)<br/>
"로더 잠금" 문제 및 해결 방법을 설명 합니다.

[혼합형 어셈블리에 대 한 라이브러리 지원](../dotnet/library-support-for-mixed-assemblies.md)<br/>
**/Clr** 컴파일에서 네이티브 라이브러리를 사용 하는 방법에 대해 설명 합니다.

[성능 고려 사항](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
혼합 어셈블리 및 데이터 마샬링에 대 한 성능 영향을 설명 합니다.

[응용 프로그램 도메인 및 Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
응용 프로그램 도메인에 대 한 Visual C++ 지원에 대해 설명 합니다.

[이중 썽킹](../dotnet/double-thunking-cpp.md)<br/>
관리 되는 함수에 대 한 네이티브 진입점의 성능 영향에 대해 설명 합니다.

[/Clr을 사용 하 여 빌드한 COM 개체를 사용할 때 CLR 종료 시 예외 방지](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
**/Clr** 을 사용 하 여 컴파일된 COM 개체를 사용 하는 관리 되는 응용 프로그램의 적절 한 종료를 보장 하는 방법을 설명 합니다.

[방법: CRT 라이브러리 DLL에 대 한 종속성을 제거 하 여 부분적으로 신뢰할 수 있는 응용 프로그램 만들기](../dotnet/create-a-partially-trusted-application.md)<br/>
msvcm90.dll 종속성을 제거 하 여 Visual C++를 사용 하 여 부분적으로 신뢰할 수 있는 공용 언어 런타임 응용 프로그램을 만드는 방법을 설명 합니다.

혼합형 어셈블리에 대 한 코딩 지침에 대 한 자세한 내용은 [관리 되는 코드와 비관리 코드 상호 운용성](/previous-versions/dotnet/articles/ms973872(v=msdn.10))에 대 한 개요를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [네이티브 및 .NET 상호 운용성](../dotnet/native-and-dotnet-interoperability.md)
