---
title: "Ref 클래스 및 구조체 (C + + /cli CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d8b7717c98ebd4bab8c0d3d8c20a594a3f4d58e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="ref-classes-and-structs-ccx"></a>Ref 클래스 및 구조체(C++/CX)
C + + /cli CX 지원 사용자 정의 *ref 클래스* 및 *ref 구조체*, 사용자 정의 및 *값 클래스* 및 *값 구조체*합니다. 이러한 데이터 구조는는 기본 컨테이너는 C + + /cli CX Windows 런타임 형식 시스템을 지원 합니다. 해당 콘텐츠는 특정 규칙에 따라 메타 데이터로 내보내집니다 및 c + + 또는 다른 언어로 작성 된 유니버설 Windows 플랫폼 앱 및 Windows 런타임 구성 요소 간에 전달 될 수 있도록 합니다.  
  
 ref 클래스 또는 ref 구조체에는 다음과 같은 중요한 기능이 있습니다.  
  
-   네임스페이스 안에서 선언되어야 하며, 네임스페이스 범위에 있어야 하며, 해당 네임스페이스에서 public 또는 private 액세스 가능성이 있을 수 있습니다. public 형식만 메타데이터로 내보내집니다. 중첩된 public [enum](../cppcx/enums-c-cx.md) 클래스를 포함하여 중첩된 public 클래스 정의는 허용되지 않습니다. 자세한 내용은 참조 [네임 스페이스 및 형식 표시 유형](../cppcx/namespaces-and-type-visibility-c-cx.md)합니다.  
  
-   C + 멤버를 포함할 수 있습니다 + CX ref 클래스, 값 클래스, ref 구조체, 값 구조체 또는 nullable 값 구조체를 포함 합니다. float64, bool 등의 스칼라 형식도 포함할 수 있습니다. 또한 `std::vector` 또는 사용자 지정 클래스(public이 아니어야 함)와 같은 표준 C++ 형식을 포함할 수 있습니다. C + + /CX 구문이 있을 수 `public`, `protected`, `internal`, `private`, 또는 `protected private` 내게 필요한 옵션입니다. 모든 `public` 또는 `protected` 멤버는 메타데이터로 내보내집니다. 표준 C++ 형식에는 메타데이터로 내보내지지 못하게 하는 `private`, `internal`또는 `protected private` 액세스 가능성이 있어야 합니다.  
  
-   하나 이상의 *인터페이스 클래스* 또는 *인터페이스 구조체*를 구현할 수 있습니다.  
  
-   한 기본 클래스에서 상속할 수 있으며 기본 클래스 자체에는 추가 제한이 있습니다. public ref 클래스 계층 구조의 상속에는 private ref 클래스의 상속보다 많은 제한이 있습니다.  
  
-   제네릭으로 선언될 수 없습니다. private 액세스 가능성이 있는 경우 템플릿일 수 있습니다.  
  
-   수명은 참조 횟수를 자동으로 계산하여 관리됩니다.  
  
## <a name="declaration"></a>선언  
 다음 코드 조각에서는 `Person` ref 클래스를 선언합니다. 표준 c + + `std::map` 전용 멤버 및 Windows Runtime에서 사용 되는`IMapView` 인터페이스는 공용 인터페이스에서 사용 됩니다. 또한 참조 형식 선언에 "^"가 추가되었습니다.  
  
 [!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]  
  
## <a name="implementation"></a>구현  
 이 코드 예제에서는 `Person` ref 클래스의 구현을 보여 줍니다.  
  
 [!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]  
  
## <a name="usage"></a>사용법  
 다음 코드 예제에서는 클라이언트 코드가 `Person` ref 클래스를 사용하는 방법을 보여 줍니다.  
  
 [!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]  
  
 또한 스택 의미 체계를 사용하여 지역 ref 클래스 변수를 선언할 수도 있습니다. 이러한 개체는 메모리가 계속 동적으로 할당되는 경우에도 스택 기반 변수처럼 동작합니다. 중요한 차이점은 스택 의미 체계로 선언된 변수에는 함수가 종료되면 참조 횟수가 0으로 감소하도록 보장하는 추적 참조(%)를 할당할 수 없다는 점입니다. 이 예제에서는 기본 ref 클래스 `Uri`및 스택 의미 체계에 이를 사용하는 함수를 보여 줍니다.  
  
 [!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]  
  
