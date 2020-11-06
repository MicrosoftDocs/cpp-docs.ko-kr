---
title: 링커 도구 오류 LNK1104
description: Microsoft C 및 c + + (MSVC) 링커 오류 LNK1104, 원인 및 가능한 해결 방법을 설명 합니다.
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: 2eea6885537037db496a2f42e0fff0ffa69127e3
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334210"
---
# <a name="linker-tools-error-lnk1104"></a>링커 도구 오류 LNK1104

> ' *filename* ' 파일을 열 수 없습니다.

이 오류는 링커에서 파일을 읽거나 쓰기 위해 파일을 열지 못할 때 보고 됩니다. 문제의 가장 일반적인 두 가지 원인은 다음과 같습니다.

- 프로그램이 이미 실행 되 고 있거나 디버거에서 로드 되었습니다.

- 라이브러리 경로가 잘못 되었거나 큰따옴표로 묶여 있지 않습니다.

이 오류의 원인은 여러 가지가 있습니다. 범위를 좁히려면 먼저 파일 *이름* 파일의 종류를 확인 합니다. 그런 다음, 다음 섹션을 참조 하 여 특정 문제를 식별 하 고 해결 합니다.

## <a name="cant-open-your-app-or-its-pdb-file"></a>앱 또는 .pdb 파일을 열 수 없습니다.

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>앱이 실행 되 고 있거나 디버거에서 로드 되었습니다.

*Filename* 이 실행 파일의 이름 이거나 연결 된 .pdb 파일인 경우 응용 프로그램이 이미 실행 중인지 확인 합니다. 그런 다음 디버거에서 로드 되는지 확인 합니다. 이 문제를 해결 하려면 프로그램을 중지 하 고 다시 빌드하기 전에 디버거에서 언로드합니다. 앱이 리소스 편집기와 같은 다른 프로그램에서 열려 있는 경우 닫습니다. 프로그램이 응답 하지 않는 경우 작업 관리자를 사용 하 여 프로세스를 종료 해야 할 수 있습니다. Visual Studio를 닫았다가 다시 시작 해야 할 수도 있습니다.

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>바이러스 백신 검색으로 앱을 잠 궜 습니다.

바이러스 백신 프로그램은 일반적으로 새로 만든 파일, 특히 .exe 및 .dll 실행 파일에 대 한 액세스를 차단 합니다. 이 문제를 해결 하려면 바이러스 백신 스캐너에서 프로젝트 빌드 디렉터리를 제외 하십시오.

## <a name="cant-open-a-microsoft-library-file"></a>Microsoft 라이브러리 파일을 열 수 없습니다.

### <a name="windows-libraries-such-as-kernel32lib"></a>Kernel32.dll와 같은 Windows 라이브러리

열 수 없는 파일이 Microsoft에서 제공 하는 표준 라이브러리 파일 (예: *kernel32.dll* ) 중 하나인 경우 프로젝트 구성 오류 또는 설치 오류가 있을 수 있습니다. Windows SDK 설치 되어 있는지 확인 합니다. 프로젝트에서 MFC와 같은 다른 Microsoft 라이브러리를 필요로 하는 경우 Visual Studio 설치 관리자를 통해서도 MFC 구성 요소를 설치 했는지 확인 합니다. 설치 관리자를 다시 실행 하 여 언제 든 지 선택적 구성 요소를 추가할 수 있습니다. 자세한 내용은 [Visual Studio 수정](/visualstudio/install/modify-visual-studio)을 참조 하세요. 설치 관리자의 **개별 구성 요소** 탭을 사용 하 여 특정 라이브러리 및 sdk를 선택할 수 있습니다.

### <a name="versioned-vcruntime-libraries"></a>버전이 지정 된 vcruntime 라이브러리

