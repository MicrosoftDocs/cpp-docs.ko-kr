---
title: Visual Studio 버전의 C++ 도구 및 기능
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: c2ef6c539d5845beee044a963e0056d3287ba679
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924807"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>Visual Studio 버전의 C++ 도구 및 기능

::: moniker range=">=msvc-160"

다음 C++ 기능은 Visual Studio 2019에서 사용할 수 있습니다. 별도로 명시되지 않는 한 모든 기능은 모든 버전에서 사용할 수 있습니다. Visual Studio Community, Visual Studio Professional 및 Visual Studio Enterprise. 일부 기능에는 Visual Studio 설치 관리자를 사용하여 설치할 수 있는 특정 워크로드 또는 선택적 구성 요소가 필요합니다.

## <a name="platforms"></a>플랫폼

- Windows 바탕 화면
- 유니버설 Windows 플랫폼((태블릿, PC, Xbox, IoT 및 HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>컴파일러

- x86, x64, ARM 및 ARM64용 MSVC 32비트 컴파일러
- x86, x64, ARM 및 ARM64용 MSVC 64비트 컴파일러
- ARM용 GCC 크로스 컴파일러
- Clang/LLVM
  - Windows의 경우 x86 또는 x64를 대상으로 하는 Clang/LLVM 7.0(CMake 지원에만 해당). 다른 Clang 버전도 작동하지만 공식적으로 지원되지 않습니다.
  - Linux의 경우 배포판에서 지원되는 모든 Clang/LLVM 설치.

## <a name="c-workloads"></a>C++ 워크로드

Visual Studio에는 C++ 개발을 위한 다음과 같은 워크로드가 포함되어 있습니다. .NET 데스크톱 개발, Python 개발, Azure 개발, Visual Studio 확장 개발 등과 같은 다른 워크로드와 함께 이러한 워크로드 중 일부 또는 모두를 설치할 수 있습니다.

### <a name="desktop-development-with-c"></a>C++를 사용한 데스크톱 개발

Included:

- C++ 핵심 데스크톱 기능

선택적 구성 요소:

- MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.21)
- Windows 10 SDK(10.0.17763.0)
- Just-In-Time 디버거
- C++ 프로파일링 도구
- Windows용 C++ CMake 도구
- v142 빌드 도구용 C++ ATL(x86 및 x64)
- Test Adapter for Boost.Test
- Test Adapter for Google Test
- Live Share
- IntelliCode
- IntelliTrace(Enterprise만 해당)
- v142 빌드 도구용 C++ MFC(x86 및 x64)
- v142 빌드 도구용 C++/CLI 지원(14.21)
- v142 빌드 도구용 C++ 모듈(x64/x86 – 실험적)
- Windows용 Clang 컴파일러
- IncrediBuild - 빌드 가속화
- Windows 10 SDK(10.0.17134.0)
- Windows 10 SDK(10.0.16299.0)
- MSVC v141 – VS 2017 C++ x64/x86 빌드 도구(v14.16)
- MSVC v140 - VS 2015 C++ 빌드 도구(v14.00)

### <a name="linux-development-with-c"></a>C++를 사용한 Linux 개발

Included:

- C++ 핵심 기능
- Windows 유니버설 C 런타임
- Linux 개발용 C++

선택적 구성 요소:

- Linux용 C++ CMake 도구
- Embedded 및 IoT 개발 도구

### <a name="universal-windows-platform-development"></a>유니버설 Windows 플랫폼 개발

Included:

- Visual Studio용 Blend
- .NET 네이티브 및 .NET Standard
- NuGet 패키지 관리자
- 유니버설 Windows 플랫폼 도구
- Windows 10 SDK(10.0.17763.0)

선택적 구성 요소:

- IntelliCode
- IntelliTrace(Enterprise만 해당)
- USB 디바이스 연결
- C++(v142) 유니버설 Windows 플랫폼 도구
- C++(v141) 유니버설 Windows 플랫폼 도구
- DirectX용 그래픽 디버거 및 GPU 프로파일러
- Windows 10 SDK(10.0.18362.0)
- Windows 10 SDK(10.0.17134.0)
- Windows 10 SDK(10.0.16299.0)
- 아키텍처 및 분석 도구

### <a name="c-game-development"></a>C++ 게임 개발

Included:

- C++ 핵심 기능
- Windows 유니버설 C 런타임
- C++ 2019 재배포 가능 업데이트
- MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.21)

