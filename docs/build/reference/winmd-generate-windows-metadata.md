---
description: 다음에 대 한 자세한 정보:/WINMD (Windows 메타 데이터 생성)
title: /WINMD(Windows 메타데이터 생성)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 7cf52a49716e6ec30a29c7e6a96fe7a078b4830c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259086"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD(Windows 메타데이터 생성)

Windows 런타임 메타데이터(.winmd) 파일을 생성할 수 있게 해줍니다.

> **/Winmd** \[ **:**{**NO** \| **ONLY**}]

## <a name="arguments"></a>인수

**/WINMD**<br/>
유니버설 Windows 플랫폼 앱에 대 한 기본 설정입니다. 링커가 바이너리 실행 파일 및 .winmd 메타데이터 파일을 모두 생성합니다.

**/WINMD:NO**<br/>
링커가 바이너리 실행 파일만 생성하고 .winmd 파일은 생성하지 않습니다.

**/WINMD:ONLY**<br/>
링커가 .winmd 파일만 생성하고 바이너리 실행 파일은 생성하지 않습니다.

## <a name="remarks"></a>설명

**/Winl** 링커 옵션은 UWP 앱 및 Windows 런타임 구성 요소에서 Windows 런타임 메타 데이터 (WINMD) 파일의 생성을 제어 하는 데 사용 됩니다. Winmd 파일은 Windows 런타임 형식에 대 한 메타 데이터를 포함 하는 DLL의 종류 이며 런타임 구성 요소의 경우 이러한 형식의 구현입니다. 메타 데이터는 [ECMA-335](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 표준을 따릅니다.

기본적으로 출력 파일 이름에는 *binaryname*. winmd 형식이 있습니다. 다른 파일 이름을 지정 하려면 [/WINMDFILE](winmdfile-specify-winmd-file.md) 옵션을 사용 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **Windows 메타 데이터** 속성 페이지를 선택 합니다.

1. **Windows 메타 데이터 생성** 드롭다운 목록 상자에서 원하는 옵션을 선택 합니다.

## <a name="see-also"></a>참고 항목

[연습: 간단한 Windows 런타임 구성 요소 만들기 및 JavaScript에서 호출](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Microsoft 인터페이스 정의 언어 3.0 소개](/uwp/midl-3/intro)<br/>
[/WINMDFILE (winmd 파일 지정)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (winmd 키 파일 지정)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (키 컨테이너 지정)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (winmd에 부분적으로 서명)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
