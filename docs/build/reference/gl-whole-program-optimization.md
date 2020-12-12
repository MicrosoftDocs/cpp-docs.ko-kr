---
description: 자세히 알아보기:/GL (전체 프로그램 최적화)
title: /GL(전체 프로그램 최적화)
ms.date: 11/04/2016
f1_keywords:
- /gl
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: ad42eaeeacf897686831c9b415aa62026b5644f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200197"
---
# <a name="gl-whole-program-optimization"></a>/GL(전체 프로그램 최적화)

전체 프로그램 최적화를 사용합니다.

## <a name="syntax"></a>구문

```
/GL[-]
```

## <a name="remarks"></a>설명

전체 프로그램 최적화를 사용 하면 컴파일러가 프로그램의 모든 모듈에 대 한 정보를 사용 하 여 최적화를 수행할 수 있습니다. 전체 프로그램 최적화를 사용 하지 않으면 각 모듈 (compiland)에 대 한 최적화가 수행 됩니다.

전체 프로그램 최적화는 기본적으로 해제 되어 있으며 명시적으로 사용 하도록 설정 해야 합니다. 그러나 **/GL-** 를 사용 하 여 명시적으로 사용 하지 않도록 설정할 수도 있습니다.

모든 모듈에 대 한 정보를 통해 컴파일러는 다음을 수행할 수 있습니다.

- 함수 경계에서 레지스터 사용을 최적화 합니다.

- 전역 데이터에 대 한 수정 내용을 추적 하 여 로드 및 저장소의 수를 줄일 수 있도록 하는 작업을 더 효율적으로 수행 합니다.

- 포인터 역참조로 수정 된 가능한 항목 집합을 추적 하 여 로드 및 저장소의 수를 줄이는 것이 더 나은 작업을 수행 합니다.

- 함수가 다른 모듈에서 정의 된 경우에도 모듈의 함수를 인라인 합니다.

**/gl** 로 생성 된 .obj 파일은 [EDITBIN](editbin-reference.md) 및 [DUMPBIN](dumpbin-reference.md)으로 이러한 링커 유틸리티에서 사용할 수 없습니다.

**/Gl** 및 [/c](c-compile-without-linking.md)를 사용 하 여 프로그램을 컴파일하는 경우/ltcg 링커 옵션을 사용 하 여 출력 파일을 만들어야 합니다.

[/Zi](z7-zi-zi-debug-information-format.md) 는 **/gl** 과 함께 사용할 수 없습니다.

현재 버전에서 **/gl** 로 생성 된 파일의 형식은 이후 버전의 Visual C++에서 읽을 수 없습니다. 사용자가 현재, 나중에 사용할 것으로 예측 하는 모든 버전의 Visual C++에 대 한 .lib 파일의 복사본을 제공 하지 않는 한, **/gl** 을 사용 하 여 생성 된 .obj 파일로 구성 된 .lib 파일은 제공 하면 안 됩니다.

**/gl 파일** 을 생성 한 동일한 컴퓨터에 .lib 파일을 연결 하지 않는 한, **/gl** 및 미리 컴파일된 헤더 파일을 사용 하 여 생성 된 .obj 파일은 .lib 파일을 빌드하는 데 사용할 수 없습니다. .Obj 파일의 미리 컴파일된 헤더 파일의 정보는 링크 타임에 필요 합니다.

에서 사용할 수 있는 최적화에 대 한 자세한 내용과 전체 프로그램 최적화의 제한 사항에 대 한 자세한 내용은 [/ltcg](ltcg-link-time-code-generation.md)를 참조 하세요.  또한 **/gl** 은 프로필 기반 최적화를 사용할 수 있도록 합니다. /LTCG. 참조  프로필 기반 최적화를 위해 컴파일하는 경우와 프로필 기반 최적화에서 함수 순서를 지정 하려는 경우에는 [/gy](gy-enable-function-level-linking.md) 를 사용 하거나/gy. 의미 하는 컴파일러 옵션을 사용 하 여 컴파일해야 합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 개발 환경에서 **/gl** 을 지정 하는 방법에 대 한 자세한 내용은 [/ltcg (링크 타임 코드 생성)](ltcg-link-time-code-generation.md) 를 참조 하세요.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
