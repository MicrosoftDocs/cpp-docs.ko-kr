---
description: '자세한 정보: C Pragma'
title: C Pragma
ms.date: 07/26/2020
helpviewer_keywords:
- pragmas, C/C++
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
ms.openlocfilehash: 45b899dc3266390095d70e8f74f6c6e5a58fc6c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300244"
---
# <a name="c-pragmas"></a>C Pragma

**Microsoft 전용**

*pragma* 는 컴파일러가 컴파일 타임에 특정 작업을 수행하도록 지시합니다. Pragma는 컴파일러마다 서로 다릅니다. 예를 들어 `optimize` pragma를 사용하여 프로그램에서 수행하는 최적화를 설정할 수 있습니다. Microsoft C pragma는 다음과 같습니다.

:::row:::
    :::column:::
        [`alloc_text`](../preprocessor/alloc-text.md)\
        [`auto_inline`](../preprocessor/auto-inline.md)\
        [`bss_seg`](../preprocessor/bss-seg.md)\
        [`check_stack`](../preprocessor/check-stack.md)\
        [`code_seg`](../preprocessor/code-seg.md)\
        [`comment`](../preprocessor/comment-c-cpp.md)\
        [`component`](../preprocessor/component.md)\
        [`const_seg`](../preprocessor/const-seg.md)\
        [`data_seg`](../preprocessor/data-seg.md)
    :::column-end:::
    :::column:::
        [`deprecated`](../preprocessor/deprecated-c-cpp.md)\
        [`detect_mismatch`](../preprocessor/detect-mismatch.md)\
        [`fenv_access`](../preprocessor/fenv-access.md)\
        [`float_control`](../preprocessor/float-control.md)\
        [`fp_contract`](../preprocessor/fp-contract.md)\
        [`function`](../preprocessor/function-c-cpp.md)\
        [`hdrstop`](../preprocessor/hdrstop.md)\
        [`include_alias`](../preprocessor/include-alias.md)\
        [`inline_depth`](../preprocessor/inline-depth.md)
    :::column-end:::
    :::column:::
        [`inline_recursion`](../preprocessor/inline-recursion.md)\
        [`intrinsic`](../preprocessor/intrinsic.md)\
        [`make_public`](../preprocessor/make-public.md)\
        [`managed`](../preprocessor/managed-unmanaged.md)\
        [`message`](../preprocessor/message.md)\
        [`omp`](../preprocessor/omp.md)\
        [`once`](../preprocessor/once.md)\
        [`optimize`](../preprocessor/optimize.md)\
        [`pack`](../preprocessor/pack.md)
    :::column-end:::
    :::column:::
        [`pop_macro`](../preprocessor/pop-macro.md)\
        [`push_macro`](../preprocessor/push-macro.md)\
        [`region`, `endregion`](../preprocessor/region-endregion.md)\
        [`runtime_checks`](../preprocessor/runtime-checks.md)\
        [`section`](../preprocessor/section.md)\
        [`setlocale`](../preprocessor/setlocale.md)\
        [`strict_gs_check`](../preprocessor/strict-gs-check.md)\
        [`unmanaged`](../preprocessor/managed-unmanaged.md)\
        [`warning`](../preprocessor/warning.md)
    :::column-end:::
:::row-end:::

Microsoft C 컴파일러 pragma에 대한 설명은 [Pragma 지시문 및 `__Pragma` 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)를 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[원본 파일 및 원본 프로그램](../c-language/source-files-and-source-programs.md)
