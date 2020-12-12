---
description: '자세히 알아보기: 인터페이스 (c + +/CX)'
title: 인터페이스(C++/CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: 590b1b80ada186f90bfd38ed9dcdc8a35c34020f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320935"
---
# <a name="interfaces-ccx"></a>인터페이스(C++/CX)

ref 클래스가 상속할 수 있는 구체적 기본 클래스는 하나뿐이지만 구현할 수 있는 인터페이스 클래스의 개수에는 제한이 없습니다. 인터페이스 클래스(또는 인터페이스 구조체) 자체는 여러 인터페이스 클래스를 상속하거나 필요로 할 수 있고, 멤버 함수를 오버로드할 수 있으며, 형식 매개 변수를 사용할 수 있습니다.

## <a name="characteristics"></a>특징

인터페이스에는 다음과 같은 특징이 있습니다.

- 인터페이스 클래스(또는 구조체)는 네임스페이스 안에서 선언되어야 하며 public 또는 private 액세스 가능성이 있을 수 있습니다. public 인터페이스만 메타데이터로 내보내집니다.

- 인터페이스의 멤버에는 속성, 메서드 및 이벤트가 포함될 수 있습니다.

- 모든 인터페이스 멤버는 암시적으로 public 및 virtual입니다.

- 필드 및 정적 멤버는 허용되지 않습니다.

- 속성, 메서드 매개 변수 또는 반환 값으로 사용 되는 형식은 Windows 런타임 형식만 될 수 있습니다. 여기에는 기본 형식 및 열거형 클래스 형식이 포함 됩니다.

## <a name="declaration-and-usage"></a>선언과 사용법

다음 예제에서는 인터페이스를 선언하는 방법을 보여 줍니다. 인터페이스는 클래스나 구조체 형식으로 선언할 수 있습니다.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

인터페이스를 구현하기 위해 ref 클래스 또는 ref 구조체는 가상 메서드 및 속성을 선언하고 구현합니다. 인터페이스와 구현하는 ref 클래스는 다음 예제와 같이 동일한 메서드 매개 변수 이름을 사용해야 합니다.

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>인터페이스 상속 계층 구조

인터페이스는 하나 이상의 인터페이스에서 상속할 수 있습니다. 그러나 ref 클래스 또는 구조체와 달리 인터페이스는 상속된 인터페이스 멤버를 선언하지 않습니다. 인터페이스 B가 인터페이스 A에서 상속하고 ref 클래스 C가 B에서 상속하는 경우 C는 A와 B를 모두 구현해야 합니다. 이는 다음 예제에서 보여 줍니다.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>인터페이스 속성 및 이벤트 구현

이전 예에서 본 것처럼 간단한 가상 속성을 사용하여 인터페이스 속성을 구현할 수 있습니다. 또한 구현하는 클래스에 사용자 지정 getter 및 setter를 제공할 수도 있습니다.  getter와 setter는 모두 인터페이스 속성에서 공용이어야 합니다.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

인터페이스가 get-only 또는 set-only 속성을 선언하는 경우 구현하는 클래스가 getter 또는 setter를 명시적으로 제공해야 합니다.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

또한 구현하는 클래스의 이벤트에 대해 사용자 지정 add 및 remove 메서드를 구현할 수도 있습니다.

## <a name="explicit-interface-implementation"></a>명시적 인터페이스 구현

ref 클래스가 여러 인터페이스를 구현하고 이러한 인터페이스의 메서드들이 컴파일러에 동일한 이름과 시그니처를 갖고 있는 경우 다음 구문을 사용하여 클래스 메서드가 구현하고 있는 인터페이스 메서드를 명시적으로 나타낼 수 있습니다.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>제네릭 인터페이스

C + +/CX에서 **`generic`** 키워드는 매개 변수가 있는 Windows 런타임 형식을 나타내는 데 사용 됩니다. 매개 변수화된 형식은 메타데이터로 내보내지고 형식 매개 변수를 지원하는 임의의 언어로 작성된 코드에서 사용될 수 있습니다. Windows 런타임은 [Windows:: Foundation:: Collections:: IVector \<T> ](/uwp/api/windows.foundation.collections.ivector-1)와 같은 일부 제네릭 인터페이스를 정의 하지만 c + +/cx에서 공용 사용자 정의 제네릭 인터페이스 생성을 지원 하지 않습니다. 하지만 private 제네릭 인터페이스를 만들 수 있습니다.

Windows 런타임 형식을 사용 하 여 제네릭 인터페이스를 작성 하는 방법은 다음과 같습니다.

- 구성 요소에 정의 된 일반 사용자는 **`interface class`** 해당 Windows 메타 데이터 파일로 내보낼 수 없습니다. 따라서 공용 액세스 가능성을 가질 수 없으며 다른 winmd 파일의 클라이언트 코드도 구현할 수 없습니다. 이 클래스는 동일한 구성 요소의 public이 아닌 ref 클래스에서 구현될 수 있습니다. public ref 클래스는 제네릭 인터페이스 형식을 private 멤버로 사용할 수 있습니다.

   다음 코드 조각에서는 제네릭를 선언한 **`interface class`** 다음 private ref 클래스에서 구현 하 고 ref 클래스를 public ref 클래스에서 private 멤버로 사용 하는 방법을 보여 줍니다.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- 제네릭 인터페이스는 액세스 가능성, 멤버, *requires* 관계, 기본 클래스 등을 제어하는 표준 인터페이스 규칙을 따라야 합니다.

- 제네릭 인터페이스는 또는 앞에 있는 하나 이상의 제네릭 형식 매개 변수를 사용할 수 있습니다 **`typename`** **`class`** . 비형식 매개 변수는 지원되지 않습니다.

- 형식 매개 변수는 모든 Windows 런타임 형식일 수 있습니다. 즉, 형식 매개 변수는 참조 형식, 값 형식, 인터페이스 클래스, 대리자, 기본 형식 또는 public enum 클래스가 될 수 있습니다.

- *폐쇄형 제네릭 인터페이스* 는 일반 인터페이스에서 상속하고 모든 형식 매개 변수의 구체적인 형식 인수를 지정하는 인터페이스입니다. 제네릭이 아닌 private 인터페이스를 사용할 수 있는 모든 위치에서 사용할 수 있습니다.

- *개방형 제네릭 인터페이스* 는 구체적인 형식이 아직 제공되지 않은 하나 이상의 형식 매개 변수가 있는 인터페이스입니다. 형식을 사용할 수 있는 모든 위치에서 사용할 수 있습니다. 여기에는 다른 제네릭 인터페이스의 형식 인수로 사용하는 경우가 포함됩니다.

- 개별 메서드가 아니라 전체 인터페이스만 매개 변수화할 수 있습니다.

- 형식 매개 변수는 제한할 수 없습니다.

- 폐쇄형 제네릭 인터페이스에는 암시적으로 생성된 UUID가 있습니다. 사용자가 UUID를 지정할 수 없습니다.

- 인터페이스에서 메서드 매개 변수, 반환 값 또는 속성에 있는 현재 인터페이스에 대한 모든 참조는 현재 인스턴스화에 대한 참조로 간주됩니다. 예를 들어 *IMyIntf* 는 *IMyIntf \<T>* 를 의미 합니다.

- 메서드 매개 변수의 형식이 형식 매개 변수일 경우 해당 매개 변수 또는 변수 선언에 포인터, 네이티브 참조 또는 핸들 선언자 없이 형식 매개 변수의 이름이 사용됩니다. 따라서 "T^"를 작성할 필요가 없습니다.

- 템플릿 기반 ref 클래스는 private여야 하며, 제네릭 인터페이스를 구현할 수 있고 제네릭 인수 *t* 에 템플릿 매개 변수 *t* 를 전달할 수 있습니다. 템플릿 기반 ref 클래스의 각 인스턴스화는 자체 ref 클래스입니다.

## <a name="see-also"></a>참고 항목

[유형 시스템](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
