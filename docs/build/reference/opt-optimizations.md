---
description: 자세히 알아보기:/OPT (최적화)
title: /OPT(최적화)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: 73cdb182941ddf865695d58f6d60a96002f5005a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221958"
---
# <a name="opt-optimizations"></a>/OPT(최적화)

LINK가 빌드하는 동안 수행할 최적화를 제어합니다.

## <a name="syntax"></a>Syntax

> **/OPT:**{**REF** \| **NEF**} \
> **/Opt:**{**ICF** \[ **=** _반복_] \| **noicf**} \
> **/OPT:**{**LBR** \| **NOLBR**}

## <a name="arguments"></a>인수

**참조** &#124; **없음**

**/Opt: REF** 는 참조 되지 않는 함수 및 데이터를 제거 합니다. **/Opt: 없음 ef** 는 참조 되지 않는 함수 및 데이터를 유지 합니다.

/OPT: REF를 사용 하는 경우 LINK는 *comdat* 라는 참조 되지 않은 패키지 함수와 데이터를 제거 합니다. 이러한 최적화를 전이적 COMDAT 제거라고 합니다. **/Opt: REF** 옵션은 증분 링크도 사용 하지 않도록 설정 합니다.

클래스 선언 내에 정의 된 인라인 함수 및 멤버 함수는 항상 Comdat입니다. 개체 파일의 모든 함수는 [/gy](gy-enable-function-level-linking.md) 옵션을 사용 하 여 컴파일된 경우 comdat로 생성 됩니다. **`const`** Comdat에 데이터를 저장 하려면를 사용 하 여 선언 해야 합니다 `__declspec(selectany)` . 제거 또는 정리를 위해 데이터를 지정 하는 방법에 대 한 자세한 내용은 [selectany](../../cpp/selectany.md)를 참조 하세요.

기본적으로/opt: **eef** 또는 [/debug](debug-generate-debug-info.md) 가 지정 되지 않은 경우에는 **/opt: REF** 가 링커에 의해 활성화 됩니다. 이 기본값을 재정의 하 고 참조 되지 않는 Comdat를 프로그램에 유지 하려면 **/opt: 없음 ef** 를 지정 합니다. [/INCLUDE](include-force-symbol-references.md) 옵션을 사용 하 여 특정 기호의 제거를 재정의할 수 있습니다.

[/Debug](debug-generate-debug-info.md) 를 지정 하면 **/opt** 의 기본값 **은 없습니다.** 및 모든 함수가 이미지에 유지 됩니다. 이 기본값을 재정의 하 고 디버그 빌드를 최적화 하려면 **/opt: REF** 를 지정 합니다. 이를 통해 실행 파일의 크기를 줄일 수 있으며 디버그 빌드에서도 유용한 최적화를 수행할 수 있습니다. 또한 디버그 빌드에서 동일한 함수를 유지 하기 위해 **/opt: NOICF** 를 지정 하는 것이 좋습니다. 이렇게 하면 스택 추적을 읽고 다른 방식으로는 함께 정리될 함수에서 중단점을 쉽게 설정할 수 있습니다.

 \[ ICF **=** _반복_] &#124; **Noicf**

**ICF** \[ **=** _반복_]을 사용 하 여 동일한 COMDAT 정리를 수행 합니다. 중복 COMDAT는 링커 출력에서 제거될 수 있습니다. 선택적인 *반복* 매개 변수는 중복을 위해 기호를 트래버스하는 횟수를 지정 합니다. 기본 반복 횟수는 1입니다. 추가 반복에서 이전 반복의 정리를 통해 발견되지 않은 중복 항목을 더 많이 찾을 수도 있습니다.

/Opt: **NOICF** 또는 [/debug](debug-generate-debug-info.md) 가 지정 되지 않은 경우 기본적으로 **/opt: ICF** 는 링커에 의해 사용 하도록 설정 됩니다. 이 기본값을 재정의 하 고 Comdat가 프로그램에서 접힌 되지 않도록 하려면 **/opt: NOICF** 를 지정 합니다.

디버그 빌드에서는 명시적으로 **/opt: ICF** 를 지정 하 여 COMDAT 정리를 사용 하도록 설정 해야 합니다. 그러나 **/opt: ICF** 는 동일한 데이터 또는 함수를 병합할 수 있으므로 스택 추적에 표시 되는 함수 이름을 변경할 수 있습니다. 또한 특정 함수에서 중단점을 설정 하거나 디버거의 일부 데이터를 검사 하는 것은 불가능 하며, 코드를 한 단계씩 실행할 때 예기치 않은 함수를 사용할 수 있습니다. 코드의 동작은 동일 하지만 디버거 프레젠테이션은 매우 복잡할 수 있습니다. 따라서 작은 코드의 이점이 이러한 단점 보다 큰 경우를 제외 하 고는 디버그 빌드에서 **/opt: ICF** 를 사용 하지 않는 것이 좋습니다.