오류 메시지에 *msvcr120.dll* 와 같은 버전의 Microsoft 라이브러리가 있는 경우 해당 컴파일러 버전에 대 한 플랫폼 도구 집합이 설치 되지 않을 수 있습니다. 이 문제를 해결 하려면 두 가지 옵션이 있습니다. 현재 플랫폼 도구 집합을 사용 하도록 프로젝트를 업그레이드 하거나 이전 도구 집합을 설치 하 고 변경 되지 않은 상태로 프로젝트를 빌드합니다. 자세한 내용은 [이전 버전의 Visual C++에서 프로젝트 업그레이드](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) 및 [Visual Studio에서 네이티브 다중 대상 지정을 사용 하 여 이전 프로젝트 빌드](../../porting/use-native-multi-targeting.md)를 참조 하세요.

### <a name="retail-debug-or-platform-specific-libraries"></a>정품, 디버그 또는 플랫폼별 라이브러리

새 대상 플랫폼 또는 구성 (예: 일반 정품 또는 ARM64)에 대해 처음 빌드할 때 오류가 발생할 수 있습니다. IDE에서 [일반 속성 페이지](../../build/reference/general-property-page-project.md) 에 지정 된 **플랫폼 도구 집합** 및 **Windows SDK 버전이** 설치 되어 있는지 확인 합니다. 또한 [VC + + 디렉터리 속성 페이지](../../build/reference/vcpp-directories-property-page.md)에 지정 된 **라이브러리 디렉터리** 에서 필요한 라이브러리를 사용할 수 있는지 확인 합니다. 각 구성의 속성 (예: 디버그, 일반 정품, x86 또는 ARM64)을 확인 합니다. 한 빌드가 작동 하지만 다른 빌드가 작동 하지 않는 경우 두 설정을 비교 합니다. 누락 된 필수 도구 및 라이브러리를 설치 합니다.

### <a name="the-vccorliblib-library"></a>Vccorlib .lib 라이브러리

UWP (유니버설 Windows) 앱 또는 구성 요소에 대 한 스펙터 완화 된 라이브러리가 없습니다. 오류 메시지에 *vccorlib. lib* 가 포함 된 경우 UWP 프로젝트에서 [/Qspectre](../../build/reference/qspectre.md) 를 사용 하도록 설정 했을 수 있습니다. 이 문제를 해결 하려면 **/Qspectre** 컴파일러 옵션을 사용 하지 않도록 설정 합니다. Visual Studio에서 **스펙터 완화** 속성을 변경 합니다. 프로젝트 속성 페이지 대화 상자의 **C/c + +**  >  **코드 생성** 페이지에 **Property Pages** 있습니다.

### <a name="libraries-in-projects-from-online-or-other-sources"></a>온라인 또는 다른 원본에서 프로젝트의 라이브러리

다른 컴퓨터에서 복사한 프로젝트를 빌드하는 경우 라이브러리 설치 위치는 다를 수 있습니다. 명령줄 빌드의 경우 빌드에 대해 LIB 환경 변수 및 라이브러리 경로가 올바르게 설정 되었는지 확인 합니다. Visual Studio에서 프로젝트에 대 한 속성 페이지에 설정 된 현재 라이브러리 경로를 보고 편집할 수 있습니다. **VC + + 디렉터리** 페이지에서 **라이브러리 디렉터리** 속성의 드롭다운 컨트롤을 선택한 다음 **편집** 을 선택 합니다. **라이브러리 디렉터리** 대화 상자의 **계산 된 값** 섹션에 라이브러리 파일에 대해 검색 된 현재 경로가 나열 됩니다. 로컬 라이브러리를 가리키도록 이러한 경로를 업데이트 합니다.

### <a name="updated-windows-sdk-libraries"></a>업데이트 된 Windows SDK 라이브러리

이 오류는 Windows SDK에 대 한 Visual Studio 경로가 만료 된 경우에 발생할 수 있습니다. Visual Studio 설치 관리자와 독립적으로 최신 Windows SDK를 설치 하는 경우에 발생할 수 있습니다. IDE에서이 문제를 해결 하려면 [VC + + 디렉터리 속성 페이지](../../build/reference/vcpp-directories-property-page.md)에 지정 된 경로를 업데이트 합니다. 새 SDK와 일치 하도록 경로의 버전을 설정 합니다. 개발자 명령 프롬프트 사용 하는 경우 새 SDK 경로를 사용 하 여 환경 변수를 초기화 하는 배치 파일을 업데이트 합니다. Visual Studio 설치 관리자를 사용 하 여 업데이트 된 Sdk를 설치 하면이 문제를 방지할 수 있습니다.

