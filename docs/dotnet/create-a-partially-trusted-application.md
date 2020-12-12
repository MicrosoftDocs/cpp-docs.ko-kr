---
description: '자세한 정보: 방법: CRT 라이브러리 DLL에 대 한 종속성을 제거 하 여 부분적으로 신뢰할 수 있는 응용 프로그램 만들기'
title: '방법: 부분적으로 신뢰할 수 있는 응용 프로그램 만들기 (c + +/CLI)'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: 937262595df4415d5620b60d9ccd8c17a6c44abf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124282"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>방법: CRT 라이브러리 DLL에 대한 종속성을 제거하여 부분적으로 신뢰할 수 있는 애플리케이션 만들기

이 항목에서는 msvcm90.dll에서 종속성을 제거 하 여 Visual C++를 사용 하 여 부분적으로 신뢰할 수 있는 공용 언어 런타임 응용 프로그램을 만드는 방법을 설명 합니다.

**/Clr** 을 사용 하 여 빌드된 Visual C++ 응용 프로그램은 C 런타임 라이브러리의 일부인 msvcm90.dll에 종속 됩니다. 부분 신뢰 환경에서 응용 프로그램을 사용 하려는 경우 CLR은 DLL에 특정 코드 액세스 보안 규칙을 적용 합니다. 따라서 msvcm90.dll 네이티브 코드를 포함 하 고 코드 액세스 보안 정책을 적용할 수 없기 때문에이 종속성을 제거 해야 합니다.

응용 프로그램에서 C 런타임 라이브러리의 기능을 사용 하지 않고 코드에서이 라이브러리에 대 한 종속성을 제거 하려면 **/nodefaultlib: msvcmrt.lib** 링커 옵션을 사용 하 고 ptrustm .lib 또는 ptrustm .lib와 연결 해야 합니다. 이러한 라이브러리는 응용 프로그램의 초기화 및 초기화 개체 파일, 초기화 코드에서 사용 하는 예외 클래스 및 관리 되는 예외 처리 코드를 포함 합니다. 이러한 라이브러리 중 하나에 연결 하면 msvcm90.dll에 대 한 종속성이 제거 됩니다.

> [!NOTE]
> 어셈블리 초기화의 순서는 ptrust 라이브러리를 사용 하는 응용 프로그램에 대해 다를 수 있습니다. 일반적인 응용 프로그램의 경우 어셈블리는 일반적으로 로드 되는 역순으로 언로드되고,이는 보장 되지 않습니다. 부분 신뢰 응용 프로그램의 경우 어셈블리는 대개 로드 된 순서와 동일한 순서로 언로드됩니다. 또한이는 보장 되지 않습니다.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>부분적으로 신뢰할 수 있는 혼합 (/clr) 응용 프로그램을 만들려면

1. msvcm90.dll에 대 한 종속성을 제거 하려면 **/nodefaultlib: msvcmrt.lib** 링커 옵션을 사용 하 여이 라이브러리를 포함 하지 않도록 링커에 지정 해야 합니다. Visual Studio 개발 환경을 사용 하 여 또는 프로그래밍 방식으로이 작업을 수행 하는 방법에 대 한 자세한 내용은 [/nodefaultlib (라이브러리 무시)](../build/reference/nodefaultlib-ignore-libraries.md)를 참조 하세요.

1. Ptrustm 라이브러리 중 하나를 링커 입력 종속성에 추가 합니다. 릴리스 모드에서 응용 프로그램을 빌드하는 경우 ptrustm .lib를 사용 합니다. 디버그 모드의 경우 ptrustmd .lib를 사용 합니다. Visual Studio 개발 환경을 사용 하 여 또는 프로그래밍 방식으로이 작업을 수행 하는 방법에 대 한 자세한 내용은을 참조 하십시오 [. 링커 입력 파일로 서의 Lib 파일](../build/reference/dot-lib-files-as-linker-input.md)입니다.

## <a name="see-also"></a>참고 항목

[혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[혼합 어셈블리 초기화](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[혼합형 어셈블리에 대 한 라이브러리 지원](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (링커에 옵션 전달)](../build/reference/link-pass-options-to-linker.md)
