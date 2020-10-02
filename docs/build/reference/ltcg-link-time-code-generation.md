---
title: /LTCG(링크 타임 코드 생성)
description: MSVC 링커 옵션/LTCG는 전체 프로그램 최적화에 대 한 링크 타임 코드 생성을 사용 하도록 설정 합니다.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: 6c0009e5236f33119ed411dc81ce6a4385f21a2a
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662270"
---
# <a name="ltcg-link-time-code-generation"></a>`/LTCG` (링크 타임 코드 생성)

를 사용 **`/LTCG`** 하 여 전체 프로그램 최적화를 수행 하거나, PGO (프로필 기반 최적화) 계측을 만들고, 학습을 수행 하 고, 프로필 기반 최적화 빌드를 만듭니다.

## <a name="syntax"></a>Syntax

> **`/LTCG`**[**`:`**{**`INCREMENTAL`**|**`NOSTATUS`**|**`STATUS`**|**`OFF`**}]

이 옵션은 Visual Studio 2015부터 더 이상 사용되지 않습니다.

> **`/LTCG:`**{**`PGINSTRUMENT`**|**`PGOPTIMIZE`**|**`PGUPDATE`**}

### <a name="arguments"></a>인수

**`INCREMENTAL`**<br/>
필드 링커가 전체 프로젝트 대신 편집의 영향을 받는 파일에만 전체 프로그램 최적화 또는 LTCG (링크 타임 코드 생성)를 적용 하도록 지정 합니다. 기본적으로를 지정 하면이 플래그가 설정 되지 **`/LTCG`** 않으며 전체 프로그램 최적화를 사용 하 여 전체 프로젝트가 연결 됩니다.

**`NOSTATUS`** &#124; **`STATUS`**<br/>
(선택 사항) 완료된 링크 비율을 표시하는 진행률 표시기가 링커에 표시되는지 여부를 지정합니다. 기본적으로이 상태 정보는 표시 되지 않습니다.

**`OFF`**<br/>
(선택 사항) 링크 시간 코드 생성을 사용하지 않습니다. 이 동작은 **`/LTCG`** 명령줄에서가 지정 되지 않은 경우와 동일 합니다.

