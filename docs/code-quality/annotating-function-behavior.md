---
description: '자세한 정보: 함수 동작에 주석 달기'
title: 함수 동작에 주석 달기
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
ms.openlocfilehash: 8db57731f34c3e3085766ddb0a79dfa1c231dcb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136736"
---
# <a name="annotating-function-behavior"></a>함수 동작에 주석 달기

[함수 매개 변수와 반환 값](../code-quality/annotating-function-parameters-and-return-values.md)에 주석을 추가 하는 것 외에도 전체 함수의 속성에 주석을 달 수 있습니다.

## <a name="function-annotations"></a>함수 주석

다음 주석은 해당 함수 전체에 적용되며, 주석의 작동 방법 또는 예상 결과를 보여줍니다.

|Annotation|설명|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|독립 실행형으로 사용되지 않으며, 대신 `_When_` 주석과 함께 사용되는 조건자입니다. 자세한 내용은 [주석이 적용 되는 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)을 참조 하세요.<br /><br /> `name`매개 변수는 `_Function_class_` 일부 함수 선언에서 주석에도 표시 되는 임의의 문자열입니다.  `_Called_from_function_class_` 현재 분석 중인 함수에의 값이 같은를 사용 하 여 주석이 추가 된 경우 0이 아닌 값을 반환 하 `_Function_class_` `name` 고, 그렇지 않으면 0을 반환 합니다.|
|`_Check_return_`|반환 값을 주석 처리하고 호출자가 이를 조사하도록 지시합니다. 함수가 void 컨텍스트에서 호출되면 검사기가 오류를 보고합니다.|
|`_Function_class_(name)`|`name` 매개 변수는 사용자가 지정하는 임의의 문자열입니다.  이 매개 변수는 다른 네임스페이스와 구분되는 네임스페이스에 존재합니다. 함수, 함수 포인터 또는 가장 유용한 함수 포인터 유형은 하나 이상의 함수 클래스에 속하는 것으로 지정될 수 있습니다.|
|`_Raises_SEH_exception_`|`_When_` 및 `_On_failure_` 조건에 따라 항상 SEH(구조화된 예외 처리기) 예외를 일으키는 함수를 주석 처리합니다. 자세한 내용은 [주석이 적용 되는 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)을 참조 하세요.|
|`_Maybe_raises_SEH_exception_`|`_When_` 및 `_On_failure_` 조건에 따라 선택적으로 SEH 예외를 일으킬 수 있는 함수를 주석 처리합니다.|
|`_Must_inspect_result_`|반환 값, 매개 변수 및 전역 값을 포함해서 모든 출력 값을 주석 처리합니다.  분석기는 주석 처리된 개체의 값이 이후에 검사되지 않은 경우 오류를 보고합니다. "검사"에는 조건 식에 사용되었거나, 출력 매개 변수 또는 전역 값에 할당되었거나, 매개 변수로 전달되었는지 여부가 포함됩니다.  반환 값에서 `_Must_inspect_result_`에는 `_Check_return_`이 포함됩니다.|
|`_Use_decl_annotations_`|는 헤더의 주석 목록 대신 함수 정의 (함수 본문이 라고도 함)에 사용할 수 있습니다.  를 사용 하는 경우 `_Use_decl_annotations_` 동일한 함수의 범위 내 헤더에 표시 되는 주석이 주석이 있는 정의에도 있는 것 처럼 사용 됩니다 `_Use_decl_annotations_` .|

## <a name="successfailure-annotations"></a>성공/실패 주석

함수는 실패할 수 있으며, 실패할 경우에는 해당 결과가 완전하지 않거나 함수가 성공할 때의 결과와 다를 수 있습니다.  다음 목록에서 주석은 실패 동작을 표현하는 방법을 제공합니다.  이러한 주석을 사용하려면 성공을 확인할 수 있도록 설정해야 합니다. 따라서 `_Success_` 주석이 필요합니다.  `NTSTATUS` 및 `HRESULT`에는 이미 `_Success_` 주석이 기본 제공되어 있습니다. 하지만 `_Success_` 또는 `NTSTATUS`에 고유한 `HRESULT` 주석을 지정할 경우 기본 제공 주석을 재정의합니다.

|Annotation|설명|
|----------------|-----------------|
|`_Always_(anno_list)`|`anno_list _On_failure_(anno_list)`와 동일합니다. 즉, 함수 성공 여부에 관계없이 `anno_list`의 주석이 적용됩니다.|
|`_On_failure_(anno_list)`|함수에 주석을 달기 위해 `_Success_`가 사용될 경우에만 사용하려면 명시적으로 또는 typedef에서 `_Return_type_success_`를 통해 암시적으로 사용합니다 `_On_failure_` 주석이 함수 매개 변수 또는 반환 값에 제공되었으면, `anno_list`(anno)의 각 주석이 `_When_(!expr, anno)`로 코딩된 것처럼 작동합니다. 여기서 `expr`은 필요한 `_Success_` 주석에 대한 매개 변수입니다. 즉, 모든 사후 조건에 대한 `_Success_`의 암시적 적용이 `_On_failure_`에 대해 적용되지 않습니다.|
|`_Return_type_success_(expr)`|typedef에 적용될 수 있습니다. 해당 형식을 반환하고 명시적으로 `_Success_`를 포함하지 않는 모든 함수가 `_Success_(expr)`를 포함한 것처럼 주석을 달도록 지정합니다. `_Return_type_success_`는 함수 또는 함수 포인터 typedef에서 사용할 수 없습니다.|
|`_Success_(expr)`|`expr`은 값을 생성하는 식입니다. `_Success_` 주석이 함수 선언 또는 정의에 제공된 경우 함수 및 사전 조건의 각 주석(`anno`)은 `_When_(expr, anno)`으로 코딩된 것처럼 작동합니다. `_Success_` 주석은 해당 매개 변수 또는 반환 유형이 아닌 함수에서만 사용할 수 있습니다. 함수에는 최대한 하나의 `_Success_` 주석만 있을 수 있으며, `_When_`, `_At_` 또는 `_Group_`에는 있을 수 없습니다. 자세한 내용은 [주석이 적용 되는 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)을 참조 하세요.|

## <a name="see-also"></a>참고 항목

- [C/c + + 코드 오류를 줄이기 위해 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL 이해](../code-quality/understanding-sal.md)
- [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)
- [구조체 및 클래스에 주석 지정](../code-quality/annotating-structs-and-classes.md)
- [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)
- [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [내장 함수](../code-quality/intrinsic-functions.md)
- [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
