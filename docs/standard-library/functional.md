---
description: '자세한 정보: &lt; 기능&gt;'
title: '&lt;functional&gt;'
ms.date: 02/21/2019
f1_keywords:
- <functional>
- functional/std::<functional>
- std::<functional>
helpviewer_keywords:
- functors
- functional header
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
ms.openlocfilehash: a13ddeb7bdb45b02bb8b35052e34a3b9601c6fec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232150"
---
# <a name="ltfunctionalgt"></a>&lt;functional&gt;

*함수 개체*( *함수* 라고도 함) 및 해당 바인더를 생성 하는 데 도움이 되는 c + + 표준 라이브러리 함수를 정의 합니다. 함수 개체는 `operator()`를 정의하는 형식의 개체입니다. 함수 개체는 함수 포인터일 수 있지만, 개체를 사용하여 함수 호출 중에 액세스할 수 있는 추가 정보를 저장하는 것이 더 일반적입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<functional>

**네임스페이스:** std

## <a name="remarks"></a>설명

알고리즘에는 *단항* 및 *binary* 의 두 가지 함수 개체 형식이 필요 합니다. 단항 함수 개체에는 인수가 하나 필요하고 이항 함수 개체에는 인수가 두 개 필요합니다. 함수 개체 및 함수 포인터는 알고리즘 조건자로 전달할 수 있지만 함수 개체는 조정 가능하며 C++ 표준 라이브러리의 범위, 유연성 및 효율성을 높입니다. 예를 들어 값이 알고리즘에 전달되기 전에 함수에 바인딩되어야 하는 경우 함수 포인터를 사용할 수 없습니다. 함수 어댑터는 함수 포인터를 값에 바인딩될 수 있는 조정 가능한 함수 개체로 변환합니다. 헤더에 \<functional> 는 멤버 함수를 융통성 있는 함수 개체로 호출할 수 있도록 하는 멤버 함수 어댑터도 포함 되어 있습니다. 함수는 해당 인수 및 반환 형식을 지정하는 중첩 형식 선언을 포함하는 경우 조정 가능합니다. 함수 개체와 해당 어댑터는 C++ 표준 라이브러리가 기존 애플리케이션을 업그레이드할 수 있도록 하며 라이브러리를 C++ 프로그래밍 환경으로 통합하는 데 도움이 됩니다.

에서 함수 개체의 구현에는 \<functional> *투명 연산자 함수* 가 포함 됩니다. 표준 함수 개체의 특수화 이며 템플릿 매개 변수를 사용 하지 않고 함수 인수의 완벽 한 전달 및 결과의 완벽 한 반환을 수행 합니다. 이러한 템플릿 특수화는 산술, 비교, 논리 및 비트 연산자 함수를 호출할 때 인수 형식을 지정할 필요가 없습니다. 사용자 고유의 형식 또는 다른 유형의 형식 조합에 대해 산술, 비교, 논리 또는 비트 연산자를 오버로드할 수 있으며 투명 연산자 함수를 함수 인수로 사용할 수 있습니다. 예를 들어 *MyType* 형식이 `operator<`를 구현하는 경우 `sort(my_collection.begin(), my_collection.end(), less<MyType>())` 형식을 명시적으로 지정하는 대신 `sort(my_collection.begin(), my_collection.end(), less<>())`를 호출할 수 있습니다.

C + + 11, c + + 14 및 c + + 17에 추가 된 기능은 다음과 같습니다.

- *호출 시그니처* 는 반환 형식의 이름 및 0개 이상 인수 형식의 괄호로 묶인 쉼표로 구분된 목록입니다.

- *호출 가능 형식* 은 함수에 대한 포인터, 멤버 함수에 대한 포인터, 멤버 데이터에 대한 포인터 또는 개체가 함수 호출 연산자 바로 왼쪽에 표시될 수 있는 클래스 형식입니다.

- *호출 가능 개체* 는 호출 가능 형식의 개체입니다.

- *호출 래퍼 형식* 은 호출 가능 개체를 보유하고 해당 개체에 전달하는 호출 작업을 지원하는 형식입니다.

- *호출 래퍼* 는 호출 래퍼 형식의 개체입니다.

- *대상 개체* 는 호출 래퍼 개체가 보유한 호출 가능 개체입니다.

의사(pseudo) 함수 `INVOKE(f, t1, t2, ..., tN)`은 다음 중 하나를 의미합니다.

