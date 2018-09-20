---
title: -Ox (대부분의 속도 최적화 사용) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /ox
dev_langs:
- C++
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1da84c3a4ec481d3af2880a80f5923bf0c50cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438082"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox (대부분의 속도 최적화 사용)

합니다 **/Ox** 컴파일러 옵션을 사용 하면 최적화 속도 유사한의 조합입니다. 일부 버전의 Visual Studio IDE 및 컴파일러 도움말 메시지를이 라고 *전체 최적화*, 되지만 **/Ox** 컴파일러 옵션을 사용 하 여 속도 최적화 옵션의 하위 집합만 사용 하면 **/O2**합니다.

## <a name="syntax"></a>구문

> /Ox

## <a name="remarks"></a>설명

**/Ox** 컴파일러 옵션이 사용 하도록 설정 합니다 **/O** 컴파일러 옵션는 속도입니다. 합니다 **/Ox** 컴파일러 옵션이 추가 포함 되지 않습니다 [/GF (중복 문자열 제거)](../../build/reference/gf-eliminate-duplicate-strings.md) 하 고 [/Gy (함수 수준 링크 사용)](../../build/reference/gy-enable-function-level-linking.md) 로사용하도록설정하는옵션[/O1 또는/o2 (크기 최소화, 속도 최대화)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)합니다. 적용 하 여 추가 옵션 **/o1** 하 고 **/o2** 문자열 또는 디버깅에 영향을 줄 수 있는 대상 주소 및 엄격한 언어 규칙을 공유 하는 함수에 대 한 포인터를 발생할 수 있습니다. 합니다 **/Ox** 옵션은 포함 하지 않고 대부분의 최적화를 사용 하는 쉬운 방법을 **/GF** 하 고 **/Gy**합니다. 자세한 설명은 참조 하세요. 합니다 [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) 하 고 [/Gy](../../build/reference/gy-enable-function-level-linking.md) 옵션입니다.

합니다 **/Ox** 컴파일러 옵션 조합 하 여 다음 옵션을 사용 하는 것 같습니다.

- [/Ob (인라인 함수 확장)](../../build/reference/ob-inline-function-expansion.md)option 매개 변수 2는 위치 (**/ob2**)

- [/Og(전역 최적화)](../../build/reference/og-global-optimizations.md)

- [/Oi(내장 함수 만들기)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot (속도 우선 코드)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (프레임 포인터 생략)](../../build/reference/oy-frame-pointer-omission.md)

**/Ox** 에서 함께 사용할 수 없습니다.

- [/ O1 (크기 최소화)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (속도 최대화)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od(디버그 사용 안 함)](../../build/reference/od-disable-debug.md)

오차의 속도 취소할 수 있습니다는 **/Ox** 컴파일러 옵션을 지정 하는 경우 **/Oxs**를 결합 하는 합니다 **/Ox** 컴파일러 옵션 [(크기 우선 작은 /Os 코드)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)합니다. 결합 된 옵션은 코드 크기를 선호합니다.

릴리스 빌드에 대 한 모든 사용 가능한 파일-수준 최적화를 적용 하려면 지정할 권장 [/o2 (속도 최대화)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) of **/Ox**, 및 [/o1 (크기 최소화)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 대신 **/Oxs**합니다. 릴리스에서 더 많은 최적화 빌드에 대 한 수도 합니다 [/GL (전체 프로그램 최적화)](../../build/reference/gl-whole-program-optimization.md) 컴파일러 옵션 및 [/LTCG (링크 타임 코드 생성)](../../build/reference/ltcg-link-time-code-generation.md) 링커 옵션입니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 아래 **구성 속성**오픈 **C/c + +** 를 선택한 후는 **최적화** 속성 페이지.

1. 수정 된 **최적화** 속성입니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/O 옵션(코드 최적화)](../../build/reference/o-options-optimize-code.md)<br/>
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)