---
title: 캐스팅 (C + + /cli CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71be537ecc0dc0cb58a3ada13612dbe8cbd7d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="casting-ccx"></a>캐스팅(C++/CX)
Windows 런타임 형식에 적용 된 네 가지 캐스트 연산자: [static_cast 연산자](../cpp/static-cast-operator.md), [dynamic_cast Operator](../cpp/dynamic-cast-operator.md), **safe_cast Operator**, 및 [ reinterpret_cast 연산자](../cpp/reinterpret-cast-operator.md)합니다. `safe_cast` 및 `static_cast` 는 변환이 수행될 수 없을 때 예외를 throw합니다. [static_cast 연산자](../cpp/static-cast-operator.md) 도 컴파일 타임 형식 검사를 수행합니다. `dynamic_cast` 는 형식을 변환하지 못할 경우 `nullptr` 을 반환합니다. `reinterpret_cast` 는 null이 아닌 값을 반환하지만 이는 잘못되었을 수 있습니다. 따라서 캐스팅이 성공할지 여부를 모른다면 `reinterpret_cast` 를 사용하지 않는 것이 좋습니다. 또한 좋습니다 사용 하는 C 스타일 캐스트 C + + /cli CX 동일 하기 때문에 코드 `reinterpret_cast`합니다.  
  
 또한 컴파일러와 런타임은 암시적 캐스트를 수행합니다. 예를 들어, 매개 변수 형식이 `Object^`인 메서드에 값 형식 또는 기본 제공 형식이 인수로 전달될 때 boxing 연산에서 암시적 캐스트를 수행합니다. 이론적으로 런타임에는 암시적 캐스트로 인해 예외가 발생하지 않습니다. 컴파일러가 암시적 변환을 수행할 수 없는 경우 컴파일 시 오류가 발생합니다.  
  
Windows Runtime 예외 대신 HRESULT 오류 코드를 사용 하는 COM을 통한 추상화입니다. 일반적으로 [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) 은 E_NOINTERFACE의 하위 수준 COM 오류를 나타냅니다.  
  
## <a name="staticcast"></a>static_cast  
 컴파일 시 `static_cast` 검사를 통해 두 형식 간에 상속 관계가 있는지 여부를 확인합니다. 형식이 관련되지 않은 경우 컴파일러 오류가 발생합니다.  
  
 ref 클래스의 `static_cast` 에 의해서도 런타임 검사가 수행됩니다. ref 클래스의 `static_cast` 가 컴파일 타임 확인을 통과할 수 있지만 런타임에는 여전히 실패합니다. 이 경우 `Platform::InvalidCastException` 이 throw됩니다. 대개 이러한 예외는 거의 항상 개발 및 테스트 중에 제거할 수 있는 프로그래밍 오류를 나타내기 때문에 무시해도 됩니다.  
  
 코드에서 두 형식 간의 관계를 명시적으로 선언하고 그에 따라 캐스팅이 확실히 작동하는 경우 `static_cast` 를 사용합니다.  
  
```
    interface class A{};  
    public ref class Class1 sealed : A { };  
...  
    A^ obj = ref new Class1(); // Class1 is an A  
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.  
    Class1^ c = static_cast<Class1^>(obj);
```  
  
## <a name="safecast"></a>safe_cast  
 `safe_cast` 연산자가 일부 ofWindows 런타임. 변환에 실패하는 경우 런타임 형식 검사를 수행하고 `Platform::InvalidCastException` 을 throw합니다. 런타임 오류가 예외 상황을 나타낼 때는 `safe_cast` 를 사용하세요. `safe_cast` 의 주요 용도는 개발 및 테스트 단계에서 발생하는 프로그래밍 오류를 바로 식별하는 것입니다. 처리되지 않은 예외가 오류 발생 시점을 나타내므로 예외를 처리할 필요가 없습니다.  
  
 코드에서 관계를 선언하지는 않지만 캐스팅이 확실히 작동하는 경우 safe_cast를 사용합니다.  
  
```  
    // A and B are not related  
    interface class A{};  
    interface class B{};  
    public ref class Class1 sealed : A, B { };  
...  
    A^ obj = ref new Class1();  
  
    // You know that obj’s backing type implements A and B, but  
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.  
    B^ obj2 = safe_cast<B^>(obj);  
```  
  
## <a name="dynamiccast"></a>dynamic_cast  
 사용 하 여 `dynamic_cast` 개체를 캐스팅 하는 경우 (hat 보다 구체적으로, `^`) 더 많이 파생 된 형식으로 예상 하는 중 하나가 대상 개체가 있을 경우에 따라 수도 있습니다 `nullptr` 이거나 캐스팅에 실패할 수 있습니다를 일반 코드로 상황을 처리 하려면 예외 대신 경로입니다. 예를 들어,는 **비어 있는 앱 (유니버설 Windows)** 프로젝트 템플릿에 `OnLaunched` 에서 메서드 `app.xamp.cpp` 사용 하 여 `dynamic_cast` 응용 프로그램 창에 내용이 있는지 여부를 테스트 합니다. 내용이 없어도 오류가 아니며 예기된 상황입니다. `Windows::Current::Content` 는 `Windows::UI::XAML::UIElement` 이며 상속 계층 구조에서 더 많이 파생된 형식인 `Windows::UI.XAML::Controls::Frame`으로 변환됩니다.  
```
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)  
{  
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);  
  
    // Do not repeat app initialization when the window already has content,  
    // just ensure that the window is active  
    if (rootFrame == nullptr)  
    {  
        // Create a Frame to act as the navigation context and associate it with  
        // a SuspensionManager key  
        rootFrame = ref new Frame();  
...  
```  
 `dynamic_cast` 의 또 다른 용도는 `Object^` 를 검색하여 boxed 값 형식이 있는지 확인하는 것입니다. 이 경우 `dynamic_cast<Platform::Box>` 나 `dynamic_cast<Platform::IBox>`를 시도합니다.  
  
 **dynamic_cast 및 추적 참조(%)**  
  
 추적 참조에 `dynamic_cast` 를 적용할 수도 있지만 이렇게 하면 캐스트가 `safe_cast`처럼 동작합니다. 추적 참조는 `Platform::InvalidCastException` 값을 가질 수 없으므로 실패 시 `nullptr`이 throw됩니다.  
  
## <a name="reinterpretcast"></a>reinterpret_cast  
 컴파일 타임 검사 또는 런타임 검사 중 어느 것도 수행되지 않으므로 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) 를 사용하지 않는 것이 좋습니다. 최악의 경우 `reinterpret_cast` 를 사용했을 때 개발 시 프로그래밍 오류가 감지되지 않아 프로그램 동작에 포착하기 어려운 오류나 심각한 오류가 발생할 수 있습니다. 드문 경우지만 관련되지 않은 형식 간의 캐스팅이 필요하며 해당 캐스트의 성공이 확실할 때만 `reinterpret_cast` 를 사용하는 것이 좋습니다. 사용 하는 드문 예 aWindows 런타임 형식을 내부 ABI 형식으로 변환 하는-즉, 해당 참조는 개체에 대 한 횟수를 제어 수행 되어 있습니다. 이렇게 하려면 [ComPtr Class](../cpp/com-ptr-t-class.md) 스마트 포인터를 사용하는 것이 좋습니다. 그렇지 않으면 인터페이스에서 릴리스를 명시적으로 호출해야 합니다. 다음 예제에서는 ref 클래스를 `IInspectable*`로 캐스팅하는 방법을 보여 줍니다.  
  
