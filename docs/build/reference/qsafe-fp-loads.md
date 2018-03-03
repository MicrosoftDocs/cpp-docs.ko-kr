---
title: /Qsafe_fp_loads | Microsoft Docs
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e079e084c641318c9bec0820263487139b4d5076
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/25/2018
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

부동 소수점 값에 대한 정수 이동 명령을 필요로 하고 특정 부동 소수점 부하 최적화를 사용하지 않도록 설정합니다.

## <a name="syntax"></a>구문

> **/Qsafe_fp_loads**

## <a name="remarks"></a>설명

**/Qsafe_fp_loads** 에서만 사용 가능 컴파일러에서는 x86 대상으로 하는 것으로 x64 또는 ARM 대상 컴파일러에서 사용할 수 있습니다.

**/Qsafe_fp_loads** 강제로 메모리 및 MMX 간 데이터 이동 부동 소수점 이동 명령 대신 정수 이동 명령을 사용 하도록 컴파일러에 등록 합니다. 이 옵션은 또한 로드 시 값(예: NaN 값)이 예외를 일으킬 수 있는 여러 제어 경로에서 로드할 수 있는 부동 소수점 값에 대한 레지스터 로드 최적화를 사용하지 않도록 설정합니다.

이 옵션을 재정의 하 여 [/fp: 제외한](../../build/reference/fp-specify-floating-point-behavior.md)합니다. **/Qsafe_fp_loads** 변수로 지정 된 컴파일러 동작의 하위 집합을 지정 **/fp: 제외한**합니다.

**/Qsafe_fp_loads** 와 호환 되지 않는 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 및 [/fp: fast](../../build/reference/fp-specify-floating-point-behavior.md)합니다. 부동 소수점 컴파일러 옵션에 대 한 자세한 내용은 참조 [/fp (부동 소수점 동작 지정)](../../build/reference/fp-specify-floating-point-behavior.md)합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 참조 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)합니다.

1. 선택 된 **구성 속성** > **C/c + +** > **명령줄** 속성 페이지.

1. 입력에 컴파일러 옵션은 **추가 옵션** 상자입니다. 선택 **확인** 에 변경 내용을 적용 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션(하위 수준 작업)](../../build/reference/q-options-low-level-operations.md)  
[컴파일러 옵션](../../build/reference/compiler-options.md)  
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)  
