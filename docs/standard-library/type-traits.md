---
description: '다음에 대 한 자세한 정보: &lt; type_traits&gt;'
title: '&lt;type_traits&gt;'
ms.date: 02/21/2019
f1_keywords:
- <type_traits>
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
ms.openlocfilehash: cf7bb4a5bf73eb49526926c151ffbbd0b55fda5b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226495"
---
# <a name="lttype_traitsgt"></a>&lt;type_traits&gt;

형식 인수의 속성에 대 한 정보를 제공 하거나 변환 된 형식을 생성 하는 컴파일 시간 상수의 템플릿을 정의 합니다.

## <a name="syntax"></a>구문

```cpp
#include <type_traits>
```

## <a name="remarks"></a>설명

의 클래스 및 템플릿은 \<type_traits> 컴파일 시간에 형식 유추, 분류 및 변환을 지 원하는 데 사용 됩니다. 또한 형식 관련 오류를 감지 하 고 일반 코드를 최적화 하는 데 사용 됩니다. 단항 형식 특성은 형식의 속성을 설명 하 고, 이진 형식 특성은 형식 간의 관계를 설명 하며, 변환 특성은 형식의 속성을 수정 합니다.

도우미 클래스 `integral_constant` 와 해당 템플릿 특수화 `true_type` 및 `false_type` 형식 조건자의 기본 클래스를 구성 합니다. *형식 조건자* 는 형식 인수를 하나 이상 사용하는 템플릿입니다. 형식 조건자가 *true 이면* [true_type](../standard-library/type-traits-typedefs.md#true_type)에서 직접 또는 간접적으로 공개적으로 파생 됩니다. 형식 조건자가 *false* 이면 [false_type](../standard-library/type-traits-typedefs.md#false_type)에서 직접 또는 간접적으로 공개적으로 파생 됩니다.

*형식 한정자* 또는 *변환 특성* 은 템플릿 인수를 하나 이상 사용하며 수정된 형식과 동일한 의미인 단일 구성원(`type`)를 포함하는 템플릿입니다.

### <a name="alias-templates"></a>별칭 템플릿

형식 특성 식을 단순화 하기 위해에 대 한 [별칭 템플릿이](../cpp/aliases-and-typedefs-cpp.md) `typename some_trait<T>::type` 제공 됩니다. 여기서 *some_trait* 는 클래스 템플릿 이름입니다. 예를 들어 [add_const](../standard-library/add-const-class.md)에는 다음과 같이 정의된 `add_const_t` 형식에 대한 별칭 템플릿이 있습니다.

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

다음은 멤버에 대해 제공 되는 별칭입니다 `type` .

:::row:::
   :::column:::
      `add_const_t`\
      `add_cv_t`\
      `add_lvalue_reference_t`\
      `add_pointer_t`\
      `add_rvalue_reference_t`\
      `add_volatile_t`\
      `aligned_storage_t`\
      `aligned_union_t`\
   :::column-end:::
   :::column:::
      `common_type_t`\
      `conditional_t`\
      `decay_t`\
      `enable_if_t`\
      `invoke_result_t`\
      `make_signed_t`\
      `make_unsigned_t`\
      `remove_all_extents_t`\
   :::column-end:::
   :::column:::
      `remove_const_t`\
      `remove_cv_t`\
      `remove_extent_t`\
      `remove_pointer_t`\
      `remove_reference_t`\
      `remove_volatile_t`\
      `result_of_t`\
      `underlying_type_t`\
   :::column-end:::
:::row-end:::

### <a name="classes"></a>클래스

도우미 클래스 및 형식 정의

|Name|설명|
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|형식 및 값에서 정수 계열 상수를 만듭니다.|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|값이 true인 정수 상수를 보관합니다.|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|값이 false인 정수 상수를 보관합니다.|

기본 형식 범주

|Name|설명|
|-|-|
|[is_void](../standard-library/is-void-class.md)|형식이 인지 여부를 테스트 **`void`** 합니다.|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|형식이 `std::nullptr_t`인지 테스트합니다.|
|[is_integral](../standard-library/is-integral-class.md)|형식이 정수인지 테스트합니다.|
|[is_floating_point](../standard-library/is-floating-point-class.md)|형식이 부동 소수점인지 테스트합니다.|
|[is_array](../standard-library/is-array-class.md)|형식이 배열형인지 테스트합니다.|
|[is_pointer](../standard-library/is-pointer-class.md)|형식이 포인터인지 테스트합니다.|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|형식이 lvalue 참조인지 여부를 테스트합니다.|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|형식이 rvalue 참조인지 테스트합니다.|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|형식이 멤버 개체에 대한 포인터인지 테스트합니다.|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|형식이 멤버 함수에 대한 포인터인지 테스트합니다.|
|[is_enum](../standard-library/is-enum-class.md)|형식이 열거형인지 테스트합니다.|
|[is_union](../standard-library/is-union-class.md)|형식이 공용 구조체인지 테스트합니다.|
|[is_class](../standard-library/is-class-class.md)|형식이 클래스인지 테스트합니다.|
|[is_function](../standard-library/is-function-class.md)|형식이 함수 형식인지 테스트합니다.|

복합 형식 범주

|Name|설명|
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|형식이 참조인지 테스트합니다.|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|형식이 산술형인지 테스트합니다.|
|[is_fundamental](../standard-library/is-fundamental-class.md)|형식이 또는 산술 형식 인지 테스트 **`void`** 합니다.|
|[is_object](../standard-library/is-object-class.md)|형식이 개체 형식인지 테스트합니다.|
|[is_scalar](../standard-library/is-scalar-class.md)|형식이 스칼라 형식인지 테스트합니다.|
|[is_compound](../standard-library/is-compound-class.md)|형식이 스칼라가 아닌지 테스트합니다.|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|형식이 멤버에 대한 포인터인지 테스트합니다.|

형식 속성

|Name|설명|
|-|-|
|[is_const](../standard-library/is-const-class.md)|형식이 인지 여부를 테스트 **`const`** 합니다.|
|[is_volatile](../standard-library/is-volatile-class.md)|형식이 인지 여부를 테스트 **`volatile`** 합니다.|
|[is_trivial](../standard-library/is-trivial-class.md)|형식이 trivial인지 테스트합니다.|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|형식을 일반적으로 복사할 수 있는지 테스트합니다.|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|형식이 표준 레이아웃 형식인지 테스트합니다.|
|[is_pod](../standard-library/is-pod-class.md)|형식이 POD인지 테스트합니다.|
|[is_literal_type](../standard-library/is-literal-type-class.md)|형식이 **`constexpr`** 변수 이거나 함수에서 사용 될 수 있는지 여부를 테스트 **`constexpr`** 합니다.|
|[is_empty](../standard-library/is-empty-class.md)|형식이 빈 클래스인지 테스트합니다.|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|형식이 다형 클래스인지 테스트합니다.|
|[is_abstract](../standard-library/is-abstract-class.md)|형식이 추상 클래스인지 테스트합니다.|
|[is_final](../standard-library/is-final-class.md)|형식이 `final`로 표시된 클래스 종류인지 테스트합니다.|
|[is_aggregate](../standard-library/is-aggregate-class.md)||
|[is_signed](../standard-library/is-signed-class.md)|형식이 부호 있는 정수인지 테스트합니다.|
|[is_unsigned](../standard-library/is-unsigned-class.md)|형식이 부호가 없는 정수인지 테스트합니다.|
|[is_constructible](../standard-library/is-constructible-class.md)|형식이 지정된 인수 유형을 사용하여 생성 가능한지 테스트합니다.|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|형식에 기본 생성자가 있는지 테스트합니다.|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|형식에 복사 생성자가 있는지 테스트합니다.|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|형식에 이동 생성자가 있는지 테스트합니다.|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|첫 번째 형식에 두 번째 형식의 값을 할당할 수 있는지 테스트합니다.|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|형식에 해당 형식의 const 참조 값을 할당할 수 있는지 테스트합니다.|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|형식에 해당 형식의 rvalue 참조를 할당할 수 있는지 테스트합니다.|
|[is_swappable](../standard-library/type-traits-functions.md#is_swappable)||
|[is_swappable_with](../standard-library/type-traits-functions.md#is_swappable_with)||
|[is_destructible](../standard-library/is-destructible-class.md)|형식이 소멸 가능한지 테스트합니다.|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|지정된 형식을 사용하여 생성될 때 형식이 특수 작업을 사용하지 않는지 테스트합니다.|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|기본 생성될 때 형식이 특수 작업을 사용하지 않는지 테스트합니다.|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|복사를 통해 생성될 때 형식이 특수 작업을 사용하지 않는지 테스트합니다.|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|이동을 통해 생성될 때 형식이 특수 작업을 사용하지 않는지 테스트합니다.|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|형식이 할당 가능하며 할당에서 특수 작업을 사용하지 않는지 테스트합니다.|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|형식이 복사 할당 가능하며 할당에서 특수 작업을 사용하지 않는지 테스트합니다.|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|형식이 이동 할당 가능하며 할당에서 특수 작업을 사용하지 않는지 테스트합니다.|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|형식이 소멸 가능하며 소멸자가 특수 작업을 사용하지 않는지 테스트합니다.|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|형식이 생성 가능하며 지정된 형식을 사용하여 생성할 때 throw되지 않는 것으로 확인되는지 테스트합니다.|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|형식이 기본 생성 가능하며 기본 생성 시에 throw되지 않는 것으로 확인되는지 테스트합니다.|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|형식이 복사 생성 가능하며 복사 생성자가 throw되지 않는 것으로 확인되는지 테스트합니다.|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|형식이 이동 생성 가능하며 이동 생성자가 throw되지 않는 것으로 확인되는지 테스트합니다.|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|형식이 지정된 형식을 사용하여 할당 가능하며 할당이 throw되지 않는 것으로 확인되는지 테스트합니다.|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|형식이 복사 할당 가능하며 할당이 throw되지 않는 것으로 확인되는지 테스트합니다.|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|형식이 이동 할당 가능하며 할당이 throw되지 않는 것으로 확인되는지 테스트합니다.|
|[is_nothrow_swappable](../standard-library/type-traits-functions.md#is_nothrow_swappable)||
|[is_nothrow_swappable_with](../standard-library/type-traits-functions.md#is_nothrow_swappable_with)||
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|형식이 소멸 가능하며 소멸자가 throw되지 않는 것으로 확인되는지 테스트합니다.|
|`has_virtual_destructor`|형식에 가상 소멸자가 있는지 테스트합니다.|
|`has_unique_object_representations`||
| [is_invocable](is-invocable-classes.md) | 지정 된 인수 형식을 사용 하 여 호출 가능 형식이 호출 될 수 있는지 여부를 테스트 합니다.<br/> C + + 17에 추가 되었습니다. |
| [is_invocable_r](is-invocable-classes.md) | 지정 된 인수 형식을 사용 하 여 호출 가능 형식이 호출 될 수 있는지 여부를 테스트 하 고 결과를 지정 된 형식으로 변환할 수 있는지 여부를 테스트 합니다.<br/> C + + 17에 추가 되었습니다. |
| [is_nothrow_invocable](is-invocable-classes.md) | 지정 된 인수 형식을 사용 하 여 호출 가능 형식이 호출 될 수 있는지 여부를 테스트 하 고 예외를 throw 하지 않도록 합니다.<br/> C + + 17에 추가 되었습니다. |
| [is_nothrow_invocable_r](is-invocable-classes.md) | 지정 된 인수 형식을 사용 하 여 호출 가능 형식이 호출 될 수 있는지 여부를 테스트 하 고, 예외를 throw 하지 않고 결과를 지정 된 형식으로 변환할 수 있는지 여부를 테스트 합니다.<br/> C + + 17에 추가 되었습니다. |

형식 속성 쿼리

|Name|설명|
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|형식의 맞춤을 가져옵니다.|
|[배열](../standard-library/rank-class.md)|배열 차원 수를 가져옵니다.|
|[됨으로써](../standard-library/extent-class.md)|지정된 배열 차원에서 요소의 수를 가져옵니다.|

형식 관계

|Name|설명|
|-|-|
|[is_same](../standard-library/is-same-class.md)|두 형식이 동일한지 테스트합니다.|
|[is_base_of](../standard-library/is-base-of-class.md)|한 형식이 다른 형식의 기본 형식인지를 테스트합니다.|
|[is_convertible](../standard-library/is-convertible-class.md)|한 가지 형식을 다른 형식으로 변환할 수 있는지 테스트합니다.|

const-volatile 수정

|Name|설명|
|-|-|
|[add_const](../standard-library/add-const-class.md)|**`const`** 형식에서 형식을 생성 합니다.|
|[add_volatile](../standard-library/add-volatile-class.md)|**`volatile`** 형식에서 형식을 생성 합니다.|
|[add_cv](../standard-library/add-cv-class.md)|**`const volatile`** 형식에서 형식을 생성 합니다.|
|[remove_const](../standard-library/remove-const-class.md)|형식에서 비const 형식을 생성합니다.|
|[remove_volatile](../standard-library/remove-volatile-class.md)|형식에서 비volatile 형식을 생성합니다.|
|[remove_cv](../standard-library/remove-cv-class.md)|형식에서 비const/비volatile 형식을 생성합니다.|

참조 수정

|Name|설명|
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|형식에서 형식에 대한 참조를 생성합니다.|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|형식에서 형식에 대한 rvalue 참조를 생성합니다.|
|[remove_reference](../standard-library/remove-reference-class.md)|형식에서 비참조 형식을 생성합니다.|

부호 수정

|Name|설명|
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|부호가 있는 경우 형식을 생성하거나, 형식의 크기보다 크거나 같은 부호가 있는 가장 작은 형식을 생성합니다.|
|[make_unsigned](../standard-library/make-unsigned-class.md)|부호가 없는 경우 형식을 생성하거나, 형식의 크기보다 크거나 같은 부호가 없는 가장 작은 형식을 생성합니다.|

배열 수정

|Name|설명|
|-|-|
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|배열 형식에서 배열이 아닌 형식을 생성합니다.|
|[remove_extent](../standard-library/remove-extent-class.md)|배열 형식에서 요소 형식을 생성합니다.|

포인터 수정

|Name|설명|
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|형식에서 형식에 대한 포인터를 생성합니다.|
|[remove_pointer](../standard-library/remove-pointer-class.md)|입력에 대한 포인터에서 형식을 생성합니다.|

기타 변환

|Name|설명|
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|정렬된 형식에 대해 초기화되지 않은 메모리를 할당합니다.|
|[aligned_union](../standard-library/aligned-union-class.md)|특수한 생성자 또는 소멸자를 사용하여 정렬된 공용 구조체에 대해 초기화되지 않은 메모리를 할당합니다.|
|[common_type](../standard-library/common-type-class.md)|모든 매개 변수 팩 형식의 공통 형식을 생성합니다.|
|[defined](../standard-library/conditional-class.md)|조건이 true이면 지정된 첫 번째 형식을 생성하고 그렇지 않으면 지정된 두 번째 형식을 생성합니다.|
|[decay](../standard-library/decay-class.md)|값으로 전달된 형식을 생성합니다. 비참조, 비상수, 비휘발성 형식 또는 형식에 대한 포인터를 만듭니다.|
|[enable_if](../standard-library/enable-if-class.md)|조건이 true이면 지정된 형식을 생성하고 그렇지 않으면 형식을 생성하지 않습니다.|
|[invoke_result](invoke-result-class.md)|지정된 인수 유형을 사용하는 호출 가능 형식의 반환 형식을 결정합니다. <br/>C + + 17에 추가 되었습니다. |
|[result_of](../standard-library/result-of-class.md)|지정된 인수 유형을 사용하는 호출 가능 형식의 반환 형식을 결정합니다. <br/>C + + 14에서 추가 되었고, c + + 17에서 사용 되지 않습니다. |
|[underlying_type](../standard-library/underlying-type-class.md)|열거형 형식에 대한 내부 정수 계열 형식을 생성합니다.|

논리 연산자 특성

|Name|설명|
|-|-|
|[논리곱](../standard-library/conjunction-class.md)||
|[논리합](../standard-library/disjunction-class.md)||
|[음의](../standard-library/negation-class.md)||

## <a name="see-also"></a>참고 항목

[\<functional>](../standard-library/functional.md)
