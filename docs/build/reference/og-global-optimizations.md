---
title: /Og(전역 최적화)
description: 이전에는 전역 최적화를 사용 하는 데 사용 되는 사용 되지 않는 MSVC 컴파일러 옵션/Og를 설명 합니다.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: 2d5baf4967f4f4f945540d2a7baef399974d2d42
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506577"
---
# <a name="og-global-optimizations"></a>`/Og` (전역 최적화)

더 이상 사용되지 않습니다. 로컬 및 전역 최적화, 자동 등록 할당 및 루프 최적화를 제공 합니다. 대신 [ `/O1` (크기 최소화)](o1-o2-minimize-size-maximize-speed.md) 또는 [ `/O2` (속도 최대화)](o1-o2-minimize-size-maximize-speed.md) 중 하나를 사용 하는 것이 좋습니다.

## <a name="syntax"></a>구문

> **`/Og`**

## <a name="remarks"></a>설명

**`/Og`** 는 사용 되지 않습니다. 최적화를 사용 하도록 설정 하면 이제 이러한 최적화가 기본적으로 사용 하도록 설정 됩니다. 최적화에 대 한 자세한 내용은 [ `/O1` , `/O2` (크기 최소화, 속도 최대화)](o1-o2-minimize-size-maximize-speed.md)또는 [ `/Ox` (대부분의 속도 최적화 사용)](ox-full-optimization.md)을 참조 하세요.

에서 사용할 수 있는 최적화는 **`/Og`** 다음과 같습니다.

- 로컬 및 전역 공통 부분식 제거

   이 최적화에서 공통 하위 식의 값은 한 번 계산 됩니다. 다음 예제에서 `b` 세 식 사이에 및 값이 `c` 변경 되지 않는 경우 컴파일러는 `b + c` 에 대 한 계산을 임시 변수에 할당 하 고이 변수를에 사용할 수 있습니다 `b + c` .

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   로컬 공통 하위 식 최적화의 경우 컴파일러는 일반적인 부분식에 대 한 코드의 짧은 섹션을 검사 합니다. 전역 공통 부분식 최적화의 경우 컴파일러는 전체 함수에서 일반적인 하위 식을 검색 합니다.

- 자동 레지스터 할당

   이러한 최적화를 통해 컴파일러는 자주 사용 되는 변수 및 부분식을 레지스터에 저장할 수 있습니다. **`register`** 키워드는 무시 됩니다.

- 루프 최적화

   이 최적화는 루프 본문에서 고정 부분식을 제거 합니다. 최적 루프에는 루프가 실행 될 때마다 값이 변경 되는 식만 포함 됩니다. 다음 예에서는 식이 `x + y` 루프 본문에서 변경 되지 않습니다.

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   최적화 후 `x + y` 은 루프가 실행 될 때마다 한 번 계산 됩니다.

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   루프 최적화는 컴파일러에서, 또는로 설정 하는 별칭을 사용 하지 않는다고 가정할 때 훨씬 더 효과적입니다 [`__restrict`](../../cpp/extension-restrict.md) [`noalias`](../../cpp/noalias.md) [`restrict`](../../cpp/restrict.md) .

   > [!NOTE]
   > 옵션과 함께 pragma를 사용 하 여 함수 별로 전역 최적화를 사용 하거나 사용 하지 않도록 설정할 수 있습니다 `optimize` `g` .

관련 정보는 [ `/Oi` (내장 함수 생성)](oi-generate-intrinsic-functions.md) 및 [ `/Ox` (대부분의 속도 최적화 사용)](ox-full-optimization.md)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