**`PGINSTRUMENT`**<br/>
(선택 사항) 이 옵션은 Visual Studio 2015부터 더 이상 사용되지 않습니다. 대신, **`/LTCG`** [ `/GENPROFILE` `/FASTGENPROFILE` 또는](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 를 사용 하 여 프로필 기반 최적화를 위해 계측 된 빌드를 생성 합니다. 계측된 실행으로부터 수집되는 데이터는 최적화된 이미지를 만드는 데 사용됩니다. 자세한 내용은 [프로필 기반 최적화](../profile-guided-optimizations.md)를 참조하세요. 이 옵션의 약식 형태는 **`/LTCG:PGI`** 입니다.

**`PGOPTIMIZE`**<br/>
(선택 사항) 이 옵션은 Visual Studio 2015부터 더 이상 사용되지 않습니다. 대신 및를 **`/LTCG`** 사용  [`/USEPROFILE`](useprofile.md) 하 여 최적화 된 이미지를 작성 합니다. 자세한 내용은 [프로필 기반 최적화](../profile-guided-optimizations.md)를 참조하세요. 이 옵션의 약식 형태는 **`/LTCG:PGO`** 입니다.

**`PGUPDATE`**<br/>
(선택 사항) 이 옵션은 Visual Studio 2015부터 더 이상 사용되지 않습니다. 대신 및를 **`/LTCG`** 사용  **`/USEPROFILE`** 하 여 최적화 된 이미지를 다시 빌드합니다. 자세한 내용은 [프로필 기반 최적화](../profile-guided-optimizations.md)를 참조하세요. 이 옵션의 약식 형태는 **`/LTCG:PGU`** 입니다.

## <a name="remarks"></a>설명

**`/LTCG`** 옵션은 컴파일러를 호출 하 고 전체 프로그램 최적화를 수행 하도록 링커에 지시 합니다. 프로필 기반 최적화를 수행할 수도 있습니다. 자세한 내용은 [프로필 기반 최적화](../profile-guided-optimizations.md)를 참조하세요.

다음 예외를 제외 하 고 **`/LTCG`** **`/USEPROFILE`** 및 옵션의 이전 pgo 초기화 조합에서 지정 하지 않은 및의 pgo 조합에 링커 옵션을 추가할 수 없습니다 **`/LTCG`** **`/GENPROFILE`** .

- [`/BASE`](base-base-address.md)

- [`/FIXED`](fixed-fixed-base-address.md)

- **`/LTCG`**

- [`/MAP`](map-generate-mapfile.md)

- [`/MAPINFO`](mapinfo-include-information-in-mapfile.md)

- [`/NOLOGO`](nologo-suppress-startup-banner-linker.md)

- [`/OUT`](out-output-file-name.md)

- [`/PGD`](pgd-specify-database-for-profile-guided-optimizations.md)

- [`/PDB`](pdb-use-program-database.md)

- [`/PDBSTRIPPED`](pdbstripped-strip-private-symbols.md)

- [`/STUB`](stub-ms-dos-stub-file-name.md)

- [`/VERBOSE`](verbose-print-progress-messages.md)

및를 **`/LTCG`** **`/GENPROFILE`** 사용 하 여 빌드할 때 PGO를 초기화 하는 및 옵션과 함께 지정 된 링커 옵션은 지정 하지 않아도 **`/LTCG`** **`/USEPROFILE`** 됩니다.

이 문서의 나머지 부분에서는에서 수행 된 링크 타임 코드 생성에 대해 설명 합니다 **`/LTCG`** .

**`/LTCG`** 에는가 포함 됩니다 [`/GL`](gl-whole-program-optimization.md) .

또는 MSIL 모듈을 사용 하 여 컴파일된 모듈이 전달 되는 경우 링커는 링크 타임 코드 생성을 호출 **`/GL`** 합니다 ( [ `.netmodule` 링커 입력으로 파일](netmodule-files-as-linker-input.md)참조). 또는 MSIL 모듈을 링커에 전달할 때를 명시적으로 지정 하지 않으면 **`/LTCG`** **`/GL`** 링커가이 상황을 감지 하 고를 사용 하 여 링크를 다시 시작 **`/LTCG`** 합니다. **`/LTCG`** **`/GL`** 가능한 가장 빠른 빌드 성능을 위해 및 MSIL 모듈을 링커에 전달할 때를 명시적으로 지정 합니다.

훨씬 더 빠른 성능을 위해를 사용 **`/LTCG:INCREMENTAL`** 합니다. 이 옵션은 전체 프로젝트가 아닌 소스 파일 변경의 영향을 받는 파일만 링커에 최적화 하도록 지시 합니다. 이 옵션을 선택 하면 필요한 링크 시간이 상당히 줄어들 수 있습니다. 이 옵션은 [증분 링크](incremental-link-incrementally.md)와 동일한 옵션이 아닙니다.

**`/LTCG`** 는에 사용할 유효 하지 않습니다 [`/INCREMENTAL`](incremental-link-incrementally.md) .

**`/LTCG`**,, 또는를 사용 하 여 컴파일된 모듈을 연결 하는 데를 사용 하는 경우 [`/Og`](og-global-optimizations.md) [`/O1`](o1-o2-minimize-size-maximize-speed.md) [`/O2`](o1-o2-minimize-size-maximize-speed.md) [`/Ox`](ox-full-optimization.md) 다음 최적화가 수행 됩니다.

- 모듈 간 인라인 처리

- 프로시저 간 레지스터 할당(64비트 운영 체제만 해당)

- 사용자 지정 호출 규칙(x86만 해당)

- 작은 TLS 치환(x86만 해당)

- 스택 이중 맞춤(x86만 해당)

- 향상된 메모리 명확성(전역 변수 및 입력 매개 변수에 대한 보다 효율적인 간섭 정보)

> [!NOTE]
> 링커는 각 함수를 컴파일하는 데 사용된 최적화를 확인하고 링크 타임에 동일한 최적화를 적용합니다.

**`/LTCG`** 및를 사용 **`/O2`** 하면 이중 맞춤 최적화가 수행 됩니다.

**`/LTCG`** 및 **`/O1`** 가 지정 된 경우에는 이중 맞춤이 수행 되지 않습니다. 응용 프로그램에 포함 된 대부분의 함수를 속도에 맞게 컴파일하는 경우 (예를 들어, pragma를 사용 하는 등) 몇 가지 함수를 크기에 맞게 컴파일하면 [`optimize`](../../preprocessor/optimize.md) 컴파일러는 이중 맞춤이 필요한 함수를 호출 하는 경우 크기에 최적화 된 함수를 이중 정렬 합니다.

컴파일러가 함수의 모든 호출 사이트를 식별할 수 있는 경우 컴파일러는 함수의 명시적 호출 규칙 한정자를 무시하고 함수의 호출 규칙을 최적화하려고 합니다.

- 레지스터의 매개 변수 전달

- 맞춤을 위해 매개 변수 다시 정렬

- 사용하지 않는 매개 변수 제거

함수가 함수 포인터를 통해 호출 되거나 함수가를 사용 하 여 컴파일된 모듈 외부에서 호출 되는 경우 **`/GL`** 컴파일러는 함수의 호출 규칙을 최적화 하려고 시도 하지 않습니다.

> [!NOTE]
> 을 사용 하 **`/LTCG`** 고를 다시 정의 하는 경우 `mainCRTStartup` 응용 프로그램은 전역 개체를 초기화 하기 전에 실행 되는 사용자 코드와 관련 된 예기치 않은 동작을 수행할 수 있습니다. 이 문제를 해결 하는 방법에는 다음 세 가지가 있습니다. 즉 `mainCRTStartup` ,를 사용 하 여 포함 하는 파일을 다시 정의 하지 마십시오. `mainCRTStartup` **`/LTCG`** 또는 전역 변수와 개체를 정적으로 초기화 합니다.

### <a name="ltcg-and-msil-modules"></a>`/LTCG` 및 MSIL 모듈

및를 사용 하 여 컴파일된 [`/GL`](gl-whole-program-optimization.md) 모듈 [`/clr`](clr-common-language-runtime-compilation.md) **`/LTCG`** 은가 지정 된 경우 링커에 대 한 입력으로 사용할 수 있습니다.

- **`/LTCG`** 는 네이티브 개체 파일 및 혼합 된 네이티브/관리 개체 파일 (를 사용 하 여 컴파일)을 허용할 수 있습니다 **`/clr`** . **`/clr:pure`** 및 **`/clr:safe`** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017 이상에서는 지원 되지 않습니다.

- **`/LTCG:PGI`** 및를 사용 하 여 컴파일된 네이티브 모듈을 허용 하지 않습니다. **`/GL`****`/clr`**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트 **속성 페이지** 대화 상자를 엽니다. [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**  >  **일반** 속성 페이지를 선택 합니다.

1. **전체 프로그램 최적화** 속성을 수정합니다.

또한 **`/LTCG`** **Build**  >  메뉴 모음에서**프로필 기반 최적화** 빌드를 선택 하거나 프로젝트의 바로 가기 메뉴에서 프로필 기반 최적화 옵션 중 하나를 선택 하 여 특정 빌드에 적용할 수 있습니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>을 참조하세요.

## <a name="see-also"></a>참조

[MSVC 링커 참조](linking.md)\
[MSVC 링커 옵션](linker-options.md)
