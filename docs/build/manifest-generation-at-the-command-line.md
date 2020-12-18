---
description: '자세한 정보: 명령줄에서 매니페스트 생성'
title: 명령줄에서 매니페스트 생성
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 30b826e0fe98a143f58d7987203881a8fd8e601b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176459"
---
# <a name="manifest-generation-at-the-command-line"></a>명령줄에서 매니페스트 생성

명령줄에서 nmake 또는 유사한 도구를 사용하여 C/C++ 애플리케이션을 빌드할 경우 링커에서 모든 개체 파일을 처리하고 최종 이진 파일을 빌드한 후에 매니페스트가 생성됩니다. 링커는 개체 파일에 저장된 어셈블리 정보를 수집하고 이 정보를 최종 매니페스트 파일로 결합합니다. 기본적으로 링커는 최종 이진 파일을 설명하는 *binary_name*.*extension*.manifest라는 파일을 생성합니다. 링커는 매니페스트 파일을 이진 파일 안에 포함하지 않고 매니페스트를 외부 파일로만 생성할 수 있습니다. 매니페스트를 최종 이진 파일에 포함하는 여러 가지 방법이 있습니다. 예를 들어 [매니페스트 도구(mt.exe)](/windows/win32/sbscs/mt-exe)를 사용하거나 매니페스트를 리소스 파일로 컴파일할 수 있습니다. 증분 링크, 서명, 편집하며 계속하기와 같은 기능을 사용할 수 있도록 최종 이진 내에 매니페스트를 포함할 경우 특정 규칙을 따라야 합니다. 해당 옵션과 기타 옵션에 대해서는 명령줄에서 빌드할 때 [방법: C/C++ 애플리케이션에 매니페스트 포함](how-to-embed-a-manifest-inside-a-c-cpp-application.md)에서 설명합니다.

## <a name="see-also"></a>참조

[매니페스트](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL(증분 링크)](reference/incremental-link-incrementally.md)<br/>
[강력한 이름 어셈블리(어셈블리 서명)(C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[편집하며 계속하기](/visualstudio/debugger/edit-and-continue)<br/>
[ 프로그램의 매니페스트 생성 이해](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
