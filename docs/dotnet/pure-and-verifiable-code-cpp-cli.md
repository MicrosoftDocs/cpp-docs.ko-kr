---
description: '자세히 알아보기: 순수형 및 안정형 코드 (c + +/CLI)'
title: 순수형 및 안정형 코드(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
ms.openlocfilehash: 64224f7f462b5e11e522648a5b64ec9d568dc53f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276766"
---
# <a name="pure-and-verifiable-code-ccli"></a>순수형 및 안정형 코드 (c + +/CLI)

.NET 프로그래밍의 경우 Visual Studio 2017의 Visual C++ [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md) 컴파일러 옵션을 사용 하 여 혼합 어셈블리 만들기를 지원 합니다. **/Clr: pure** 및 **clr: Safe** 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다. 코드를 안전 하거나 확인 해야 하는 경우 c #으로 이식 하는 것이 좋습니다.

## <a name="mixed-clr"></a>Mixed (/clr)

혼합 어셈블리 ( **/clr** 로 컴파일된)는 관리 되지 않는 부분과 관리 되는 부분을 모두 포함 하 여 .net 기능을 사용할 수 있도록 하 고 네이티브 코드를 계속 포함 합니다. 이렇게 하면 전체 프로젝트를 다시 작성할 필요 없이 .NET 기능을 사용 하도록 응용 프로그램 및 구성 요소를 업데이트할 수 있습니다. 이러한 방식으로 Visual C++를 사용 하 여 관리 코드와 네이티브 코드를 혼합 하면 c + + Interop 라고 합니다. 자세한 내용은 [혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md) 및 [네이티브 및 .net 상호 운용성](../dotnet/native-and-dotnet-interoperability.md)을 참조 하세요.

P/Invoke를 통해 관리 되는 어셈블리에서 네이티브 Dll로 생성 된 호출은 컴파일되지만 보안 설정에 따라 런타임에 실패할 수 있습니다.

컴파일러를 전달 하는 코딩 시나리오는 하나 이며,이 경우 확인할 수 없는 어셈블리가 생성 됩니다. 범위 확인 연산자를 사용 하 여 개체 인스턴스를 통해 가상 함수를 호출 합니다.  예를 들어 `MyObj -> A::VirtualFunction();`을 참조하십시오.

## <a name="see-also"></a>참고 항목

- [C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