- `f`가 `T` 클래스의 멤버 함수에 대한 포인터이고, `t1`이 `T` 형식의 개체이거나 `T` 형식의 개체에 대한 참조 또는 `T`에서 파생된 형식의 개체에 대한 참조인 경우 `(t1.*f)(t2, ..., tN)`입니다.

- `f`가 `T` 클래스의 멤버 함수에 대한 포인터이고 `t1`이 이전 항목에서 설명한 형식 중 하나가 아닌 경우 `((*t1).*f)(t2, ..., tN)`입니다.

- N == 1이며 `f`가 `T` 클래스의 멤버 데이터에 대한 포인터이고, `t1`이 `T` 형식의 개체이거나 `T` 형식의 개체에 대한 참조 또는 `T`에서 파생된 형식의 개체에 대한 참조인 경우 `t1.*f`입니다.

- N == 1이며 `f`가 `T` 클래스의 멤버 데이터에 대한 포인터이고 `t1`이 이전 항목에서 설명한 형식 중 하나가 아닌 경우 `(*t1).*f`입니다.

- 다른 모든 경우에는 `f(t1, t2, ..., tN)`.

의사(pseudo) 함수 `INVOKE(f, t1, t2, ..., tN, R)`은 `INVOKE(f, t1, t2, ..., tN)`이 `R`로 암시적으로 변환되었음을 의미합니다.

호출 래퍼에 *약한 결과 형식* 이 있는 경우 해당 멤버 형식 `result_type`의 형식은 다음과 같이 래퍼 대상 개체의 `T` 형식을 기반으로 합니다.

- `T`가 함수에 대한 포인터인 경우 `result_type`은 `T`의 반환 형식에 대한 동의어입니다.

- `T`가 멤버 함수에 대한 포인터인 경우 `result_type`은 `T`의 반환 형식에 대한 동의어입니다.

- `T`가 멤버 형식 `result_type`을 포함하는 클래스 형식인 경우 `result_type`은 `T::result_type`에 대한 동의어입니다.

- 그렇지 않은 경우 멤버 `result_type`이 없습니다.

각 호출 래퍼에 이동 생성자 및 복사 생성자가 있습니다. *단순 호출 래퍼* 는 대입 연산자가 있고 해당 복사 생성자, 이동 생성자 및 대입 연산자에서 예외가 발생하지 않는 호출 래퍼입니다. *전달 호출 래퍼* 는 임의의 인수 목록을 사용하여 호출할 수 있고 래핑된 호출 가능 개체에 인수를 참조로 전달하는 호출 래퍼입니다. 모든 rvalue 인수는 rvalue 참조로 전달되고 lvalue 인수는 lvalue 참조로 전달됩니다.

## <a name="members"></a>멤버

### <a name="classes"></a>클래스

