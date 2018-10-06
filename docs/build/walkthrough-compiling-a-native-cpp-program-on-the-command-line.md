---
title: '연습: 명령줄에서 네이티브 c + + 프로그램 컴파일 | Microsoft Docs'
ms.custom: conceptual
ms.date: 09/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7f8fad0c4676e8dfedcf8e80332c0a239f230cb
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821194"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>연습: 명령줄에서 네이티브 C++ 프로그램 컴파일

Visual c + + 유니버설 Windows 플랫폼 앱에 대 한 기본적인 콘솔 앱, 데스크톱 앱, 장치 드라이버 및.NET 구성 요소에서 모든 항목을 만들 데 사용할 수 있는 명령줄 c + + 컴파일러를 포함 합니다.

이 연습에서는 basic, "Hello, World" 만든-편집기에서 텍스트를 사용 하 여 c + + 프로그램을 스타일 및 다음 명령줄에서 컴파일합니다. 내용은 명령줄을 사용 하는 대신 Visual Studio IDE를 시도 하려는 경우 [연습: 프로젝트 및 솔루션 (c + +)를 사용 하 여 작업](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) 하거나 [c + + 데스크톱 개발에 Visual Studio IDE를 사용 하 여](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)입니다.

이 연습에서는 표시되는 내용을 입력하는 대신 Visual C++ 프로그램을 사용하거나 다른 도움말 문서의 Visual C++ 코드 샘플을 사용할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

이 연습을 완료 하려면 설치 해야 Visual Studio 및 선택적인 **c + +를 사용한 데스크톱 개발** 워크 로드 또는 Visual Studio에 대 한 명령줄 빌드 도구입니다.

Visual Studio는 다양 한 언어 및 플랫폼에 대 한 완전 한 편집기, 리소스 관리자, 디버거 및 컴파일러를 지 원하는 강력한 통합된 개발 환경 (IDE)입니다. 다운로드 무료 Visual Studio Community edition 등 Visual Studio를 설치 하 고 C/c + + 개발에 대 한 지원을 포함 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 c + + 설치 지원](../build/vscpp-step-0-installation.md)합니다.

