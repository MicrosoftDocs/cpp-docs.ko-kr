---
title: Pragma 지시문 및 __pragma 키워드
ms.date: 08/29/2019
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: 786f76d9f7fd2eee73c6b1d009186bf93ea0c667
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842691"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Pragma 지시문 및 __pragma 키워드

Pragma 지시문은 컴퓨터 또는 운영 체제별 컴파일러 기능을 지정 합니다. Microsoft 컴파일러와 관련 된 **__pragma** 키워드를 사용 하면 매크로 정의 내에서 pragma 지시어를 코딩할 수 있습니다.

## <a name="syntax"></a>구문

> **#pragma** *토큰-문자열*\
> **__pragma (** *토큰 문자열* **)**

## <a name="remarks"></a>설명

C 및 C++의 각 구현은 호스트 컴퓨터나 운영 체제에 고유한 기능을 몇 가지 지원합니다. 예를 들어 일부 프로그램은 메모리에 있는 데이터의 위치를 정확 하 게 제어 하거나 특정 함수가 매개 변수를 수신 하는 방법을 제어 해야 합니다. **#Pragma** 지시문은 각 컴파일러가 컴퓨터 및 운영 체제별 기능을 제공할 수 있는 방법을 제공 하는 동시에 C 및 c + + 언어와의 전반적인 호환성을 유지 합니다.

Pragma는 정의에 따라 컴퓨터 또는 운영 체제에 따라 다르며 일반적으로 모든 컴파일러 마다 다릅니다. Pragma는 조건부 지시문에서 사용 하거나, 새 전처리기 기능을 제공 하거나, 컴파일러에 구현 정의 정보를 제공 하는 데 사용할 수 있습니다.

*토큰 문자열* 은 특정 컴파일러 명령 및 인수 (있는 경우)를 제공 하는 일련의 문자입니다. 숫자 기호 ( **#** )는 pragma를 포함 하는 줄에서 공백이 아닌 첫 번째 문자 여야 합니다. 공백 문자는 숫자 기호와 단어 "pragma"를 구분할 수 있습니다. **#Pragma**다음에는 변환기가 전처리 토큰으로 구문 분석할 수 있는 텍스트를 씁니다. **#Pragma** 인수는 매크로 확장의 영향을 받습니다.

컴파일러가 인식할 수 없는 pragma를 찾으면 경고를 발생 하 고 컴파일을 계속 합니다.

Microsoft C 및 C++ 컴파일러는 다음 pragma를 인식합니다.

:::row:::
   :::column span="":::
      [`alloc_text`](../preprocessor/alloc-text.md)\
      [`auto_inline`](../preprocessor/auto-inline.md)\
      [`bss_seg`](../preprocessor/bss-seg.md)\
      [`check_stack`](../preprocessor/check-stack.md)\
      [`code_seg`](../preprocessor/code-seg.md)\
      [`comment`](../preprocessor/comment-c-cpp.md)\
      [`component`](../preprocessor/component.md)\
      [`conform`](../preprocessor/conform.md)<sup>1</sup>\
      [`const_seg`](../preprocessor/const-seg.md)\
      [`data_seg`](../preprocessor/data-seg.md)\
      [`deprecated`](../preprocessor/deprecated-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`detect_mismatch`](../preprocessor/detect-mismatch.md)\
      [`fenv_access`](../preprocessor/fenv-access.md)\
      [`float_control`](../preprocessor/float-control.md)\
      [`fp_contract`](../preprocessor/fp-contract.md)\
      [`function`](../preprocessor/function-c-cpp.md)\
      [`hdrstop`](../preprocessor/hdrstop.md)\
      [`include_alias`](../preprocessor/include-alias.md)\
      [`init_seg`](../preprocessor/init-seg.md)<sup>1</sup>\
      [`inline_depth`](../preprocessor/inline-depth.md)\
      [`inline_recursion`](../preprocessor/inline-recursion.md)
   :::column-end:::
   :::column span="":::
      [`intrinsic`](../preprocessor/intrinsic.md)\
      [`loop`](../preprocessor/loop.md)<sup>1</sup>\
      [`make_public`](../preprocessor/make-public.md)\
      [`managed`](../preprocessor/managed-unmanaged.md)\
      [`message`](../preprocessor/message.md)\
      [`omp`](../preprocessor/omp.md)\
      [`once`](../preprocessor/once.md)\
      [`optimize`](../preprocessor/optimize.md)\
      [`pack`](../preprocessor/pack.md)\
      [`pointers_to_members`](../preprocessor/pointers-to-members.md)<sup>1</sup>
   :::column-end:::
   :::column span="":::
      [`pop_macro`](../preprocessor/pop-macro.md)\
      [`push_macro`](../preprocessor/push-macro.md)\
      [`region`, endregion](../preprocessor/region-endregion.md)\
      [`runtime_checks`](../preprocessor/runtime-checks.md)\
      [`section`](../preprocessor/section.md)\
      [`setlocale`](../preprocessor/setlocale.md)\
      [`strict_gs_check`](../preprocessor/strict-gs-check.md)\
      [`unmanaged`](../preprocessor/managed-unmanaged.md)\
      [`vtordisp`](../preprocessor/vtordisp.md)<sup>1</sup>\
      [`warning`](../preprocessor/warning.md)
   :::column-end:::
:::row-end:::

<sup>1</sup> c + + 컴파일러 에서만 지원 됩니다.

## <a name="pragmas-and-compiler-options"></a>Pragma 및 컴파일러 옵션

일부 pragma는 컴파일러 옵션과 같은 기능을 제공합니다. 소스 코드에 pragma가 발생하면 컴파일러 옵션에 지정된 동작을 재정의합니다. 예를 들어, [/Zp8](../build/reference/zp-struct-member-alignment.md)을 지정한 경우 [pack](../preprocessor/pack.md)을 사용 하 여 코드의 특정 섹션에 대해이 컴파일러 설정을 재정의할 수 있습니다.

```cmd
cl /Zp8 some_file.cpp
```

```cpp
// some_file.cpp - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8 again
// ...
```

## <a name="the-__pragma-keyword"></a>__Pragma () 키워드

또한 컴파일러는 **#pragma** 지시문과 동일한 기능을 포함 하는 Microsoft 관련 **__pragma** 키워드를 지원 합니다. 차이점은 **__pragma** 키워드는 매크로 정의에서 인라인으로 사용할 수 있습니다. 컴파일러는 지시문의 숫자 기호 문자 (' # ')를 [문자열 화 연산자 (#)](../preprocessor/stringizing-operator-hash.md)로 해석 하기 때문에 **#pragma** 지시어는 매크로 정의에서 사용할 수 없습니다.

다음 코드 예제에서는 매크로에 **__pragma** 키워드를 사용할 수 있는 방법을 보여 줍니다. 이 코드는 "컴파일러 COM 지원 샘플"의 ACDUAL 샘플에 있는 mfcdual.h 헤더에서 발췌되었습니다.

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

## <a name="see-also"></a>참고 항목

[C/c + + 전처리기 참조](../preprocessor/c-cpp-preprocessor-reference.md)\
[C pragma](../c-language/c-pragmas.md)\
[C++ 키워드](../cpp/keywords-cpp.md)