|이름|설명|
|-|-|
|[bad_function_call](../standard-library/bad-function-call-class.md)|개체가 비어 있어서 [function](../standard-library/function-class.md) 개체에 대한 `operator()` 호출이 실패했음을 나타내기 위해 발생한 예외를 설명하는 클래스입니다.|
|[binary_negate](../standard-library/binary-negate-class.md)|지정 된 이항 함수의 반환 값을 부정 하는 멤버 함수를 제공 하는 클래스 템플릿입니다.<br/> C + + 17에서 사용 되지 않습니다. |
|[binder1st](../standard-library/binder1st-class.md)|이항 함수의 첫 번째 인수를 지정 된 값에 바인딩하여 이항 함수 개체를 단항 함수 개체로 변환 하는 생성자를 제공 하는 클래스 템플릿입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[binder2nd](../standard-library/binder2nd-class.md)|이항 함수의 두 번째 인수를 지정 된 값에 바인딩하여 이항 함수 개체를 단항 함수 개체로 변환 하는 생성자를 제공 하는 클래스 템플릿입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[boyer_moore_horspool_searcher](../standard-library/boyer-moore-horspool-searcher-class.md)||
|[boyer_moore_searcher](../standard-library/boyer-moore-searcher-class.md)||
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|참조 인수를 사용하여 초기화할 때 인수를 사용하지 않는 const 멤버 함수를 단항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|포인터 인수를 사용하여 초기화할 때 인수를 사용하지 않는 const 멤버 함수를 단항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|참조 인수를 사용하여 초기화할 때 단일 인수를 사용하는 const 멤버 함수를 이항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|포인터 인수를 사용하여 초기화할 때 단일 인수를 사용하는 const 멤버 함수를 이항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[default_searcher](../standard-library/default-searcher-class.md)||
|[function](../standard-library/function-class.md)|호출 가능 개체를 래핑하는 클래스입니다.|
|[hash](../standard-library/hash-class.md)|값에 대한 해시 코드를 계산하는 클래스입니다.|
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|`bind`를 호출하여 특정 형식이 생성되었는지 테스트하는 클래스입니다.|
|[is_placeholder](../standard-library/is-placeholder-class.md)|특정 형식이 자리 표시자인지 테스트하는 클래스입니다.|
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|`non_const`참조 인수를 사용 하 여 초기화할 때 인수를 사용 하지 않는 멤버 함수를 단항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|`non_const`포인터 인수를 사용 하 여 초기화할 때 인수를 사용 하지 않는 멤버 함수를 단항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|`non_const`참조 인수를 사용 하 여 초기화할 때 단일 인수를 사용 하는 멤버 함수를 이항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|`non_const`포인터 인수를 사용 하 여 초기화할 때 단일 인수를 사용 하는 멤버 함수를 이항 함수 개체로 호출할 수 있도록 하는 어댑터 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|이항 함수 포인터를 조정 가능한 이항 함수로 변환합니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|단항 함수 포인터를 조정 가능한 단항 함수로 변환합니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[reference_wrapper](../standard-library/reference-wrapper-class.md)|참조를 래핑하는 클래스입니다.|
|[unary_negate](../standard-library/unary-negate-class.md)|지정 된 단항 함수의 반환 값을 부정 하는 멤버 함수를 제공 하는 클래스 템플릿입니다.<br/> C + + 17에서 사용 되지 않습니다.  |

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[bind](../standard-library/functional-functions.md#bind)|호출 가능 개체에 인수를 바인딩합니다.|
|[bind1st](../standard-library/functional-functions.md#bind1st)|이항 함수의 첫 번째 인수를 지정된 값에 바인딩하여 이항 함수 개체를 단항 함수 개체로 변환하는 어댑터를 만드는 도우미 템플릿 함수입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[bind2nd](../standard-library/functional-functions.md#bind2nd)|이항 함수의 두 번째 인수를 지정된 값에 바인딩하여 이항 함수 개체를 단항 함수 개체로 변환하는 어댑터를 만드는 도우미 템플릿 함수입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[bit_and](../standard-library/functional-functions.md#bit_and)|두 매개 변수의 비트 논리적 AND(binary operator&)를 반환합니다.|
|[bit_not](../standard-library/functional-functions.md#bit_not)|매개 변수의 비트 논리적 보수(operator~)를 반환합니다.<br/> C + + 14에서 추가 되었습니다. |
|[bit_or](../standard-library/functional-functions.md#bit_or)|두 매개 변수의 비트 논리적 OR(operator&#124;)를 반환합니다.|
|[bit_xor](../standard-library/functional-functions.md#bit_xor)|두 매개 변수의 비트 논리적 XOR(operator^)을 반환합니다.|
|[cref](../standard-library/functional-functions.md#cref)|인수에서 const `reference_wrapper`를 생성합니다.|
|[invoke](../standard-library/functional-functions.md#invoke)||
|[mem_fn](../standard-library/functional-functions.md#mem_fn)|단순 호출 래퍼를 생성합니다.|
|[mem_fun](../standard-library/functional-functions.md#mem_fun)|포인터 인수를 사용하여 초기화할 때 멤버 함수에 대한 함수 개체 어댑터를 생성하는 데 사용되는 도우미 템플릿 함수입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)|참조 인수를 사용하여 초기화할 때 멤버 함수에 대한 함수 개체 어댑터를 생성하는 데 사용되는 도우미 템플릿 함수입니다.|
|[not1](../standard-library/functional-functions.md#not1)|단항 조건자의 보수를 반환합니다.<br/> C + + 17에서 사용 되지 않습니다. |
|[not2](../standard-library/functional-functions.md#not2)|이항 조건자의 보수를 반환합니다.<br/> C + + 17에서 사용 되지 않습니다. |
|[not_fn](../standard-library/functional-functions.md#not_fn)|함수 개체의 결과에 대 한 보수를 반환 합니다.<br/> (C + + 17에서 추가 됨) |
|[ptr_fun](../standard-library/functional-functions.md#ptr_fun)|단항 및 이항 함수 포인터를 각각 조정 가능한 단항 및 이항 함수로 변환하는 데 사용되는 도우미 템플릿 함수입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[ref](../standard-library/functional-functions.md#ref)|인수에서 `reference_wrapper` 를 생성합니다.|
|[스왑을](../standard-library/functional-functions.md#swap)|두 `function` 개체를 교환합니다.|

### <a name="structs"></a>구조체

|Name|설명|
|-|-|
|[binary_function](../standard-library/binary-function-struct.md)|이항 함수 개체를 제공하는 파생 클래스에 상속될 수 있는 형식을 정의하는 빈 기본 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |
|[divides](../standard-library/divides-struct.md)|클래스는 지정된 값 형식의 요소에 대해 나누기 산술 연산을 수행하는 미리 정의된 함수 개체를 제공합니다.|
|[equal_to](../standard-library/equal-to-struct.md)|지정된 형식의 값이 해당 형식의 다른 값과 같은지 테스트하는 이항 조건자입니다.|
|[greater](../standard-library/greater-struct.md)|지정된 형식의 값이 해당 형식의 다른 값보다 큰지 테스트하는 이항 조건자입니다.|
|[greater_equal](../standard-library/greater-equal-struct.md)|지정된 형식의 값이 해당 형식의 다른 값보다 크거나 같은지 테스트하는 이항 조건자입니다.|
|[less](../standard-library/less-struct.md)|지정된 형식의 값이 해당 형식의 다른 값보다 작은지 테스트하는 이항 조건자입니다.|
|[less_equal](../standard-library/less-equal-struct.md)|지정된 형식의 값이 해당 형식의 다른 값보다 작거나 같은지 테스트하는 이항 조건자입니다.|
|[logical_and](../standard-library/logical-and-struct.md)|이 클래스는 지정된 값 형식의 요소에 대해 논리곱 논리 연산을 수행하고 결과가 참 또는 거짓인지 테스트하는 미리 정의된 함수 개체를 제공합니다.|
|[logical_not](../standard-library/logical-not-struct.md)|이 클래스는 지정된 값 형식의 요소에 대해 부정 논리 연산을 수행하고 결과가 참 또는 거짓인지 테스트하는 미리 정의된 함수 개체를 제공합니다.|
|[logical_or](../standard-library/logical-or-struct.md)|이 클래스는 지정된 값 형식의 요소에 대해 분리 논리 연산을 수행하고 결과가 참 또는 거짓인지 테스트하는 미리 정의된 함수 개체를 제공합니다.|
|[minus](../standard-library/minus-struct.md)|이 클래스는 지정된 값 형식의 요소에 대해 빼기 산술 연산을 수행하는 미리 정의된 함수 개체를 제공합니다.|
|[T:System.Security.Cryptography.RSA](../standard-library/modulus-struct.md)|이 클래스는 지정된 값 형식의 요소에 대해 모듈러스 산술 연산을 수행하는 미리 정의된 함수 개체를 제공합니다.|
|[multiplies](../standard-library/multiplies-struct.md)|이 클래스는 지정된 값 형식의 요소에 대해 곱하기 산술 연산을 수행하는 미리 정의된 함수 개체를 제공합니다.|
|[negate](../standard-library/negate-struct.md)|이 클래스는 요소 값의 부정을 반환하는 미리 정의된 함수 개체를 제공합니다.|
|[not_equal_to](../standard-library/not-equal-to-struct.md)|지정된 형식의 값이 해당 형식의 다른 값과 같지 않은지 테스트하는 이항 조건자입니다.|
|[항목과](../standard-library/plus-struct.md)|클래스는 지정된 값 형식의 요소에 대해 더하기 산술 연산을 수행하는 미리 정의된 함수 개체를 제공합니다.|
|[unary_function](../standard-library/unary-function-struct.md)|단항 함수 개체를 제공하는 파생 클래스에 상속될 수 있는 형식을 정의하는 빈 기본 클래스입니다.<br/> C + + 11에서 사용 되지 않으며 c + + 17에서 제거 되었습니다. |

### <a name="objects"></a>개체

|Name|설명|
|-|-|
|[_1.._M](../standard-library/1-object.md)|대체 가능한 인수에 대한 자리 표시자입니다.|

### <a name="operators"></a>연산자

|Name|설명|
|-|-|
|[연산자 = =](../standard-library/functional-operators.md#op_eq_eq)|호출 가능 개체의 같음 비교를 허용하지 않습니다.|
|[연산자! =](../standard-library/functional-operators.md#op_neq)|호출 가능 개체의 같지 않음 비교를 허용하지 않습니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
