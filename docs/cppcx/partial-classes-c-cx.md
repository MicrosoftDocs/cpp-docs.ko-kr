---
title: Partial 클래스(C++/CX)
description: C + +/CX에서 partial 클래스를 선언 하 고 사용 하는 방법
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 70225069c948a50b38ac3642113cf940c86cf8da
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609072"
---
# <a name="partial-classes-ccx"></a>Partial 클래스(C++/CX)

partial 클래스는 사용자가 클래스 정의의 한 부분을 수정할 때 자동 코드 생성 소프트웨어(예: XAML 디자이너)도 동일한 클래스의 코드를 수정하는 시나리오를 지원하는 생성자입니다. partial 클래스를 사용하면 디자이너가 코드를 덮어쓰지 않게 할 수 있습니다. Visual Studio 프로젝트에서 **`partial`** 한정자는 생성 된 파일에 자동으로 적용 됩니다.

## <a name="syntax"></a>구문

Partial 클래스를 정의 하려면 **`partial`** 클래스 키 바로 앞에 키워드를 사용 합니다. 그렇지 않으면 일반 클래스 정의가 됩니다. 와 같은 키워드는 **`partial ref class`** 공백 문자를 포함 하는 상황별 키워드입니다. 부분 정의는 다음 생성자에서 지원됩니다.

- **`class`** 또는 **`struct`**

- **`ref class`** 또는 **`ref struct`**

- **`value class`** 또는 **`value struct`**

- **`enum`** 또는 **`enum class`**

- **`ref interface`**, **`interface class`** , **`interface struct`** 또는 **`__interface`**

- **`union`**

이 예제에서는 부분을 보여 줍니다 **`ref class`** .

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>콘텐츠

Partial 클래스 정의는 키워드가 생략 된 경우 전체 클래스 정의에 포함 될 수 있는 모든 항목을 포함할 수 있습니다 **`partial`** . 여기에는 한 가지 경우를 제외하고, 기본 클래스, 데이터 멤버, 멤버 함수, 열거형, friend 선언 및 특성과 같은 모든 유효한 생성자가 포함됩니다. 정적 데이터 멤버의 인라인 정의가 허용됩니다.

한 가지 예외는 클래스 액세스 가능성입니다. 예를 들어 `public partial class MyInvalidClass {/* ... */};` 구문은 오류입니다. MyInvalidClass의 partial 클래스 정의에 사용되는 액세스 지정자는 MyInvalidClass의 후속 부분 또는 전체 클래스 정의의 기본 액세스 가능성에 영향을 미치지 않습니다.

다음 코드 조각에서 액세스 가능성을 보여 줍니다. 첫 번째 partial 클래스에서 `Method1` 은 액세스 가능성이 public이므로 공용입니다. 두 번째 partial 클래스에서 기본 클래스 액세스 가능성이 private이므로 `Method2` 는 전용입니다.

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>선언

와 같은 클래스의 부분 정의는 `MyClass` MyClass의 선언입니다. 즉, 이름만 소개 `MyClass` 합니다. `MyClass` 는 클래스 정의가 필요한 방식으로 사용할 수 없습니다. 예를 들어의 크기를 알고 `MyClass` 있거나의 기본 또는 멤버를 사용할 수 없습니다 `MyClass` . `MyClass` 는 컴파일러가의 부분 정의가 아닌 정의를 발견할 경우에만 정의 된 것으로 간주 됩니다 `MyClass` .

다음 예제에서는 partial 클래스의 선언 동작을 보여 줍니다. #1 선언 후에 `MyClass` 는를 전방 선언으로 작성 된 것 처럼 사용할 수 있습니다 `ref class MyClass;` . Declaration #2는 Declaration #1과 같습니다. Declaration #3은 클래스에 대한 정방향 선언이므로 유효합니다. 그러나 Declaration #4는

`MyClass`가 완전히 정의되지 않았으므로 유효하지 않습니다.

선언 #5 키워드를 사용 하지 않으며 **`partial`** 선언이 완전히 정의 `MyClass` 됩니다. 따라서 Declaration #6은 유효합니다.

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>번호 및 순서 지정

클래스의 모든 전체 정의에는 0개 이상의 부분 클래스 정의가 있을 수 있습니다.

클래스의 모든 부분 클래스 정의는 어휘 적으로 해당 클래스의 전체 정의 보다 앞에 나와야 하지만 클래스의 전방 선언 앞에 오지 않아도 됩니다. 클래스의 전체 정의가 없는 경우 부분 클래스 선언만 정방향 선언이 될 수 있습니다.

및와 같은 모든 클래스 키 **`class`** 가 **`struct`** 일치 해야 합니다. 예를 들어, `partial class X {}; struct X {};`만 생성합니다.

다음 예제에서는 번호 및 순서 지정을 보여 줍니다. 클래스가 이미 정의되어 있으므로 마지막 partial 선언은 실패합니다.

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>전체 정의

클래스 X의 전체 정의 지점에서는 X 정의가 모든 기본 클래스, 멤버 등을 partial 클래스에서 발견되고 정의된 순서대로 선언한 것처럼 동작이 동일합니다. 즉, partial 클래스의 내용은 클래스의 전체 정의 지점에 작성된 것처럼 처리되고, 이름 조회 및 다른 언어 규칙은 partial 클래스의 내용이 제자리에 작성된 것처럼 클래스의 전체 정의 지점에 적용됩니다.

다음의 두 코드 예제는 의미와 효과가 동일합니다. 첫 번째 예에서는 partial 클래스를 사용하고 두 번째 예에서는 그렇지 않습니다.

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>템플릿

partial 클래스는 템플릿이 될 수 없습니다.

## <a name="restrictions"></a>제한 사항

partial 클래스는 번역 단위를 벗어날 수 없습니다.

키워드는 **`partial`** **`ref class`** 키워드 또는 키워드와 함께 사용할 때만 지원 됩니다 **`value class`** .

### <a name="examples"></a>예제

다음 예제는 두 코드 파일에 걸쳐 `Address` 클래스를 정의합니다. 디자이너가 `Address.details.h` 를 수정하고 사용자가 `Address.h`를 수정합니다. 첫 번째 파일의 클래스 정의만 키워드를 사용 **`partial`** 합니다.

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>참고 항목

[유형 시스템](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
