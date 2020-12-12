---
description: '자세한 정보: MIDL 속성 페이지'
title: MIDL 컴파일러 속성 페이지
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: 12cc0791bfadf7611d62ab16fc788081f4c7b7e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137828"
---
# <a name="midl-property-pages"></a>MIDL 속성 페이지

MIDL 속성 페이지는에서 항목 속성으로 사용할 수 있습니다. COM을 사용 하는 c + + 프로젝트의 IDL 파일입니다. [MIDL 컴파일러](/windows/win32/midl/using-the-midl-compiler-2)를 구성 하는 데 사용 합니다. C++ 프로젝트의 MIDL 옵션에 프로그래밍 방식으로 액세스하는 방법에 대한 자세한 내용은 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> 개체를 참조하세요. 또한 [일반 MIDL 명령줄 구문](/windows/win32/midl/general-midl-command-line-syntax)을 참조 하세요.

## <a name="general-property-page"></a>일반 속성 페이지

### <a name="preprocessor-definitions"></a>전처리기 정의

MIDL 매크로 ([/d](/windows/win32/midl/-d)) 매크로를 포함 한 하나 이상의 정의를 지정 합니다 \[ \] .

### <a name="additional-include-directories"></a>추가 포함 디렉터리

포함 경로 ([/i](/windows/win32/midl/-i)경로)에 추가할 하나 이상의 디렉터리를 지정 합니다 \[ \] .

### <a name="additional-metadata-directories"></a>추가 메타 데이터 디렉터리

Windows ([/metadata_dir](/windows/win32/midl/-metadata-dir) 경로) 파일을 포함 하는 디렉터리를 지정 \[ \] 합니다.

### <a name="enable-windows-runtime"></a>Windows 런타임 사용

Windows 런타임 의미 체계를 사용 하 여 Windows 메타 데이터 파일 ([/winrt](/windows/win32/midl/-winrt))을 만듭니다.

### <a name="ignore-standard-include-path"></a>표준 포함 경로 무시

현재 및 포함 디렉터리 ([/no_def_idir](/windows/win32/midl/-no-def-idir))를 무시 합니다.

### <a name="mktyplib-compatible"></a>MkTypLib 호환

mktyplib.exe 버전 2.03 ([/mktyplib203](/windows/win32/midl/-mktyplib203))과의 호환성을 강제 적용 합니다.

### <a name="warning-level"></a>경고 수준

MIDL 코드 오류 ([/w](/windows/win32/midl/-w))의 엄격 성을를 선택 합니다.

**Choices**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>경고를 오류로 처리

MIDL에서 모든 경고를 오류 ([/wx](/windows/win32/midl/-wx))로 처리할 수 있습니다.

### <a name="suppress-startup-banner"></a>시작 배너 표시 안 함

시작 배너 및 정보 메시지 ([/nologo](/windows/win32/midl/-nologo))를 표시 하지 않습니다.

### <a name="c-compiler-char-type"></a>C 컴파일러 Char 형식

생성 된 코드를 컴파일하는 데 사용 되는 C 컴파일러의 기본 문자 형식을 지정 합니다. ([/문자](/windows/win32/midl/-char) signed | unsigned | ascii7).

**Choices**

- **서명** 된 서명
- **Unsigned** -unsigned
- **Ascii** -ascii

### <a name="target-environment"></a>대상 환경

대상으로 지정할 환경을 지정 합니다 ([/env](/windows/win32/midl/-env) arm32 | win32 | ia64 | x64).

**Choices**

- **설정 안 함** -Win32
- **Microsoft Windows 32 비트** -Win32
- **Itanium의 Microsoft Windows 64 비트** -IA64
- **Microsoft WINDOWS arm** -arm
- **Microsoft WINDOWS ARM64** -ARM64
- **Microsoft Windows 64** 비트 (x64-x64)

### <a name="generate-stubless-proxies"></a>스텁 없는 프록시 생성

개체 인터페이스 ([/Oicf](/windows/win32/midl/-oi), [/oicf](/windows/win32/midl/-oi) )에 대해 확장 및 스텁 없는 프록시로 완전히 해석 된 스텁을 생성 합니다.

### <a name="suppress-compiler-warnings"></a>컴파일러 경고 표시 안 함

컴파일러 경고 메시지 ([/no_warn](/windows/win32/midl/-no-warn))를 표시 하지 않습니다.

### <a name="application-configuration-mode"></a>응용 프로그램 구성 모드

IDL 파일에서 선택한 ACF 특성을 허용 합니다 ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>로케일 ID

입력 파일의 LCID, 파일 이름 및 디렉터리 경로 ([/Lcid](/windows/win32/midl/-lcid) DECIMAL)를 지정 합니다.

### <a name="multi-processor-compilation"></a>다중 프로세서 컴파일

동시에 여러 인스턴스를 실행 합니다.

## <a name="output-property-page"></a>출력 속성 페이지

### <a name="output-directory"></a>출력 디렉터리

