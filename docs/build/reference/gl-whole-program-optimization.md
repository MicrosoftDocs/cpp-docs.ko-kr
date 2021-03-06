---
description: 자세히 알아보기:/GL (전체 프로그램 최적화)
title: /GL(전체 프로그램 최적화)
ms.date: 03/05/2021
f1_keywords:
- /GL
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.openlocfilehash: 509deaae8881c4875a9ec2ddf4d5f1ee7744a2cf
ms.sourcegitcommit: c0c9cdae79f19655e809a4979227c51bb19cff63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236552"
---
# <a name="gl-whole-program-optimization"></a>`/GL` (전체 프로그램 최적화)

전체 프로그램 최적화를 사용합니다.

## <a name="syntax"></a>구문

> **`/GL`**[**`-`**]

## <a name="remarks"></a>설명

전체 프로그램 최적화를 사용 하면 컴파일러가 프로그램의 모든 모듈에 대 한 정보를 사용 하 여 최적화를 수행할 수 있습니다. 전체 프로그램 최적화를 사용 하지 않을 경우 최적화는 모듈별 (compiland) 기준으로 수행 됩니다.

전체 프로그램 최적화는 기본적으로 해제 되어 있으며 명시적으로 사용 하도록 설정 해야 합니다. 그러나에서 명시적으로 해제 하는 것도 가능 **`/GL-`** 합니다.

모든 모듈에 대 한 정보를 통해 컴파일러는 다음을 수행할 수 있습니다.

- 함수 경계에서 레지스터 사용을 최적화 합니다.

- 전역 데이터에 대 한 수정 내용을 추적 하 여 로드 및 저장소의 수를 줄일 수 있도록 하는 작업을 더 효율적으로 수행 합니다.

- 포인터 역참조로 수정 된 항목의 가능한 집합을 추적 하 여 필요한 로드 및 저장소를 줄입니다.

- 함수가 다른 모듈에서 정의 된 경우에도 모듈의 함수를 인라인 합니다.

*`.obj`* 로 생성 된 파일은 **`/GL`** 및와 같은 링커 유틸리티에서 사용할 수 [`EDITBIN`](editbin-reference.md) [`DUMPBIN`](dumpbin-reference.md) 없습니다.

및를 사용 하 여 프로그램을 컴파일하는 경우 **`/GL`** [`/c`](c-compile-without-linking.md) /ltcg 링커 옵션을 사용 하 여 출력 파일을 만들어야 합니다.

[`/ZI`](z7-zi-zi-debug-information-format.md) 는와 함께 사용할 수 없습니다. **`/GL`**

최신 버전의로 생성 된 파일 형식은 **`/GL`** 나중 버전의 Visual Studio 및 MSVC 도구 집합에서 읽을 수 없는 경우가 많습니다. *`.lib`* 사용자가 사용 해야 하는 모든 버전의 Visual Studio에 대 한 파일의 복사본을 제공 하지 않는 한, 현재와 나중에에서 생성 된 파일로 구성 된 파일을 제공 하지 않습니다 *`.lib`* *`.obj`* **`/GL`** . 자세한 내용은 [이진 호환성의 제한 사항](../../porting/binary-compat-2015-2017.md#restrictions)을 참조 하세요.

*`.obj`***`/GL`** 및 미리 컴파일된 헤더 파일에 의해 생성 된 파일은 파일을 *`.lib`* 생성 한 *`.lib`* 동일한 컴퓨터에 연결 되지 않은 경우 파일을 빌드하는 데 사용할 수 없습니다 **`/GL`** *`.obj`* . *`.obj`* 파일의 미리 컴파일된 헤더 파일의 정보는 링크 타임에 필요 합니다.

에서 사용할 수 있는 최적화에 대 한 자세한 내용과 전체 프로그램 최적화의 제한 사항에 대 한 자세한 내용은을 참조 하십시오 [`/LTCG`](ltcg-link-time-code-generation.md) .  **`/GL`** 또한 프로필 기반 최적화를 사용할 수 있도록 합니다. 프로필 기반 최적화를 위해 컴파일하는 경우와 프로필 기반 최적화에서 함수 순서를 지정 하려면 [`/Gy`](gy-enable-function-level-linking.md) 또는/Gy. 의미 하는 컴파일러 옵션을 사용 하 여 컴파일해야 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

개발 환경에서를 지정 하는 방법에 대 한 자세한 내용은 **`/GL`** [ `/LTCG` (링크 타임 코드 생성)](ltcg-link-time-code-generation.md) 를 참조 하세요.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