> [!NOTE]
> **/Opt: ICF** 는 다른 함수 또는 읽기 전용 데이터 멤버 (즉,/gy를 사용 하 여 컴파일된 변수)에 동일한 주소를 할당할 수 있으므로 **`const`** 함수 또는 읽기 전용 데이터 멤버의 고유 주소에 종속 된 프로그램을 중단할 수 있습니다. 자세한 내용은 [/Gy(함수 수준 링크 사용)](gy-enable-function-level-linking.md)를 참조하세요.

**Lbr** &#124; **nolbr**

**/Opt: lbr** 및 **/OPT: nolbr** 옵션은 ARM 이진 파일에만 적용 됩니다. 특정 ARM 프로세서 분기 명령에는 제한 된 범위가 있으므로 링커가 범위를 벗어난 주소로 점프 하는 것을 감지 하면 분기 명령의 대상 주소를 실제 대상을 대상으로 하는 분기 명령이 포함 된 코드 "아일랜드"의 주소로 대체 합니다. **/Opt: LBR** 을 사용 하 여 전체 코드 크기를 최소화 하는 긴 분기 명령 및 중간 코드 아일랜드 배치의 검색을 최적화할 수 있습니다. **/Opt: NOLBR** 은 최적화 하지 않고 발생 한 긴 분기 명령에 대 한 코드 아일랜드를 생성 하도록 링커에 지시 합니다.

기본적으로 **/opt: LBR** 옵션은 증분 링크를 사용할 수 없을 때 설정 됩니다. 비연속 링크는 아니지만 긴 분기 최적화는 하지 않으려면 **/opt: NOLBR** 를 지정 합니다. **/Opt: LBR** 옵션은 증분 링크를 사용 하지 않도록 설정 합니다.

## <a name="remarks"></a>설명

명령줄에서 사용 되는 경우 링커는 기본값 **/opt: REF, ICF, LBR** 을 사용 합니다. **/Debug** 를 지정 하는 경우 기본값은 **/OPT: 없음 EF, NOICF, nolbr** 입니다.

**/Opt** 최적화는 일반적으로 이미지 크기를 줄이고 프로그램 속도를 높입니다. 이러한 향상 된 기능은 대규모 프로그램에서 매우 유용할 수 있으므로 정품 빌드에 대해 기본적으로 사용 하도록 설정 됩니다.

링커 최적화는 추가 시간이 앞에 추가 되지만 최적화 된 코드는 더 작은 최종 이미지를 만드는 데 사용 되는 재배치가 적은 경우에도 시간을 절약 하 고, 처리 하 고 PDB에 쓸 디버그 정보가 적은 경우에도 더 많은 시간을 절약 합니다. 최적화를 사용 하도록 설정 하면 더 빠른 링크 시간이 발생할 수 있습니다. 자세한 분석 비용은 링커가 더 작은 이진 파일을 통해 전달 되는 시간 절약 시간 보다 더 많을 수 있습니다.

**/Opt** 인수는 쉼표로 구분 하 여 함께 지정할 수 있습니다. 예를 들어 **/opt: ref/opt: noicf** 대신 **/opt: REF, noicf** 를 지정할 수 있습니다.

[/Verbose](verbose-print-progress-messages.md) 링커 옵션을 사용 하 여 **/opt: REF** 에 의해 제거 된 함수와 **/opt: ICF** 로 접힌 함수를 볼 수 있습니다.

**/Opt** 인수는 일반적으로 VISUAL Studio IDE의 **새 프로젝트** 대화 상자를 사용 하 여 만든 프로젝트에 대해 설정 되며, 일반적으로 디버그 및 릴리스 구성에 대해 다른 값을 포함 합니다. 프로젝트에 이러한 링커 옵션에 대 한 값이 설정 되어 있지 않으면 프로젝트 기본값을 얻을 수 있습니다 .이 기본값은 명령줄에서 링커에 사용 되는 기본값과 다를 수 있습니다.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 OPT:ICF 또는 OPT:REF 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **링커**  >  **최적화** 속성 페이지를 선택 합니다.

1. 다음 속성 중 하나를 수정합니다.

   - **COMDAT 정리 사용**

   - **참조**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 OPT:LBR 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** > **링커** > **명령줄** 속성 페이지를 선택합니다.

1. **추가 옵션** 에 옵션을 입력 합니다.

   `/opt:lbr` 또는 `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> 및 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> 속성을 참조하십시오.

## <a name="see-also"></a>참고 항목

- [MSVC 링커 참조](linking.md)
- [MSVC 링커 옵션](linker-options.md)