## <a name="memory-management"></a>메모리 관리  
 ref 클래스는 `ref new` 키워드를 사용하여 동적 메모리에 할당됩니다.  
  
 [!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]  
  
 개체 핸들 연산자 ^는 "해트"라고 하며 기본적으로 C++ 스마트 포인터입니다. 이것이 가리키는 메모리는 마지막 hat가 범위를 벗어나거나 명시적으로 `nullptr`로 설정되면 자동으로 제거됩니다.  
  
 정의에 따라 ref 클래스에는 참조 의미 체계가 있습니다. ref 클래스 변수를 할당할 경우 이는 개체 자체가 아니라 복사된 핸들입니다. 다음 예제에서 할당 후 `myClass` 및 `myClass2` 는 동일한 메모리 위치를 가리킵니다.  
  
 [!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]  
  
 C++/CX ref 클래스가 인스턴스화되면 생성자가 호출되기 전에 메모리가 0으로 초기화되므로 속성을 포함한 개별 멤버를 0으로 초기화할 필요가 없습니다. C++/CX 클래스가 WRL(Windows 런타임 C++ 라이브러리) 클래스에서 파생되는 경우 C++/CX 파생 클래스 부분만 0으로 초기화됩니다.  
  
### <a name="members"></a>멤버  
 ref 클래스에는 `public`, `protected`및 `private` 함수 멤버가 포함될 수 있습니다. `public` 및 `protected` 멤버만 메타데이터로 내보내집니다. 중첩 클래스 및 ref 클래스는 허용되지만 `public`일 수 없습니다. public 필드는 허용되지 않습니다. public 데이터 멤버는 속성으로 선언되어야 합니다. private 또는 protected internal 데이터 멤버는 필드가 될 수 있습니다. 기본적으로 ref 클래스에서 모든 멤버의 액세스 가능성은 `private`입니다.  
  
 ref 구조체는 기본적으로 멤버의 액세스 가능성이 `public` 이라는 점을 제외하고 ref 클래스와 동일합니다.  
  
 A `public` ref 클래스 또는 ref 구조체는 메타 데이터로 내보내집니다 하지만 다른 유니버설 Windows 플랫폼 앱 및 Windows 런타임 구성 요소에서 사용할 수 있으려면 public 또는 protected 생성자가 하나 이상 있어야 합니다. ABI(응용 프로그램 이진 인터페이스)를 통한 추가 파생을 방지하려면 public 생성자가 있는 public ref 클래스도 `sealed` 로 선언되어야 합니다.  
  
 공용 멤버 수 하지 const로 선언할 수 const로 Windows 런타임 형식 시스템에서 지원 하지 않으므로 합니다. 정적 속성을 사용하여 상수 값으로 public 데이터 멤버를 선언할 수 있습니다.  
  
 public ref 클래스 또는 구조체를 정의하는 경우 컴파일러가 클래스에 필수 특성을 적용하고 해당 정보를 응용 프로그램의 .winmd 파일에 저장합니다. 그러나 public unsealed ref 클래스를 정의할 때 수동으로 적용는 `Windows::Foundation::Metadata::WebHostHidden` 특성을 클래스가 JavaScript로 작성 된 유니버설 Windows 플랫폼 앱에 표시 되는지 확인 합니다.  
  
 ref 클래스의 `const` , `private`또는 `internal`멤버에는 `protected private` 형식을 포함한 표준 C++ 형식이 있을 수 있습니다.  
  
 형식 매개 변수가 있는 public ref 클래스는 허용되지 않습니다. 사용자 정의 제네릭 ref 클래스는 허용되지 않습니다. private, internal 또는 protected private ref 클래스는 템플릿일 수 있습니다.  
  
## <a name="destructors"></a>소멸자  
 C + + /CX에서는 호출 `delete` public 소멸자에 대해 개체의 참조 횟수에 관계 없이 소멸자를 호출 합니다. 이 동작을 통해 명확한 방식으로 비 RAII 리소스의 사용자 지정 정리를 수행하는 소멸자를 정의할 수 있습니다. 그러나 이 경우에도 개체 자체는 메모리에서 삭제되지 않습니다. 참조 횟수가 0에 도달할 때만 개체에 대한 메모리가 확보됩니다.  
  
 클래스의 소멸자가 public이 아닌 경우에는 참조 횟수가 0에 도달할 때만 소멸자가 호출됩니다. 호출 하는 경우 `delete` 컴파일러 private 소멸자가 있는 개체를에 경고 4493을 발생 시킵니다 "삭제 식은 효과가 없습니다 소멸자 \<유형 이름 > 'public' 액세스는 없습니다."  
  
 ref 클래스 소멸자는 다음과 같이 선언될 수만 있습니다.  
  
-   public 및 virtual(sealed 또는 unsealed 형식에서 허용됨)  
  
-   protected private 및 비가상(unsealed 형식에서만 허용됨)  
  
