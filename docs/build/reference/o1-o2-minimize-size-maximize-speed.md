---
title: /O1, /O2(크기 최소화, 속도 최대화)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: 565cfd509e48b012581ecd6243507c60810338b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596900"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2(크기 최소화, 속도 최대화)

생성 된 코드의 속도 및 미리 정의 된 집합이 크기에 영향을 주는 옵션을 선택 합니다.

## <a name="syntax"></a>구문

> / O1/O2

## <a name="remarks"></a>설명

**/o1** 하 고 **/o2** 컴파일러 옵션은 신속 하 게 한 번에 몇 가지 특정 최적화 옵션을 설정 합니다. 합니다 **/o1** 옵션의 대부분의 경우 가장 작은 코드를 작성 하는 개별 최적화 옵션을 설정 합니다. 합니다 **/o2** 대부분의 경우 가장 빠른 코드를 만드는 옵션을 설정 하는 옵션입니다. 합니다 **/o2** 옵션이 릴리스 빌드에 대 한 기본 옵션입니다. 이 테이블에서 설정 된 특정 옵션을 보여 줍니다 **/o1** 하 고 **/o2**:

|옵션|에 해당|
|------------|-------------------|
|**/ O1** (크기 최소화)|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (속도 최대화)|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** 하 고 **/o2** 함께 사용할 수 없습니다.

> [!NOTE]
> **x86 특정** 프레임 포인터 생략 사용을 의미 하는 이러한 옵션 ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) 옵션입니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 아래 **구성 속성**오픈 **C/c + +** 를 선택한 후는 **최적화** 속성 페이지.

1. 수정 된 **최적화** 속성입니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/O 옵션(코드 최적화)](../../build/reference/o-options-optimize-code.md)<br/>
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)<br/>
[/EH(예외 처리 모델)](../../build/reference/eh-exception-handling-model.md)