선택적 구성 요소:

- C++ 프로파일링 도구
- Windows 10 SDK(10.0.17763.0)
- IntelliCode
- IntelliTrace(Enterprise만 해당)
- Windows 10 SDK(10.0.17134.0)
- Windows 10 SDK(10.0.16299.0)
- IncrediBuild - 빌드 가속화
- Cocos
- 언리얼 엔진 설치 관리자
- Unreal 엔진용 Android IDE 지원

### <a name="mobile-development-with-c"></a>C++를 사용한 모바일 개발

Included:

- C++ 핵심 기능
- Android SDK 설치(API 레벨 25)(C++를 통해 모바일 개발을 할 수 있도록 로컬 설치)

선택적 구성 요소:

- Android NDK(R16B)
- Apache Ant(1.9.3)
- C++ Android 개발 도구
- IntelliCode
- Google Android 에뮬레이터(API 레벨 25)(로컬 설치)
- Intel HAXM(Hardware Accelerated Execution Manager)(로컬 설치)
- Android NDK(R16B)(32비트)
- C++ iOS 개발 도구
- IncrediBuild - 빌드 가속화

## <a name="individual-components"></a>개별 구성 요소

이러한 구성 요소는 모든 워크로드와 독립적으로 설치할 수 있습니다.

- JavaScript 진단
- Live Share
- v142 빌드 도구용 C++ 유니버설 Windows 플랫폼 런타임
- ClickOnce 게시 도구
- Microsoft Visual Studio 설치 관리자 프로젝트

## <a name="libraries-and-headers"></a>라이브러리 및 헤더

- Windows 헤더 및 라이브러리
- Windows 유니버설 C 런타임(CRT)
- C++ 표준 라이브러리
- ATL
- MFC
- .NET Framework 클래스 라이브러리
- .NET용 C++ 지원 라이브러리
- OpenMP 2.0
- Vcpkg 카탈로그를 통한 900개가 넘는 오픈 소스 라이브러리

## <a name="build-and-project-systems"></a>빌드 및 프로젝트 시스템

- CMake
- 폴더 열기를 통한 모든 빌드 시스템
- 명령줄 빌드(msbuild.exe)
- 네이티브 다중 대상 지정
- 관리되는 다중 대상 지정
- 병렬 빌드
- 빌드 사용자 지정
- 속성 페이지 확장성

## <a name="project-templates"></a>프로젝트 템플릿

설치한 워크로드에 따라 다음 프로젝트 템플릿을 사용할 수 있습니다.

Windows 데스크톱:

- 빈 프로젝트
- 콘솔 앱
- Windows 데스크톱 마법사
- Windows 데스크톱 애플리케이션
- 공유 항목 프로젝트
- MFC 앱
- 동적 연결 라이브러리
- CLR 빈 프로젝트
- CLR 콘솔 앱
- 정적 라이브러리
- CMake 프로젝트
- ATL 프로젝트
- MFC 동적 연결 라이브러리
- CLR 클래스 라이브러리
- 메이크파일 프로젝트(Windows)
- MFC ActiveXControl
- 기본 단위 테스트 프로젝트
- Google Test

유니버설 Windows 플랫폼(C++/CX):

- 새 응용 프로그램
- DirectX 11 및 XAML 앱
- DirectX 11 앱
- DirectX 12 앱
- 단위 테스트 앱
- DLL
- Windows 런타임 구성 요소
- 정적 라이브러리
- Windows 애플리케이션 패키징 프로젝트

Linux:

- 콘솔 앱(Linux)
- 빈 프로젝트(Linux)
- Raspberry Pi Blink
- 메이크파일 프로젝트(Linux)

## <a name="tools"></a>도구

