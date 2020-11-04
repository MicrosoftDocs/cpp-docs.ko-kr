---
title: partial(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: 0f9de5dda1b0838a624431e579e6bc6b328d9013
ms.sourcegitcommit: d77159732a8e782b2a1b7abea552065f2b6f61c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344698"
---
# <a name="partial--ccli-and-ccx"></a>partial(C++/CLI 및 C++/CX)

**partial** 키워드를 사용하면 동일한 ref 클래스의 각 부분을 서로 다른 파일에서 독립적으로 작성할 수 있습니다.

## <a name="all-runtimes"></a>모든 런타임

이 언어 기능은 Windows 런타임에만 적용됩니다.

## <a name="windows-runtime"></a>Windows 런타임

두 개의 부분 정의가 포함 된 ref 클래스의 경우 **partial** 키워드는 처음 발견 되는 정의에 적용 되며,이는 일반적으로 자동 생성 된 코드에 의해 수행 되므로 사용자 코드 작성자 있는지 키워드를 매우 자주 사용 하지 않습니다. 클래스의 모든 후속 부분 정의에 대해, *class-key* 키워드 및 클래스 식별자에서 **partial** 한정자를 생략합니다. 컴파일러는 이전에 정의된 ref 클래스 및 클래스 식별자를 발견했지만 **partial** 키워드가 없는 경우 ref 클래스 정의의 모든 부분을 하나의 정의에 내부적으로 결합합니다.

### <a name="syntax"></a>구문

```cpp
partial class-key identifier {
   /* The first part of the partial class definition.
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>매개 변수

*class-key*<br/>
Windows 런타임에서 지원되는 클래스 또는 구조체를 선언하는 키워드입니다. **ref class** , **value class** , **ref struct** 또는 **value struct** 입니다.

*identifier*<br/>
정의된 형식의 이름입니다.

### <a name="remarks"></a>설명

partial 클래스는 한 파일에서 클래스 정의의 한 부분을 수정하면 자동 코드 생성 소프트웨어(예: XAML 디자이너)에서 다른 파일에 있는 동일한 클래스의 코드를 수정하는 시나리오를 지원합니다. partial 클래스를 사용하면 자동 코드 생성기에서 사용자 코드를 덮어쓰는 경우를 방지할 수 있습니다. Visual Studio 프로젝트에 생성된 파일에는 **partial** 한정자가 자동으로 적용됩니다.

내용: 두 가지 예외를 제외 **하 고 partial 키워드를** 생략 한 경우 전체 클래스 정의에 포함 될 수 있는 모든 항목을 부분 클래스 정의에 포함할 수 있습니다. 그러나 클래스 접근성(예: `public partial class X { ... };`) 또는 **declspec** 은 지정할 수 없습니다.

*identifier* 의 partial 클래스 정의에 사용된 액세스 지정자는 *identifier* 의 후속 부분 또는 전체 클래스 정의에 있는 기본 접근성에 영향을 주지 않습니다. 정적 데이터 멤버의 인라인 정의가 허용됩니다.

선언: 클래스 *식별자* 의 부분 정의에는 이름 *식별자* 만 도입 되지만 클래스 정의가 필요한 방식으로는 *식별자* 를 사용할 수 없습니다. 컴파일러에서 *identifier* 의 전체 정의를 발견할 때까지 이름 *identifier* 를 통해 *identifier* 의 크기를 확인하거나 *identifier* 의 기준 또는 멤버를 사용할 수 없습니다.

번호 및 순서 지정: *식별자* 에 대해 0 개 이상의 부분 클래스 정의가 있을 수 있습니다. *identifier* 의 모든 partial 클래스 정의는 *identifier* 의 전체 정의가 있을 경우 전체 정의보다 구문상 앞에 와야 하지만(전체 정의가 없으면 정방향 선언된 것처럼 사용하는 경우를 제외하고 클래스를 사용할 수 없음), *identifier* 의 정방향 선언보다 앞에 나올 필요는 없습니다. 모든 클래스 키가 일치해야 합니다.

전체 정의: 클래스 *식별자* 의 전체 정의 지점에서 *식별자* 의 정의가 모든 기본 클래스, 멤버 등을 partial 클래스에서 발견 되 고 정의 된 순서 대로 선언한 것과 동일한 동작입니다.

템플릿: partial 클래스는 템플릿이 될 수 없습니다.

제네릭: 전체 정의가 제네릭일 수 있는 경우 partial 클래스는 제네릭일 수 있습니다. 그러나 모든 partial 클래스와 전체 클래스에서 형식 매개 변수 이름을 포함한 제네릭 매개 변수가 정확히 같아야 합니다.

**partial** 키워드를 사용하는 방법에 대한 자세한 내용은 [partial 클래스(C++/CX)](../cppcx/partial-classes-c-cx.md)를 참조하세요.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

공용 언어 런타임에는 이 언어 기능이 적용되지 않습니다.

## <a name="see-also"></a>참고 항목

[Partial 클래스 (c + +/CX)](../cppcx/partial-classes-c-cx.md)