```  
#include <wrl.h>  
using namespace Microsoft::WRL;  
auto winRtObject = ref new SomeWinRTType();  
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);  
...
```  
  
 사용 하는 경우 `reinterpret_cast` oneWindows 런타임 인터페이스 간에 변환할 있습니다으로 인해 두 번 해제 됩니다. 따라서[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] 가 아닌 인터페이스로 변환할 때만 이 캐스트를 사용하세요.  
  
 **ABI 형식**  
  
-   ABI 형식은 Windows SDK의 헤더에 있습니다. 편의를 위해 헤더는 네임스페이스의 이름을 따릅니다(예: `windows.storage.h`).  
  
-   ABI 형식은 특수 특수 네임스페이스 ABI에 있습니다(예: `ABI::Windows::Storage::Streams::IBuffer*`).  
  
-   AWindows 런타임 인터페이스 형식과 동일한 ABI 형식 간의 변환은 항상 안전 하 게 보호-즉, `IBuffer^` 를 `ABI::IBuffer*`합니다.  
  
-   AWindows 런타임 런타임 클래스를 항상 변환할 `IInspectable*` 이나 알려진 기본 인터페이스로 합니다.  
  
-   ABI 형식으로 변환한 후에는 형식의 수명을 승인하고 COM 규칙을 따라야 합니다. ABI 포인터의 수명 관리 간소화를 위해 `WRL::ComPtr` 을 사용하는 것이 좋습니다.  
  
 다음 표에는 `reinterpret_cast`를 안전하게 사용하는 경우가 요약되어 있습니다. 모든 경우에 캐스팅은 양방향으로 안전합니다.  
  
|||  
|-|-|  
|HSTRING|String^|  
|HSTRING*|String^*|  
|IInspectable*|Object^|  
|IInspectable**|Object^*|  
|IInspectable-derived-type*|same-interface-from-winmd^|  
|IInspectable-derived-type**|same-interface-from-winmd^*|  
|IDefault-interface-of-RuntimeClass*|same-RefClass-from-winmd^|  
|IDefault-interface-of-RuntimeClass**|same-RefClass-from-winmd^*|  
  
## <a name="see-also"></a>참고 항목  
 [형식 시스템](../cppcx/type-system-c-cx.md)   
 [Visual c + + 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)   
 [네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