## <a name="cant-open-a-third-party-library-file"></a>타사 라이브러리 파일을 열 수 없습니다.

이 문제에 대 한 몇 가지 일반적인 원인은 다음과 같습니다.

- 라이브러리 파일의 경로가 잘못 되었거나 큰따옴표로 래핑되지 않을 수 있습니다. 또는 링커에 지정 하지 않았을 수 있습니다.

- 32 비트 버전의 라이브러리를 설치 했지만 64 비트 또는 그 밖의 다른 방법으로 빌드 하 고 있을 수 있습니다.

- 라이브러리에 설치 되지 않은 다른 라이브러리에 대 한 종속성이 있을 수 있습니다.

명령줄 빌드에 대 한 경로 문제를 해결 하려면 LIB 환경 변수가 설정 되어 있는지 확인 합니다. 이 파일에는 사용 하는 모든 라이브러리에 대 한 경로와 빌드하는 모든 구성에 대 한 경로가 포함 되어 있는지 확인 합니다. IDE에서 라이브러리 경로는 **VC + + 디렉터리**  >  **라이브러리 디렉터리** 속성에 의해 설정 됩니다. 작성 하는 모든 구성에 대해 필요한 라이브러리가 포함 된 모든 디렉터리가 여기에 나열 되는지 확인 합니다.

표준 라이브러리 디렉터리를 재정의 하는 라이브러리 디렉터리를 제공 해야 할 수도 있습니다. 명령줄에서 [/libpath](../../build/reference/libpath-additional-libpath.md) 옵션을 사용 합니다. IDE에서 프로젝트에 대 한 **구성 속성 > 링커 > 일반** 속성 페이지의 **추가 라이브러리 디렉터리** 속성을 사용 합니다.

작성 하는 구성에 필요한 라이브러리의 모든 버전을 설치 해야 합니다. [Vcpkg](../../build/vcpkg.md) 패키지 관리 유틸리티를 사용 하 여 여러 공용 라이브러리의 설치 및 설정을 자동화 하는 것이 좋습니다. 가능 하면 타사 라이브러리의 고유한 복사본을 빌드하는 것이 가장 좋습니다. 그런 다음 프로젝트와 동일한 구성에 맞게 빌드된 모든 라이브러리의 로컬 종속성이 있어야 합니다.

## <a name="cant-open-a-file-built-by-your-project"></a>프로젝트에서 빌드한 파일을 열 수 없습니다.

링커가이 파일에 액세스 하려고 할 때 *filename* 이 아직 없는 경우이 오류가 표시 될 수 있습니다. 한 프로젝트가 솔루션의 다른 프로젝트에 종속 된 경우에 발생할 수 있지만 프로젝트는 잘못 된 순서로 빌드됩니다. 이 문제를 해결 하려면 파일을 사용 하는 프로젝트에서 프로젝트 참조가 설정 되어 있는지 확인 합니다. 그런 다음 필요에 앞서 누락 된 파일을 작성 합니다. 자세한 내용은 [Visual Studio c + + 프로젝트에서 참조 추가](../../build/adding-references-in-visual-cpp-projects.md) 및 [프로젝트에서 참조 관리](/visualstudio/ide/managing-references-in-a-project)를 참조 하세요.

## <a name="cant-open-file-cprogramobj"></a>' C: \\ Program .obj ' 파일을 열 수 없습니다.