-   private 및 비가상(sealed 형식에서만 허용됨)  
  
 액세스 가능성, 가상 및 봉인의 다른 조합은 허용되지 않습니다.  소멸자를 명시적으로 선언하지 않으면 컴파일러가 형식의 기본 클래스 또는 멤버에 public 소멸자가 있는 경우 public virtual 소멸자를 생성하고, 그렇지 않으면 unsealed 형식의 경우 비가상 protected private 소멸자를 생성하고 sealed 형식의 경우 비가상 private 소멸자를 생성합니다.  
  
 이미 소멸자가 실행되도록 한 클래스의 멤버에 액세스하려고 하는 경우의 동작은 정의되어 있지 않습니다. 프로그램 작동이 중단될 가능성이 놓습니다. public 소멸자가 없는 형식에 대해 `delete t` 를 호출하면 아무런 효과가 없습니다. 형식 계층 구조 내에서 알려진 `delete this` 또는 `private` 소멸자가 있는 형식 또는 기본 클래스에 대해 `protected private` 를 호출해도 아무런 효과가 없습니다.  
  
 public 소멸자를 선언하는 경우 ref 클래스가 `Platform::IDisposable` 을 구현하고 소멸자가 `Dispose` 메서드를 구현하도록 컴파일러에서 코드가 생성됩니다. `Platform::IDisposable` C + + /CX 프로젝션의 `Windows::Foundation::IClosable`합니다. 이러한 인터페이스를 명시적으로 구현하지 마세요.  
  
## <a name="inheritance"></a>상속  
 Platform::Object는 모든 ref 클래스의 유니버설 기본 클래스입니다. 모든 ref 클래스는 암시적으로 Platform::Object로 변환될 수 있으며 [Object::ToString](../cppcx/platform-object-class.md#tostring)을 재정의할 수 있습니다. 그러나 Windows 런타임 상속 모델이 아니며 일반적으로 상속 모델; C + + /CX에서는 사용자 정의 public ref 클래스는 기본 클래스로 사용할 수 없습니다.  
  
 XAML 사용자 정의 컨트롤을 만들며 개체가 종속성 속성 시스템에 참여하는 경우에는 `Windows::UI::Xaml::DependencyObject` 를 기본 클래스로 사용할 수 있습니다.  
  
 `MyBase` 에서 상속하는 unsealed 클래스 `DependencyObject`를 정의한 후 구성 요소나 응용 프로그램의 다른 public 또는 private ref 클래스가 `MyBase`에서 상속할 수 있습니다. public ref 클래스의 상속은 가상 메서드의 재정의, 다형 ID 및 캡슐화를 지원하기 위해서만 수행되어야 합니다.  
  
 기본 private ref 클래스는 기존 unsealed 클래스에서 파생하는 데 필요하지 않습니다. 자체 프로그래밍 구조를 모델링하거나 코드 재사용을 가능하게 하기 위해 개체 계층 구조가 필요한 경우 private 또는 internal ref 클래스를 사용하거나 표준 C++ 클래스를 사용하세요. public sealed ref 클래스 래퍼를 통해 private 개체 계층 구조의 기능을 노출할 수 있습니다.  
  
 C + public 또는 protected 생성자가 있는 ref 클래스 + CX 선언 해야 합니다. sealed로 합니다. 이 제한 사항은 의미 C# 또는 Visual Basic에서 C + 작성 된 Windows 런타임 구성 요소에서 선언 하는 형식에서 상속할 수 등의 다른 언어로 작성 된 클래스에 대 한 + CX 합니다.  
  
 C + 상속에 대 한 기본 규칙은 + CX:  
  
-   ref 클래스가 직접 상속할 수 있는 기본 ref 클래스는 하나뿐이지만 구현할 수 있는 인터페이스의 개수에는 제한이 없습니다.  
  
-   public 생성자가 있는 클래스는 추가 파생을 방지하기 위해 sealed로 선언되어야 합니다.  
  
-   internal 또는 protected private 생성자가 있는 public unsealed 기본 클래스를 만들 수 있습니다. 단, 해당 기본 클래스가 `Windows::UI::Xaml::DependencyObject`와 같은 기존 unsealed 기본 클래스에서 직접 또는 간접적으로 파생되는 경우에 한합니다. .winmd 파일 전반에서 사용자 정의 ref 클래스의 상속은 지원되지 않지만 ref 클래스는 다른 .winmd 파일에서 정의된 인터페이스에서 상속할 수 있습니다. Windows 런타임 구성 요소를 동일한 또는 유니버설 Windows 플랫폼 앱 내 에서만 사용자 정의 기본 ref 클래스에서 파생 된 클래스를 만들 수 있습니다.  
  
-   ref 클래스의 경우 공용 상속만 지원됩니다.  
  
     [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]  
  
 다음 예제에서는 상속 계층 구조의 다른 ref 클래스에서 파생되는 public ref 클래스를 노출하는 방법을 보여 줍니다.  
  
 [!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]  
  
## <a name="see-also"></a>참고 항목  
 [형식 시스템](../cppcx/type-system-c-cx.md)   
 [값 클래스 및 구조체](../cppcx/value-classes-and-structs-c-cx.md)   
 [Visual c + + 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)   
 [네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)