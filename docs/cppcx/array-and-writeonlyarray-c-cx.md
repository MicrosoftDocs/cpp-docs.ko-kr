---
description: '자세히 알아보기: Array 및 WriteOnlyArray (c + +/CX)'
title: Array 및 WriteOnlyArray(C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: 4c4f9415f401f1180786608288e33691c82fbdfa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302792"
---
# <a name="array-and-writeonlyarray-ccx"></a>Array 및 WriteOnlyArray(C++/CX)

일반 C 스타일 배열 또는 [`std::array`](../standard-library/array-class-stl.md) c + +/cx 프로그램을 자유롭게 사용할 수 [`std::vector`](../standard-library/vector-class.md) 있지만 (일반적으로 더 나은 선택 이지만) 메타 데이터에 게시 된 모든 API에서는 C 스타일 배열이 나 벡터를 [`Platform::Array`](../cppcx/platform-array-class.md) [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) 사용 방식에 따라 또는 형식으로 변환 해야 합니다. [`Platform::Array`](../cppcx/platform-array-class.md)형식은 효율적이 지 않으며 강력 [`std::vector`](../standard-library/vector-class.md) 하지도 않으므로 배열 요소에 대해 많은 작업을 수행 하는 내부 코드에서 사용 하지 않는 것이 일반적입니다.

다음 배열 형식은 ABI 너머로 전달될 수 있습니다.

1. `const Platform::Array^`

1. `Platform::Array^*`

1. `Platform::WriteOnlyArray`

1. 반환 값 `Platform::Array^`

이러한 배열 형식을 사용 하 여 Windows 런타임에서 정의 된 세 가지 배열 패턴을 구현 합니다.

PassArray
호출자가 메서드에 배열을 전달할 때 사용됩니다. C + + 입력 매개 변수 형식은 **`const`** [`Platform::Array`](../cppcx/platform-array-class.md) \<T> 입니다.

FillArray
호출자가 메서드에서 채울 배열을 전달할 때 사용됩니다. C + + 입력 매개 변수 형식은 [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) \<T> 입니다.

ReceiveArray
호출자가 메서드가 할당하는 배열을 받을 때 사용됩니다. C++/CX에서는 반환 값에서 배열을 Array^로 반환하거나 Array^* 형식의 out 매개 변수로 반환할 수 있습니다.

## <a name="passarray-pattern"></a>PassArray 패턴

클라이언트 코드에서 c + + 메서드에 배열을 전달 하 고 메서드가 수정 하지 않는 경우이 메서드는 배열을로 받아들입니다 `const Array^` . ABI (Windows 런타임 응용 프로그램 이진 인터페이스) 수준에서이를 *PassArray* 이라고 합니다. 다음 예제에서는 JavaScript에서 할당된 배열을 이 배열을 읽는 C++ 함수에 전달하는 방법을 보여 줍니다.

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

다음 코드에서는 C++ 메서드를 보여 줍니다.

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>ReceiveArray 패턴

*ReceiveArray* 패턴에서 클라이언트 코드는 배열을 선언 하 고 해당 배열을 메모리를 할당 하 고 초기화 하는 메서드에 전달 합니다. C + + 입력 매개 변수 형식은 hat에 대 한 포인터입니다 `Array<T>^*` . 다음 예제에서는 JavaScript에서 배열 개체를 선언한 다음, 메모리를 할당하고 요소를 초기화하여 JavaScript에 반환하는 C++ 함수에 이 개체를 전달하는 방법을 보여 줍니다. JavaScript는 할당된 배열을 반환 값으로 처리하지만 C++ 함수는 이 배열을 출력 매개 변수로 처리합니다.

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

다음 코드에서는 C++ 메서드를 구현하는 두 가지 방법을 보여 줍니다.

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>배열 채우기

호출자에서 배열을 할당하고, 호출을 받는 메서드에서 배열을 초기화하거나 수정하려면 `WriteOnlyArray`를 사용합니다. 다음 예제에서는 `WriteOnlyArray` 를 사용하는 C++ 함수를 구현하고 JavaScript에서 이 함수를 호출하는 방법을 보여 줍니다.

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

다음 코드에서는 C++ 메서드를 구현하는 방법을 보여 줍니다.

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>배열 규칙

이 예제에서는를 사용 하 여 [`Platform::Array`](../cppcx/platform-array-class.md) 다른 종류의 컬렉션을 생성 하는 방법을 보여 줍니다.

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

다음 예제에서는 [`Platform::Array`](../cppcx/platform-array-class.md) C 스타일 배열에서를 생성 하 고 public 메서드에서 반환 하는 방법을 보여 줍니다.

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>가변 배열

Windows 런타임 형식 시스템에서는 가변 배열의 개념이 지원되지 않으므로 public 메서드에서 `IVector<Platform::Array<T>>` 를 반환 값 또는 메서드 매개 변수로 사용할 수 없습니다. ABI 전반에서 가변 배열 또는 시퀀스의 시퀀스를 전달하려면 `IVector<IVector<T>^>`를 사용합니다.

## <a name="use-arrayreference-to-avoid-copying-data"></a>ArrayReference를 사용하여 데이터 복사 방지

데이터가 ABI 전반에서로 전달 되 [`Platform::Array`](../cppcx/platform-array-class.md) 고 효율성을 위해 C 스타일 배열에서 해당 데이터를 처리 하려는 일부 시나리오에서는 [Platform:: arrayreference](../cppcx/platform-arrayreference-class.md) 를 사용 하 여 추가 복사 작업을 방지할 수 있습니다. 을 [`Platform::ArrayReference`](../cppcx/platform-arrayreference-class.md) 사용 하는 매개 변수에를 인수로 전달 하는 경우 `Platform::Array` 는 `ArrayReference` 사용자가 지정 하는 C 스타일 배열에 직접 데이터를 저장 합니다. `ArrayReference` 에는 소스 데이터에 대한 잠금이 없으므로 호출이 완료되기 전에 다른 스레드에서 해당 데이터가 수정되거나 삭제되는 경우 결과가 정의되지 않습니다.

다음 코드 조각에서는 작업의 결과를 [`DataReader`](/uwp/api/windows.storage.streams.datareader) `Platform::Array` (일반 패턴)에 복사한 다음를 대체 하 여 `ArrayReference` C 스타일 배열에 직접 데이터를 복사 하는 방법을 보여 줍니다.

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>속성으로 배열 노출 방지

일반적으로 ref 클래스에서는 `Platform::Array` 형식을 속성으로 노출하지 않아야 합니다. 클라이언트 코드가 단일 요소에만 액세스하려고 하는 경우에도 전체 배열이 반환되기 때문입니다. 공용 ref 클래스에서 시퀀스 컨테이너를 속성으로 노출 해야 하는 경우에는를 [`Windows::Foundation::IVector`](/uwp/api/windows.foundation.collections.ivector-1) 선택 하는 것이 좋습니다. 메타 데이터에 게시 되지 않은 전용 또는 내부 Api에서는와 같은 표준 c + + 컨테이너를 사용 하는 것이 좋습니다 [`std::vector`](../standard-library/vector-class.md) .

## <a name="see-also"></a>참고 항목

[유형 시스템](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