오류 메시지에 파일 이름 *C: \\ 프로그램인* 가 표시 되 면 라이브러리 경로를 큰따옴표로 래핑합니다. 이 오류는 *C: \\ Program Files* 로 시작 하는 래핑 되지 않은 경로가 링커에 전달 될 때 발생 합니다. 래핑 되지 않은 경로 에서도 비슷한 오류가 발생할 수 있습니다. 일반적으로 드라이브의 루트에 예기치 않은 .obj 파일이 표시 됩니다.

명령줄 빌드에 대해이 문제를 해결 하려면 [/libpath](../../build/reference/libpath-additional-libpath.md) 옵션 매개 변수를 확인 합니다. 또한 LIB 환경 변수에 지정 된 경로와 명령줄에 지정 된 경로를 확인 합니다. 공백을 포함 하는 경로 앞뒤에 큰따옴표를 사용 해야 합니다.

IDE에서이 문제를 해결 하려면 필요한 경우 프로젝트의 다음 속성에 큰따옴표를 추가 합니다.

- [구성 속성 > VC + + 디렉터리](../../build/reference/vcpp-directories-property-page.md) 속성 페이지의 **라이브러리 디렉터리** 속성 페이지

- **구성 속성 > 링커 > 일반** 속성 페이지의 **추가 라이브러리 디렉터리** 속성

- **구성 속성 > 링커 > 입력** 속성 페이지의 **추가 종속성** 속성입니다.

## <a name="other-common-issues"></a>기타 일반적인 이슈

### <a name="path-or-filename-issues"></a>경로 또는 파일 이름 문제

