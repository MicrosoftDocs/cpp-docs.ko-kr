---
description: '자세한 정보: 방법: winmdidl.exe 및 midlrt.exe를 사용 하 여 windows 메타 데이터에서 .h 파일 만들기'
title: '방법: winmdidl.exe 및 midlrt.exe를 사용하여 Windows 메타데이터에서 .h 파일 만들기'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
ms.openlocfilehash: be76f0cb898017c575356f90fcd043f987a0dbad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209258"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>방법: winmdidl.exe 및 midlrt.exe를 사용하여 Windows 메타데이터에서 .h 파일 만들기

Winmdidl.exe 및 midlrt.exe는 Windows 런타임 구성 요소 및 네이티브 C++ 코드 사이의 COM 수준의 상호 작용을 지원합니다. Winmdidl.exe는 입력으로 .winmd 파일을 사용하여 Windows 런타임 구성 요소에 대한 메타데이터를 포함하고 IDL 파일을 출력합니다. Midlrt.exe는 해당 IDL 파일을 C++ 코드에서 사용할 수 있는 헤더 파일로 변환합니다. 두 도구 모두 명령줄에서 실행됩니다.

이러한 도구는 다음 두 가지 주요 시나리오에서 사용할 수 있습니다.

- Windows 런타임 템플릿 라이브러리(WRL)를 사용하여 작성된 C++ 앱에서 사용자 지정 Windows 런타임 구성 요소를 사용할 수 있도록 사용자 지정 IDL 및 헤더 파일을 만드는 경우

- Windows 런타임 구성 요소에서 사용자 정의 이벤트 형식에 대한 프록시와 스텁 파일을 생성하는 경우 자세한 내용은 [Windows 런타임 구성 요소의 사용자 지정 이벤트 및 이벤트 접근자](/windows/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components)를 참조 하세요.

이러한 도구는 사용자 지정 .winmd 파일을 구문 분석하는 데 필요합니다. Windows 운영 체제 구성 요소에 대한 .idl 및.h 파일이 이미 생성되어 있습니다. 기본적으로 Windows 8.1는 파일 \ 사용자 파일 (x86) \Windows Kits\8.1\Include\winrt에 있습니다 \\ .

## <a name="location-of-the-tools"></a>도구 위치

기본적으로 [Windows 8.1에서는 winmdidl.exe 및 midlrt.exe C:\Program Files (x86) \Windows Kits\8.1에 있습니다 \\ . 도구 버전은 \bin\x86\ 및 \bin\x64\ 폴더에서 사용할 수 있습니다.

## <a name="winmdidl-command-line-arguments"></a>Winmdidl 명령줄 인수

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
콘솔이 winmdidl 저작권 메시지 및 버전 번호를 표시하는 것을 방지합니다.

**/suppressversioncheck**<br/>
사용되지 않습니다.

**/시간**<br/>
콘솔 출력에서 총 실행 시간을 표시합니다.

**/outdir:**<em>dir</em><br/>
출력 디렉터리를 지정합니다. 경로에 공백이 있으면 따옴표를 사용합니다. 기본 출력 디렉터리는 *\<drive>* : \Users \\ *\<username>* \AppData\Local\VirtualStore\Program Files (X86) \Microsoft Visual Studio 12.0 \\ 입니다.

**/sl:**<em>파일</em><br/>
기본 저작권 메시지 앞에 오는 사용자 지정 텍스트가 포함된 파일을 지정하고 생성된 .idl 파일의 상단에 winmdidl 버전 번호를 표시합니다. 경로에 공백이 있으면 따옴표를 사용합니다.

**/utf8**<br/>
파일이 UTF-8로 포맷되도록 합니다.

*Winmdfile*<br/>
구문 분석할 .winmd 파일의 이름입니다. 경로에 공백이 있으면 따옴표를 사용합니다.

## <a name="midlrt-command-line-arguments"></a>Midlrt 명령줄 인수

[Midlrt 및 Windows 런타임 구성 요소를](/windows/win32/Midl/midlrt-and-windows-runtime-components)참조 하세요.

## <a name="examples"></a>예제

다음 예제에서는 Visual Studio x86 명령 프롬프트의 winmdidl 명령을 보여 줍니다. 출력 디렉토리와 생성된 .idl 파일에 추가할 특정 배너 텍스트를 포함하는 파일을 지정합니다.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

다음 예제에서는 작업이 성공했는지 여부를 나타내는 winmdidl의 콘솔 디스플레이를 보여 줍니다.

**C:\users\giraffe\documents \\ \ Test_for_winmdidl를 생성 하 고 있습니다.**

다음으로, midlrt는 생성된 IDL 파일에서 실행됩니다. **Metadata_dir** 인수는 .idl 파일의 이름 뒤에 지정 됩니다. \WinMetadata\ 경로는 필수이며, windows.winmd의 위치입니다.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\username\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>설명

Winmdidl 작업의 출력 파일은 입력 파일과 이름이 같지만 확장명이 .idl입니다.

WRL에서 액세스할 수 있는 Windows 런타임 구성 요소를 개발하는 경우 .idl 및 .h 파일이 각 빌드에 생성되도록 빌드 후 단계로 winmdidl.exe 및 midlrt.exe를 실행할 수 있습니다. 예를 들어 [Windows 런타임 구성 요소에서 이벤트 발생](/windows/uwp/winrt-components/raising-events-in-windows-runtime-components)을 참조 하세요.