- Incremental Linker(Link.exe)
- Microsoft 메이크파일 Utility(Nmake.exe)
- Lib Generator(Lib.exe)
- Windows Resource Compiler(Rc.exe)
- Windows Resource to Object Converter(CvtRes.exe)
- Browse Information Maintenance Utility(BscMake.exe)
- C++ Name Undecorator(Undname.exe)
- COFF/PE Dumper(Dumpbin.exe)
- COFF/PE Editor(Editbin.exe)
- MASM(Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- 유추 규칙
- 프로필 기반 최적화

## <a name="debugging-features"></a>디버깅 기능

- 네이티브 디버깅
- natvis(네이티브 형식 시각화)
- 그래픽 디버깅
- 관리 디버깅
- GPU 사용량
- 메모리 사용량
- Remote Debugging
- SQL 디버깅
- 정적 코드 분석

## <a name="designers-and-editors"></a>디자이너 및 편집기

- XAML 디자이너
- CSS 스타일 디자이너/편집기
- HTML 디자이너/편집기
- XML 편집기
- 소스 코드 편집기
- 생산성 기능: 리팩터링, EDG IntelliSense 엔진, C++ 코드 서식 지정
- Windows Forms 디자이너
- 데이터 디자이너
- 네이티브 리소스 편집기(.rc 파일)
- 리소스 편집기
- 모델 편집기
- 셰이더 디자이너
- 실시간 종속성 유효성 검사(Enterprise만 해당)
- 아키텍처 계층 다이어그램(Enterprise만 해당)
- 아키텍처 유효성 검사(Enterprise만 해당)
- 코드 복제본(Enterprise만 해당)

## <a name="data-features"></a>데이터 기능

- 데이터 디자이너
- 데이터 개체
- 웹 서비스
- 서버 탐색기

## <a name="automation-and-extensibility"></a>자동화 및 확장성

- 확장성 개체 모델
- 코드 모델
- 프로젝트 모델
- 리소스 편집기 모델
- 마법사 모델
- 디버거 개체 모델

## <a name="application-lifecycle-management-tools"></a>Application Lifecycle Management 도구

- 단위 테스트(Microsoft 네이티브 C++, Boost.Test, Google Test, CTest)
- 코드 맵 및 종속성 그래프(Professional 및 Enterprise)
- 코드 검사(Enterprise만 해당)
- 수동 테스트(Enterprise만 해당)
- 예비 테스트(Enterprise만 해당)
- 테스트 사례 관리(Enterprise만 해당)
- 코드 맵 디버거 통합(Enterprise만 해당)
- Live Unit Testing(Enterprise만 해당)
- IntelliTrace(Enterprise만 해당)
- IntelliTest(Enterprise만 해당)
- Microsoft Fakes(단위 테스트 격리)(Enterprise만 해당)
- 코드 검사(Enterprise만 해당)

## <a name="see-also"></a>참조

[Visual Studio 설치](/visualstudio/install/install-visual-studio)<br/>
[Visual Studio의 새로운 기능](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Visual Studio의 C++ 프로젝트 형식](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=msvc-150"

다음 표에는 Visual Studio 2017에서 사용할 수 있는 Visual C++ 기능이 나와 있습니다. 셀에 X가 있으면 해당 기능을 사용할 수 있음을 나타내고, 셀이 비어 있으면 해당 기능을 사용할 수 없음을 나타냅니다. 괄호 안의 참고 사항은 해당 기능을 사용할 수 있지만 제한됨을 나타냅니다.

## <a name="platforms"></a>플랫폼

|플랫폼|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|-|-|-|-|-|
|Windows 바탕 화면||X|X|X|
|범용 Windows 플랫폼(휴대폰, 태블릿, PC, Xbox, IoT 및 HoloLens)|X||X|X|
|Linux|X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>컴파일러

|컴파일러|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|MSVC 32비트 X86 컴파일러|X|X|X|X|
|X86_arm 크로스 컴파일러|X||X|X|
|MSVC 64비트 x64 컴파일러|||X|X|
|X86_ x64 크로스 컴파일러|X|X|X|X|

## <a name="libraries-and-headers"></a>라이브러리 및 헤더

|라이브러리 또는 헤더|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Windows 헤더, 라이브러리 및 CRT 라이브러리|(X)|X|X|X|
|C++ 표준 라이브러리|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|.NET Framework 클래스 라이브러리||X|X|X|
|.NET용 C++ 지원 라이브러리||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>프로젝트 템플릿

|템플릿|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|UWP, Windows 8.1, Windows Phone 8.0용 XAML 템플릿|X||X|X|
|Direct3D 응용 프로그램|X||X|X|
|DLL(유니버설 Windows)|X||X|X|
|정적 라이브러리(유니버설 Windows)|X||X|X|
|Windows 런타임 구성 요소|X||X|X|
|단위 테스트 앱(유니버설 Windows)|X||X|X|
|ATL 프로젝트|||X|X|
|클래스 라이브러리(CLR)||X|X|X|
|CLR 콘솔 애플리케이션||X|X|X|
|CLR 빈 프로젝트||X|X|X|
|사용자 지정 마법사|||X|X|
|빈 프로젝트||X|X|X|
|메이크파일 프로젝트||X|X|X|
|MFC ActiveX 컨트롤|||X|X|
|MFC 애플리케이션|||X|X|
|MFC DLL|||X|X|
|테스트 프로젝트|X|X|X|X|
|Win32 콘솔 애플리케이션||X|X|X|
|Win32 프로젝트||X|X|X|

## <a name="tools"></a>도구

|도구|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Incremental Linker(Link.exe)|X|X|X|X|
|Program Maintenance Utility(Nmake.exe)||X|X|X|
|Lib Generator(Lib.exe)|X|X|X|X|
|Windows Resource Compiler(Rc.exe)|X|X|X|X|
|Windows Resource to Object Converter(CvtRes.exe)||X|X|X|
|Browse Information Maintenance Utility(BscMake.exe)|X|X|X|X|
|C++ Name Undecorator(Undname.exe)|X|X|X|X|
|COFF/PE Dumper(Dumpbin.exe)|X|X|X|X|
|COFF/PE Editor(Editbin.exe)|X|X|X|X|
|MASM(Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|유추 규칙|||X|X|
|MSBuild에 VCBuild.vcproj 프로젝트 업그레이드(VCUpgrade.exe)|X|X|X|X|
|프로필 기반 최적화|||X|X|

## <a name="debugging-features"></a>디버깅 기능

|디버깅 기능|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|네이티브 디버깅|X|X|X|X|
|natvis(네이티브 형식 시각화)|X|X|X|X|
|그래픽 디버깅|X||X|X|
|관리 디버깅||X|X|X|
|GPU 사용량|X||X|X|
|메모리 사용량|X||X|X|
|Remote Debugging|X|X|X|X|
|SQL 디버깅|||X|X|
|정적 코드 분석|제한됨|제한됨|X|X|

## <a name="designers-and-editors"></a>디자이너 및 편집기

|디자이너 또는 편집기|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML 디자이너|X||X|X|
|CSS 스타일 디자이너/편집기|X|X|X|X|
|HTML 디자이너/편집기|X|X|X|X|
|XML 편집기|X|X|X|X|
|소스 코드 편집기|X|X|X|X|
|생산성 기능: 리팩터링, IntelliSense, C++ 코드 서식 지정|X|X|X|X|
|Windows Forms 디자이너||X|X|X|
|데이터 디자이너|||X|X|
|네이티브 리소스 편집기(.rc 파일)|||X|X|
|리소스 편집기|X|X|X|X|
|모델 편집기|X||X|X|
|셰이더 디자이너|X||X|X|

## <a name="data-features"></a>데이터 기능

|데이터 기능|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|데이터 디자이너|||X|X|
|데이터 개체|||X|X|
|웹 서비스|||X|X|
|서버 탐색기|||X|X|

## <a name="build-and-project-systems"></a>빌드 및 프로젝트 시스템

|빌드 또는 프로젝트 기능|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|명령줄 빌드(msbuild.exe)|X|X|X|X|
|네이티브 다중 대상 지정||X|X|X|
|관리되는 다중 대상 지정||X|X|X|
|병렬 빌드|X|X|X|X|
|빌드 사용자 지정|X|X|X|X|
|속성 페이지 확장성|X|X|X|X|

## <a name="automation-and-extensibility"></a>자동화 및 확장성

|자동화 및 확장성|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|확장성 개체 모델|||X|X|
|코드 모델|||X|X|
|프로젝트 모델|||X|X|
|리소스 편집기 모델|||X|X|
|마법사 모델|||X|X|
|디버거 개체 모델|||X|X|

## <a name="application-lifecycle-management-tools"></a>Application Lifecycle Management 도구

|도구|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-|-|-|-|-|
|유닛 테스트(네이티브 프레임워크)|X|X|X|X|
|유닛 테스트(관리되는 프레임워크)||X|X|X|
|코드 검사||||X|
|수동 테스트||||X|
|예비 테스트||||X|
|테스트 사례 관리||||X|
|코드 맵 및 종속성 그래프|||읽기 전용|X|
|코드 맵 디버깅||||X|

## <a name="see-also"></a>참조

[Visual Studio 설치](/visualstudio/install/install-visual-studio)<br/>
[Visual Studio의 새로운 기능](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Visual Studio의 C++ 프로젝트 형식](../build/reference/visual-cpp-project-types.md)

::: moniker-end