명령줄 컴파일러, 도구 및 C 및 c + + 프로그램을 작성 하는 데 필요한 라이브러리가 Visual studio Build Tools를 설치 합니다. 빌드 랩에 안성맞춤입니다 또는 클래스 룸 연습 하 고 비교적 빠르게 설치 합니다. 명령줄 도구만을 설치 하려면 다운로드 [Visual Studio 2017 용 Build Tools](https://go.microsoft.com/fwlink/p/?linkid=875721)합니다.

명령줄에서 C 또는 c + + 프로그램을 빌드할 수 있습니다, 전에 명령줄에서 액세스할 수 있습니다 및 도구가 설치 되어 있는지 확인 해야 합니다. Visual c + +에는 도구, 헤더 및 라이브러리를 사용 하 여 찾으려는 명령줄 환경에 대 한 복잡 한 요구 사항이 있습니다. **일반 명령 프롬프트 창에서 Visual c + +를 사용할 수 없습니다** 몇 가지 준비를 수행 하지 않고 있습니다. 다행히 Visual c + + 명령줄 빌드에 대 한 설정 환경에 있는 개발자 명령 프롬프트를 시작할 수에 대 한 바로 가기 키를 설치 합니다. 그러나 개발자 명령 프롬프트 바로 가기 및를 위치 이름은 거의 모든 버전의 Visual c + + 및 다른 버전의 Windows에서 서로 다릅니다. 첫 번째 연습에서는 작업 사용에 적합 한을 찾는 것입니다.

> [!NOTE]
> 개발자 명령 프롬프트 바로 가기를 컴파일러 및 도구에 대 한 및 모든 필수 헤더 및 라이브러리에 대 한 올바른 경로 자동으로 설정합니다. 값을 설정 해야 이러한 환경을 직접 일반을 사용 하는 경우 **명령 프롬프트** 창입니다. 자세한 내용은 [명령줄 빌드에 맞는 경로 및 환경 변수 설정](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)합니다. 직접 작성 하는 대신 개발자 명령 프롬프트 바로 가기를 사용 하는 것이 좋습니다.

### <a name="open-a-developer-command-prompt"></a>개발자 명령 프롬프트를 열으십시오

1. Windows 10에서 Visual Studio 2017을 설치한 경우 시작 메뉴를 열고 선택한 **모든 앱**합니다. 아래로 스크롤하여 엽니다는 **Visual Studio 2017** 폴더 (Visual Studio 2017 앱 제외). 선택할 **VS 2017 용 개발자 명령 프롬프트** 명령 프롬프트 창을 엽니다.

   Windows 10에서 Microsoft Visual c + + Build Tools 2015를 설치한 경우 엽니다는 **시작** 메뉴 선택 **모든 앱**합니다. 아래로 스크롤하여 엽니다는 **Visual c + + Build Tools** 폴더입니다. 선택할 **Visual c + + 2015 x86 Native Tools 명령 프롬프트** 명령 프롬프트 창을 엽니다.

   Visual Studio의 다른 버전을 사용 하거나 다른 버전의 Windows 실행 하는 경우 시작 메뉴에서 확인 하거나 개발자 명령 프롬프트 바로 가기를 포함 하는 Visual Studio tools 폴더에 대 한 페이지를 시작 합니다. 또한 "개발자 명령 프롬프트"를 검색 하 고 Visual Studio의 설치 된 버전과 일치 하는 하나를 선택 하려면 Windows 검색 기능을 사용할 수 있습니다. 바로 가기를 사용 하 여 명령 프롬프트 창을 엽니다.

1. 다음으로, Visual c + + 개발자 명령 프롬프트를 올바르게 설정 되어 있는지 확인 합니다. 명령 프롬프트 창에서 입력 `cl` 출력 같이 표시 되는지 확인 합니다.

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   현재 디렉터리 또는 Visual c + + 및 설치 된 업데이트의 버전에 따라 버전 번호가 차이점이 있을 수 있습니다. 위의 출력은 표시 되는 항목을 다음 경우 명령줄에서 C 또는 c + + 프로그램을 빌드할 준비가 됩니다.

   > [!NOTE]
   > "'C l' is not recognized as는 내부 또는 외부 명령, 실행할 수 있는 프로그램 또는 배치 파일"와 같은 오류가 발생할 경우 오류 C1034 또는 오류 LNK1104 실행할 때 합니다 **cl** 하거나 개발자 명령 프롬프트를 사용 하지 않는 명령을 또는 Visual c + + 설치를 사용 하 여 문제가 발생 했습니다. 계속 하기 전에이 문제를 수정 해야 합니다.

   개발자 명령 프롬프트 바로 가기를 찾을 수 없으면 또는 입력 하면 오류 메시지를 받게 되 면 `cl`, 다음 Visual c + + 설치에 문제가 있을 수 있습니다. Visual Studio에서 Visual c + + 구성 요소를 다시 설치 하거나 Microsoft Visual c + + Build Tools를 다시 설치 하십시오. 작동 될 때까지 다음 섹션으로 하지 마십시오. 설치 및 Visual c + + 문제 해결에 대 한 자세한 내용은 참조 하세요. [Visual Studio 설치](/visualstudio/install/install-visual-studio)합니다.

   > [!NOTE]
   > 개발자 명령 프롬프트 바로 가기에 대 한 바로 가기 메뉴를 열고 선택한 후 마우스 오른쪽 단추로 클릭 해야 컴퓨터 시스템 보안 구성에서 Windows의 버전에 따라 **관리자 권한으로 실행** 를 성공적으로 작성 하 고이 연습을 수행 하 여 만든 프로그램을 실행 합니다.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Visual c + + 소스 파일을 만들고 명령줄에서 컴파일하십시오.

1. 개발자 명령 프롬프트 창에서 입력 `md c:\hello` 디렉터리를 만들고 enter `cd c:\hello` 해당 디렉터리로 변경 합니다. 이 디렉터리는 소스 파일 및 컴파일된 프로그램에서 생성 되는 위치입니다.

1. 입력 `notepad hello.cpp` 명령 프롬프트 창에서.

   선택할 **예** 메모장이 파일을 만들 수 있습니다. 이 단계는 hello.cpp 라는 파일에 코드를 입력할 준비가 빈 메모장 창이 열립니다.

1. 메모장에서 다음 코드 줄을 입력 합니다.

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   이 코드는 화면에서 한 줄의 텍스트를 작성 하 고 종료 하는 간단한 프로그램입니다. 오류를 최소화하기 위해 이 코드를 복사하여 메모장에 붙여넣습니다.

1. 작업을 저장합니다. 메모장의 **파일** 메뉴에서 **저장**을 선택합니다.

   축 하 hello.cpp 컴파일할 준비가 된 Visual c + + 소스 파일을 만들었습니다.

1. 개발자 명령 프롬프트 창으로 전환 합니다. 입력 `dir` c:\hello 디렉터리의 내용을 나열 하려면 명령 프롬프트에서. 원본 파일 hello.cpp 디렉터리 나열 다음과 비슷하게 표시 됩니다.

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   날짜 및 기타 세부 정보는 컴퓨터에 달라 집니다. 소스 코드 파일이 보이지 않으면 hello.cpp 만든 c:\hello 디렉터리로 변경 했는지 및 메모장에서이 디렉터리에 소스 파일을 저장 했는지 확인 합니다. 또한.cpp 파일 이름 확장명을.txt 확장명이 아닌을 사용 하 여 소스 코드를 저장 해야 합니다.

1. 개발자 명령 프롬프트에서 입력 `cl /EHsc hello.cpp` 프로그램 컴파일 시.

   cl.exe 컴파일러는 컴파일된 코드가 포함된 .obj 파일을 만든 다음 링커를 실행하여 실행 프로그램인 hello.exe를 만듭니다. 이 이름은 컴파일러에서 표시하는 출력 정보 줄에 나타납니다. 컴파일러의 출력 같이 표시 됩니다.

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > "'C l' is not recognized as는 내부 또는 외부 명령, 실행할 수 있는 프로그램 또는 배치 파일"와 같은 오류가 발생할 경우 오류 C1034 또는 오류 LNK1104가 개발자 명령 프롬프트에 올바르게 설정 되지 않았습니다. 이 문제를 해결 하는 방법에 대 한 내용은 돌아가서 합니다 **개발자 명령 프롬프트를 열고** 섹션입니다.

   > [!NOTE]
   > 다른 컴파일러 또는 링커 오류 또는 경고를 받게 되 면 오류를 수정, 그런 다음 저장 하 고 컴파일러를 다시 실행 하도록 소스 코드를 검토 합니다. 특정 오류에 대 한 자세한 오류 번호를 확인 하려면 MSDN 페이지 검색 상자를 사용 합니다.

7. hello.exe 프로그램을 실행하려면 명령 프롬프트에서 `hello`를 입력합니다.

   프로그램이 다음 텍스트를 표시하고 종료됩니다.

   ```Output
   Hello, world, from Visual C++!
   ```

   축, 컴파일 및 명령줄 도구를 사용 하 여 c + + 프로그램을 실행 했습니다.

## <a name="next-steps"></a>다음 단계

이 "Hello, World" 예제는 간단 c + + 프로그램을 가져올 수 있습니다. 실제 프로그램에는 헤더 파일 및 자세한 원본 파일을 라이브러리에 연결 하 고 유용한 작업을 수행 합니다.

표시 된 예제 코드를 입력 하는 대신 사용자 고유의 c + + 코드를 빌드하려면이 연습의 단계를 사용할 수 있습니다. 다른 곳에서 검색 하는 많은 c + + 코드 샘플 프로그램을 빌드할 수 있습니다. 소스 코드를 입력 하 고 모든 쓰기 가능한 디렉터리에서 앱을 빌드할 수 있습니다. 기본적으로 Visual Studio IDE는 Visual Studio의 버전에 대 한 Visual Studio 폴더의 프로젝트 하위 폴더에 문서 폴더에 프로젝트를 만듭니다.

추가 소스 코드 파일에는 프로그램을 컴파일하려면 입력에서 명령 줄에 모두 같은:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

`/EHsc` 명령줄 옵션은 컴파일러에 c + + 예외 처리를 사용 하도록 지시 합니다. 자세한 내용은 [/EH(예외 처리 모델)](../build/reference/eh-exception-handling-model.md)를 참조하세요.

추가 원본 파일을 제공 하는 경우 컴파일러는 프로그램 이름을 만드는 데 첫 번째 입력된 파일을 사용 합니다. 이 경우 file1.exe 프로그램을 출력 합니다. 추가 program1.exe를 이름으로 변경 하는 [/출력](../build/reference/out-output-file-name.md) 링커 옵션:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

자세한 프로그래밍 실수를 자동으로 catch 하려면 하나를 사용 하 여 컴파일하는 권장 합니다 [/w3](../build/reference/compiler-option-warning-level.md) 하거나 [/w4](../build/reference/compiler-option-warning-level.md) 경고 수준 옵션:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

컴파일러에서 cl.exe에 더 많은 옵션을 빌드, 최적화, 디버그, 적용 하 고 코드를 분석할 수 있습니다. 빠른 목록을 입력 `cl /?` 개발자 명령 프롬프트에서. 또한 컴파일 및 연결할 수 별도로 있으며 더 복잡 한 빌드 시나리오에서 링커 옵션을 적용 합니다. 컴파일러 및 링커 옵션 및 사용에 대 한 자세한 내용은 참조 하세요. [C/c + + 빌드 참조](../build/reference/c-cpp-building-reference.md)합니다.

구성 하 고 명령줄에서 보다 복잡 한 프로젝트를 빌드할 NMAKE 메이크파일, 있고 MSBuild 및 프로젝트 파일을 사용할 수 있습니다. 이러한 도구 사용에 대 한 자세한 내용은 참조 하세요. [NMAKE 참조](../build/nmake-reference.md) 하 고 [MSBuild](../build/msbuild-visual-cpp.md)합니다.

C 및 c + + 언어는 유사 하지만 동일 하지는 않습니다. Visual c + + 컴파일러 코드를 컴파일할 때 사용할 언어를 결정 하는 간단한 규칙을 사용 합니다. 기본적으로 Visual C++ 컴파일러는 .c로 끝나는 파일은 모두 C 소스 코드로, .cpp로 끝나는 파일은 모두 C++ 소스 코드로 취급합니다. 모든 파일 종속 되지 않는 파일 이름 확장명에 c + +로 취급 하도록 컴파일러를 강제 적용 하려면 사용 합니다 [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 컴파일러 옵션입니다.

Visual c + + 컴파일러는 ISO C99 표준을 호환 되지만 엄격 하 게 준수 하지 않는 한 C 런타임 라이브러리 (CRT)를 포함 합니다. 대부분의 경우에서 이식 가능한 코드 컴파일 및 예상 대로 실행 합니다. Visual c + + ISO C11의 CRT 변경 내용 중 일부를 지원 하지 않습니다. 특정 라이브러리 함수 및 POSIX 함수 이름을 Visual c + + 컴파일러에서 사용 되지 않습니다. 함수는 지원 되지만 기본 이름이 변경 되었습니다. 자세한 내용은 [CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md) 하 고 [컴파일러 경고 (수준 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)합니다.

## <a name="see-also"></a>참고자료

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[C/C++ 프로그램 빌드](../build/building-c-cpp-programs.md)<br/>
[컴파일러 옵션](../build/reference/compiler-options.md)
