---
description: '자세히 알아보기: Clang 프로젝트 속성 (Android c + +)'
title: Clang 프로젝트 속성(Android C++)
ms.date: 10/23/2017
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- VC.Project.VCClangCompilerTool.AdditionalOptionsPage
ms.openlocfilehash: 5f98181ddcbd47e97333a796843e81b50e6d5276
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319289"
---
# <a name="clang-project-properties-android-c"></a>Clang 프로젝트 속성(Android C++)

| 속성 | 설명 | 선택 사항 |
|--|--|--|
| 추가 포함 디렉터리 | 포함 경로에 추가할 디렉터리를 하나 이상 지정합니다. 항목이 여러 개인 경우 세미콜론으로 구분합니다. (-I *경로*). |
| 디버그 정보 형식 | 컴파일러에서 생성되는 디버깅 정보 형식을 지정합니다. | **없음** - 디버깅 정보를 생성하지 않으므로 컴파일이 더 빨라질 수 있습니다.<br>**전체 디버그 정보(DWARF2)** - DWARF2 디버그 정보를 생성합니다.<br>**줄 번호 정보** - 줄 번호 정보만 생성합니다.<br> |
| 개체 파일 이름 | 기본 개체 파일 이름을 재정의할 이름을 지정합니다. 파일 또는 디렉터리 이름일 수 있습니다. (/Fo *이름*). |
| 경고 수준 | 컴파일러가 코드 오류를 처리하는 수준을 선택합니다.  다른 플래그는 추가 옵션에 직접 추가해야 합니다. (/w, /Weverything) | **모든 경고 해제** - 모든 컴파일러 경고를 사용하지 않도록 설정합니다.<br>**Enableallwarnings** -기본적으로 사용 하지 않도록 설정 된 모든 경고를 사용 하도록 설정 합니다.<br> |
| 경고를 오류로 처리 | 모든 컴파일러 경고를 오류로 처리합니다. 새 프로젝트인 경우 모든 컴파일에서/WX를 사용하는 것이 좋습니다. 모든 경고를 해결하면 찾기 어려운 코드 오류를 최소화할 수 있습니다. |
| 자세한 정보 표시 모드 사용 | 실행할 명령을 표시하고 자세한 정보 표시 출력을 사용합니다. |
| Optimization | 애플리케이션의 최적화 수준을 지정합니다. | **사용자 지정** - 사용자 지정 최적화입니다.<br>**사용 안 함** - 최적화를 사용하지 않습니다.<br>**크기 최소화** - 크기에 맞게 최적화합니다.<br>**속도 최대화** - 속도에 맞게 최적화합니다.<br>**전체 최적화** - 고가의 최적화입니다.<br> |
| 엄격한 앨리어싱 | 가장 엄격한 앨리어싱 규칙을 가정합니다.  한 형식의 개체는 다른 형식 개체와 동일한 주소에 있는 것으로 간주 되지 않습니다. |
| 프레임 포인터 생략 | 호출 스택에서 프레임 포인터를 생성하지 않습니다. |
| C++ 예외 사용 | 컴파일러가 사용하는 예외 처리 모델을 지정합니다. | **아니요** - 예외 처리를 사용하지 않도록 설정합니다.<br>**예** - 예외 처리를 사용하도록 설정합니다.<br>**해제 테이블** -필요한 정적 데이터를 생성 하지만 생성 된 코드에는 영향을 주지 않습니다.<br> |
| 함수 수준 링크 사용 | 컴파일러가 개별 함수를 패키지된 함수(COMDAT)의 형태로 패키지할 수 있게 합니다. 편집에 필요하며 계속 작동합니다.     (ffunction-sections) |
| 데이터 수준 연결 사용 | 링커 최적화를 사용하면 별도 섹션에서 각 데이터 항목을 내보내 사용하지 않은 데이터를 제거할 수 있습니다. |
| 고급 SIMD 사용(Neon) | NEON 부동 소수점 하드웨어에 대한 코드 생성을 사용하도록 설정합니다. ARM 아키텍처에만 적용 됩니다. |
| 부동 소수점 ABI | 부동 소수점 ABI를 선택할 수 있는 선택 옵션입니다. | **소프트** - '소프트'는 컴파일러가 부동 소수점 연산에 대한 라이브러리 호출이 포함된 출력을 생성하도록 합니다.<br>**SoftFP** - 'SoftFP'는 하드웨어 부동 소수점 명령을 사용하는 코드의 생성을 허용하지만 soft-float 호출 규칙을 계속 사용합니다.<br>**하드** - ‘하드’는 부동 소수점 명령의 생성을 허용하고 FPU 관련 호출 규칙을 사용합니다.<br> |
| 보안 검사 | 보안 검사를 통해 스택 버퍼 오버런, 프로그램의 보안에 대해 일반적으로 시도되는 공격을 검색할 수 있습니다. (fstack-protector) | **보안 검사 사용 안 함** - 보안 검사를 사용하지 않도록 설정합니다.<br>**보안 검사 사용** - 보안 검사를 사용하도록 설정합니다. (fstack-protector)<br> |
| 위치 독립적 코드 | 공유 라이브러리에서 사용할 PIC (위치 독립적 코드)를 생성 합니다. |
| 짧은 열거형 사용 | 열거형 형식은 가능한 값의 입력 집합에 필요한 만큼의 바이트만 사용합니다. |
| 런타임 형식 정보 사용 | 런타임에 C++ 개체의 형식(런타임 형식 정보)을 검사하는 코드를 추가합니다.     (frtti, fno-rtti) |
| C 언어 표준 | C 언어 표준을 결정합니다. | **기본**<br>**C89** - C89 언어 표준입니다.<br>**C99** - C99 언어 표준입니다.<br>**C11** - C11 언어 표준입니다.<br>**C99(GNU 언어)** - C99(GNU 언어) 언어 표준입니다.<br>**C11(GNU 언어)** - C11(GNU 언어) 언어 표준입니다.<br> |
| C++ 언어 표준 | C++ 언어 표준을 결정합니다. | **기본값**<br>**C++03** - C++03 언어 표준입니다.<br>**C++11** - C++11 언어 표준입니다.<br>**C++14** - C++14 언어 표준입니다.<br>**C++03(GNU 언어)** - C++03(GNU 언어) 언어 표준입니다.<br>**C++11(GNU 언어)** - C++11(GNU 언어) 언어 표준입니다.<br>**C++14(GNU 언어)** - C++14(GNU 언어) 언어 표준입니다.<br> |
| 전처리기 정의 | 소스 파일에 대한 전처리 기호를 정의합니다. (-D) |
| 전처리기 정의 해제 | 전처리기에 대 한 추가 해제를 하나 이상 지정 합니다.  (-U *매크로*) |
| 모든 전처리기 정의 해제 | 이전에 정의한 모든 전처리기 값을 정의 해제합니다.  (-undef) |
| 포함 표시 | 컴파일러 출력으로 포함 파일 목록을 생성합니다.  (-H) |
| 미리 컴파일된 헤더 | 미리 컴파일된 헤더 만들기/사용: 빌드하는 동안 미리 컴파일된 헤더를 만들거나 사용 하도록 설정 합니다. | **사용** - 미리 컴파일된 헤더를 사용합니다.<br>**미리 컴파일된 헤더 사용 안 함** - 미리 컴파일된 헤더를 사용하지 않습니다.<br> |
| 미리 컴파일된 헤더 파일 | 미리 컴파일된 헤더 파일에 사용할 헤더 파일 이름을 지정합니다. 이 파일은 빌드하는 동안 ' 강제 포함 파일 '에도 추가 됩니다. |
| 미리 컴파일된 헤더 출력 파일 디렉터리 | 생성된 미리 컴파일된 헤더에 대한 디렉터리를 지정합니다. 이 디렉터리는 빌드하는 동안 ' 추가 포함 디렉터리 '에도 추가 됩니다. |
| 미리 컴파일된 헤더를 다음으로 컴파일 | 미리 컴파일된 헤더 파일에 대한 컴파일 언어 옵션(-x c-header, -x c++-header)을 선택합니다. | **C 코드로 컴파일** -c 코드로 컴파일합니다.<br>**C + + 코드로 컴파일** -c + + 코드로 컴파일합니다.<br> |
| 다음으로 컴파일 | 및 파일에 대 한 컴파일 언어 옵션을 선택 *`.c`* *`.cpp`* 합니다.  ' 기본값 '은 또는 확장을 기준으로 검색 됩니다 *`.c`* *`.cpp`* . (-x c, -x c++) | **기본값** - 기본값입니다.<br>**C 코드로 컴파일** -c 코드로 컴파일합니다.<br>**C + + 코드로 컴파일** -c + + 코드로 컴파일합니다.<br> |
| 강제 포함 파일 | 하나 이상의 강제 포함 파일입니다.     (-include *이름*) |
| 다중 프로세서 컴파일 | 다중 프로세서 컴파일입니다. |
| 추가 옵션 | 추가 옵션입니다. |