이 오류는 링커에 지정 된 라이브러리 파일 이름 또는 경로가 잘못 된 경우에 발생할 수 있습니다. 경로에 잘못 된 드라이브 사양이 있는 경우 또는입니다. 문제에 대 한 명령줄 또는 [#pragma 주석 (lib, "library_name")](../../preprocessor/comment-c-cpp.md) 지시어를 확인 합니다. 철자와 파일 확장명을 확인 하 고 파일이 지정 된 위치에 있는지 확인 합니다.

### <a name="parallel-build-synchronization"></a>병렬 빌드 동기화

병렬 빌드 옵션을 사용 하는 경우 Visual Studio에서 다른 스레드의 파일을 잠 궜을 수 있습니다. 이 문제를 해결 하려면 동일한 코드 개체 또는 라이브러리가 여러 프로젝트에서 빌드되지 않았는지 확인 합니다. 빌드 종속성 또는 프로젝트 참조를 사용 하 여 프로젝트에서 빌드된 이진 파일을 선택 합니다.

### <a name="additional-dependencies-specified-in-the-ide"></a>IDE에 지정 된 추가 종속성

**추가 종속성** 속성에서 개별 라이브러리를 직접 지정 하는 경우 공백을 사용 하 여 라이브러리 이름을 구분 합니다. 쉼표 또는 세미콜론을 사용 하지 마세요. **편집** 메뉴 항목을 사용 하 여 **추가 종속성** 대화 상자를 여는 경우 줄바꿈를 사용 하 여 쉼표, 세미콜론, 공백 등의 이름을 구분 합니다. **라이브러리 디렉터리** 및 **추가 라이브러리 디렉터리** 대화 상자에서 라이브러리 경로를 지정 하는 경우에도 줄바꿈를 사용 합니다.

### <a name="paths-that-are-too-long"></a>경로가 너무 깁니다.

*파일 이름* 에 대 한 경로가 260 자를 초과 하 여 확장 될 때이 오류가 표시 될 수 있습니다. 필요한 경우 디렉터리 구조를 다시 정렬 하거나 폴더 및 파일 이름을 짧게 줄여서 경로를 단축 합니다.

### <a name="files-that-are-too-large"></a>파일이 너무 큼

파일이 너무 커서이 오류가 발생할 수 있습니다. 라이브러리 또는 개체 파일 크기가 기가바이트 보다 많을 경우 32 비트 링커에 문제가 발생할 수 있습니다. 이 문제에 대 한 가능한 해결 방법은 64 비트 도구 집합을 사용 하는 것입니다. 명령줄에서 64 비트 도구 집합을 사용 하는 방법에 대 한 자세한 내용은 [방법: 명령줄에서 64 비트 Visual C++ 도구 집합](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)사용을 참조 하세요. IDE에서 64 비트 도구 집합을 사용 하는 방법에 대 한 자세한 내용은 [64 비트 컴파일러 및 도구와 함께 MSBuild 사용](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)을 참조 하세요. 또한 [Visual Studio를 사용 하 여 네이티브 amd64 도구 체인를 사용 하는 방법을](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)Stack Overflow 참조 하세요.

### <a name="incorrect-file-permissions"></a>파일 사용 권한이 잘못 되었습니다.

파일 *이름* 에 액세스할 수 있는 충분 한 파일 권한이 없는 경우이 오류가 발생할 수 있습니다. 일반 사용자 계정을 사용 하 여 보호 된 시스템 디렉터리의 라이브러리 파일에 액세스 하는 경우에 발생할 수 있습니다. 또는 원래 권한이 설정 된 다른 사용자의 파일을 복사 하는 경우에는를 사용 합니다. 이 문제를 해결 하려면 파일을 쓰기 가능한 프로젝트 디렉터리로 이동 합니다. 이동한 파일에 액세스할 수 있는 권한이 없는 경우 관리자 명령 창에서 takeown.exe 명령을 실행 하 여 파일의 소유권을 가져옵니다.

### <a name="insufficient-disk-space"></a>디스크 공간 부족

이 오류는 디스크 공간이 부족 한 경우에 발생할 수 있습니다. 링커는 여러 사례에서 임시 파일을 사용합니다. 충분 한 디스크 공간이 있는 경우에도 많은 링크를 사용 하 여 사용 가능한 디스크 공간을 확보 하거나 조각화 할 수 있습니다. [/Opt (최적화)](../../build/reference/opt-optimizations.md) 옵션을 사용 하는 것이 좋습니다. 전이적 COMDAT 제거를 수행 하면 모든 개체 파일이 여러 번 읽혀집니다.

### <a name="problems-in-the-tmp-environment-variable"></a>TMP 환경 변수의 문제

*파일 이름* 이름이 .lnk *nnn* 인 경우 링커에서 임시 파일에 대해 생성 된 파일 이름입니다. TMP 환경 변수에 지정 된 디렉터리가 없을 수 있습니다. 또는 TMP 환경 변수에 둘 이상의 디렉터리를 지정할 수 있습니다. TMP 환경 변수에는 디렉터리 경로를 하나만 지정 해야 합니다.

## <a name="help-my-issue-isnt-listed-here"></a>도움말은 여기에 나열 되지 않습니다.

여기에 나열 된 문제가 적용 되지 않는 경우 Visual Studio의 사용자 의견 도구를 사용 하 여 도움을 확인할 수 있습니다. IDE에서 메뉴 모음으로 이동 하 여 **도움말 > 사용자 의견 보내기 > 문제 보고** 를 선택 합니다. 또는 도움말 > 사용 하 여 제안을 제출 하 **> 제안을** 보냅니다. 질문 및 Visual Studio c + + [개발자 커뮤니티](https://aka.ms/vsfeedback/browsecpp) 웹 사이트에 대 한 [Microsoft Docs Q&사이트를](/answers/topics/c%2B%2B.html) 사용할 수도 있습니다. 이러한 사이트를 사용 하 여 질문에 대 한 답변을 검색 하 고 도움을 요청할 수 있습니다. 자세한 내용은 [Visual C++ 도구 집합 또는 설명서를 사용 하 여 문제를 보고 하는 방법](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)을 참조 하세요.

이 문서에 추가 해야 하는이 문제를 해결 하는 새로운 방법을 발견 했다면 알려주세요. 아래 단추를 사용 하 여 **이 페이지** 에 대 한 피드백을 보낼 수 있습니다. 이를 사용 하 여 [c + + 설명서 GitHub](https://github.com/MicrosoftDocs/cpp-docs/issues)리포지토리에서 새 문제를 만듭니다. 감사합니다.
