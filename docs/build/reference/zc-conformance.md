---
title: /Zc(규칙)
description: /Zc 규격 컴파일러 옵션은 규격 또는 이전 버전과 호환 되는 동작에 대 한 지원을 사용 하거나 사용 하지 않도록 설정 합니다.
ms.date: 09/10/2020
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 13e06cd75f1ee684c2ee1ad6239aeb77b805675e
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041525"
---
# <a name="zc-conformance"></a>`/Zc` 규칙

**`/Zc`** 컴파일러 옵션을 사용 하 여 표준 또는 Microsoft 전용 컴파일러 동작을 지정할 수 있습니다.

## <a name="syntax"></a>구문

> **`/Zc:`**_옵션_{,_옵션_}

## <a name="remarks"></a>설명

Visual Studio에서 표준과 호환 되지 않는 C 또는 c + +에 대 한 확장을 구현 하는 경우 **`/Zc`** 규칙 옵션을 사용 하 여 표준에 맞는 또는 Microsoft 특정 동작을 지정할 수 있습니다. 일부 옵션의 경우 기존 코드에 대 한 대규모 주요 변경 사항을 방지 하기 위해 Microsoft 고유의 동작이 기본값입니다. 다른 경우에 기본값은 표준 동작으로, 보안, 성능 또는 호환성의 향상 된 기능이 주요 변경 비용 보다 더 중요 합니다. 각 규칙 옵션의 기본 설정은 최신 버전의 Visual Studio에서 변경 될 수 있습니다. 각 규칙 옵션에 대 한 자세한 내용은 특정 옵션에 대 한 항목을 참조 하세요. [`/permissive-`](permissive-standards-conformance.md)컴파일러 옵션은 기본적으로 설정 되지 않은 규칙 옵션을 해당 하는 규칙 설정으로 암시적으로 설정 합니다.

다음은 **`/Zc`** 컴파일러 옵션입니다.

| 옵션 | 동작 |
|--|--|
| [`/Zc:alignedNew`](zc-alignednew.md) | C + + 17 오버 정렬 된 동적 할당을 사용 합니다 (기본적으로 c + + 17의 경우). |
| [`/Zc:auto`](zc-auto-deduce-variable-type.md) | 에 대해 새로운 표준 c + +의 의미를 적용 **`auto`** 합니다 (기본적으로 설정). |
| [`/Zc__cplusplus`](zc-cplusplus.md) | 매크로를 사용 `__cplusplus` 하 여 지원 되는 표준 (기본적으로 해제)을 보고 합니다. |
| [`/Zc:externConstexpr`](zc-externconstexpr.md) | 변수에 대해 외부 링크를 사용 하도록 설정 **`constexpr`** 합니다 (기본적으로 해제). |
| [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) | 표준 c + + 범위 지정 규칙을 적용 **`for`** 합니다 (기본적으로 설정). |
| [`/ZcimplicitNoexcept`](zc-implicitnoexcept-implicit-exception-specifiers.md) | **`noexcept`** 필수 함수 (기본적으로 설정)에서 암시적으로 사용 하도록 설정 합니다. |
| [`/Zc:inline`](zc-inline-remove-unreferenced-comdat.md) | 참조 되지 않은 함수 또는 데이터는 COMDAT 이거나 내부 링크만 있는 경우 (기본적으로 해제 됨) 제거 합니다. |
| [`/Zc:noexceptTypes`](zc-noexcepttypes.md) | C + + 17 규칙을 적용 **`noexcept`** 합니다 (c + + 17 이상에서는 기본적으로 설정). |
| [`/Zc:preprocessor`](zc-preprocessor.md) | 새로운 규격 전처리기 (C11/C17를 제외 하 고 기본적으로 해제)를 사용 합니다. |
| [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) | UDT 임시는 비 const lvalue 참조에 바인딩되지 않습니다 (기본적으로 해제 됨). |
| [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) | 표준 c + + 명시적 형식 변환 규칙을 적용 합니다 (기본적으로 해제). |
| [`/Zc:sizedDealloc`](zc-sizeddealloc-enable-global-sized-dealloc-functions.md) | C + + 14 전역 크기 할당 해제 함수를 사용 합니다 (기본적으로 설정). |
| [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) | 문자열-리터럴을 `char*` 변환 하거나 변환 하지 않습니다 `wchar_t*` (기본적으로 해제). |
| [`/Zc:ternary`](zc-ternary.md) | 피연산자 형식에 조건부 연산자 규칙을 적용 합니다 (기본적으로 꺼져 있습니다). |
| [`/Zc:threadSafeInit`](zc-threadsafeinit-thread-safe-local-static-initialization.md) | 스레드로부터 안전한 로컬 정적 초기화를 사용 하도록 설정 합니다 (기본적으로 설정). |
| [`/Zc:throwingNew`](zc-throwingnew-assume-operator-new-throws.md) | **`operator new`** 실패 시 throw (기본적으로 해제)를 가정 합니다. |
| [`/Zc:trigraphs`](zc-trigraphs-trigraphs-substitution.md) | 삼중 자 (사용 되지 않음, 기본적으로 해제)를 사용 합니다. |
| [`/Zc:twoPhase`](zc-twophase.md) | 순응 하지 않는 템플릿 구문 분석 동작을 사용 합니다 (기본적으로 준수). |
| [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) | **`wchar_t`** 는 typedef가 아닌 네이티브 형식입니다 (기본적으로 설정 됨). |

Visual C++의 규칙과 관련된 문제에 대한 자세한 내용은 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