출력 디렉터리 ([/out](/windows/win32/midl/-out) [directory])를 지정 합니다.

### <a name="metadata-file"></a>메타 데이터 파일

생성 된 메타 데이터 파일의 이름을 지정 합니다 ([/sinfilename](/windows/win32/midl/-winmd) ).

### <a name="header-file"></a>헤더 파일

생성 된 헤더 파일 ([/h](/windows/win32/midl/-h) filename)의 이름을 지정 합니다.

### <a name="dlldata-file"></a>Dlldata.c 파일

DLLDATA.C 파일 ([/dlldata](/windows/win32/midl/-dlldata) filename)의 이름을 지정 합니다.

### <a name="iid-file"></a>IID 파일

인터페이스 식별자 파일 ([/iid](/windows/win32/midl/-iid) 파일 이름)의 이름을 지정 합니다.

### <a name="proxy-file"></a>프록시 파일

프록시 파일의 이름을 지정 합니다 ([/sproxy](/windows/win32/midl/-proxy) 파일 이름).

### <a name="generate-type-library"></a>형식 라이브러리 생성

형식 라이브러리를 생성 하지 않도록 지정 합니다 (no).

### <a name="type-library"></a>형식 라이브러리

형식 라이브러리 파일 ([/tlb](/windows/win32/midl/-tlb) filename)의 이름을 지정 합니다.

### <a name="generate-client-stub-files"></a>클라이언트 스텁 파일 생성

클라이언트 스텁 파일만 생성 합니다 ([/client](/windows/win32/midl/-client) [stub | none]).

**Choices**

- **스텁** 스텁
- **없음** -없음

### <a name="generate-server-stub-files"></a>서버 스텁 파일 생성

서버 스텁 파일만 생성 합니다 ([/server](/windows/win32/midl/-server) [stub | none]).

**Choices**

- **스텁** 스텁
- **없음** -없음

### <a name="client-stub-file"></a>클라이언트 스텁 파일

클라이언트 스텁 파일 ([/cstub](/windows/win32/midl/-cstub) [file])을 지정 합니다.

### <a name="server-stub-file"></a>서버 스텁 파일

서버 스텁 파일 ([/sstub](/windows/win32/midl/-sstub) [file])을 지정 합니다.

### <a name="type-library-format"></a>형식 라이브러리 형식

형식 라이브러리 파일 형식을 지정 합니다 ([/old.tlb |/stts]).

**Choices**

- **Newformat** -새 형식
- **Oldformat** -이전 형식

## <a name="advanced-property-page"></a>고급 속성 페이지

### <a name="c-preprocess-options"></a>C 전처리 옵션

C 컴파일러 전처리기 ([/cpp_opt](/windows/win32/midl/-cpp-opt) 스위치)에 전달할 스위치를 지정 합니다.

### <a name="undefine-preprocessor-definitions"></a>전처리기 정의 해제

MIDL 매크로 ([/u](/windows/win32/midl/-U)  [macros])를 포함 하 여 하나 이상의 추가 정보를 지정 합니다.

### <a name="enable-error-checking"></a>오류 검사 사용

오류 검사 옵션 ([/오류 모두 | 없음])을 선택 합니다.

**Choices**

- **EnableCustom** -모두
- **모두** -모두
- **없음** -없음

### <a name="check-allocations"></a>할당 확인

메모리 부족 오류 ([/오류](/windows/win32/midl/-error) 할당)를 확인 합니다.

### <a name="check-bounds"></a>범위 확인

크기 vs 전송 길이 사양 확인 ([/error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>열거형 범위 검사

열거 값이 허용 되는 범위 ([/error](/windows/win32/midl/-error) enum)에 있는지 확인 합니다.

### <a name="check-reference-pointers"></a>참조 포인터 확인

참조 포인터를 null이 아닌 것으로 확인 합니다 ([/error](/windows/win32/midl/-error) ref).

### <a name="check-stub-data"></a>스텁 데이터 검사

서버 쪽 스텁 데이터 유효성에 대 한 추가 검사를 내보냅니다 ([/오류](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>' ABI ' 네임 스페이스 앞에 추가

' ABI ' 네임 스페이스를 모든 형식에 추가 합니다.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>매개 변수 유효성 검사

매개 변수의 유효성을 검사 하는 추가 정보를 생성 합니다 ([/robust](/windows/win32/midl/-robust)  |  [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>구조체 멤버 맞춤

대상 시스템 (/ZpN)에서 구조의 압축 수준을 지정 합니다.

**Choices**

- **설정** 안 함-설정 안 함
- **1 바이트** -Zp1
- **2 바이트** -Zp2
- **4 바이트** -Zp4
- **8 바이트** -Zp8

### <a name="redirect-output"></a>출력 리디렉션

출력을 화면에서 파일로 리디렉션합니다 ([/o](/windows/win32/midl/-o) 파일).

### <a name="minimum-target-system"></a>최소 대상 시스템

최소 대상 시스템 ([/Target](/windows/win32/midl/-target) 문자열)을 설정 합니다.
