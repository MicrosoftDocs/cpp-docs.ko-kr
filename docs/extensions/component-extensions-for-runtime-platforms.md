---
title: .NET 및 UWP용 구성 요소 확장
ms.date: 10/12/2018
ms.topic: overview
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: 887fa14153e728735937604d531782a9ae7535bb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509719"
---
# <a name="component-extensions-for-net-and-uwp"></a>.NET 및 UWP용 구성 요소 확장

C++ 표준을 사용하면 컴파일러 공급업체에서 언어에 대한 비표준 확장을 제공할 수 있습니다. Microsoft에서는 .NET Framework 또는 UWP(유니버설 Windows 플랫폼)에서 실행되는 코드에 네이티브 C++ 코드를 연결할 수 있는 확장을 제공합니다. .NET 확장은 C++/CLI라고 하며, CLR(공용 언어 런타임)이라는 .NET 관리형 실행 환경에서 실행되는 코드를 생성합니다. UWP 확장은 C++/CX라고 하며, 네이티브 기계어 코드를 생성합니다.

> [!NOTE]
> 새 애플리케이션에는 C++/CX 대신 C++/WinRT를 사용하는 것이 좋습니다. C++/WinRT는 Windows 런타임 API용 새 표준 C++17 언어 프로젝션입니다. C++/CX와 WRL도 계속 지원되지만, 새 애플리케이션에서는 C++/WinRT를 사용하는 것이 좋습니다. 자세한 내용은 [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index) 참조하세요.

### <a name="two-runtimes-one-set-of-extensions"></a>두 개의 런타임, 하나의 확장명 집합

C++/CLI는 ISO/ANSI C++ 표준을 확장하며, Ecma C++/CLI 표준에 따라 정의됩니다. 자세한 내용은 [C++/CLI를 사용한 .NET 프로그래밍(Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)을 참조하세요.

C++/CX 확장은 C++/CLI의 하위 집합입니다. 확장 구문은 대부분의 경우에서 동일하지만, 생성되는 코드는 UWP를 대상으로 하는 `/ZW` 컴파일러 옵션을 지정하는지, .NET을 대상으로 하는 `/clr` 옵션을 지정하는지에 따라 달라집니다. 이러한 스위치는 Visual Studio를 사용하여 프로젝트를 만들 때 자동으로 설정됩니다.

## <a name="data-type-keywords"></a>데이터 형식 키워드

언어 확장에는 ‘집계 키워드’가 포함됩니다. 이 키워드는 공백으로 구분된 두 개의 토큰으로 구성됩니다.** 토큰은 별도로 사용될 때의 의미와 함께 사용될 때의 의미가 있을 수 있습니다. 예를 들어 "ref"라는 단어는 일반 식별자이고 "class"라는 단어는 네이티브 클래스를 선언하는 키워드입니다. 그러나 이러한 단어가 결합되어 **ref class**를 구성하는 경우 결과 집계 키워드는 ‘런타임 클래스’로 알려진 엔터티를 선언합니다.**

확장에는 ‘상황에 맞는’ 키워드도 포함됩니다.** 키워드는 해당 키워드를 포함하는 문의 종류 및 해당 문에서의 배치에 따라 상황에 맞는 것으로 처리됩니다. 예를 들어 토큰 "property"는 식별자이거나 특별한 종류의 public 클래스 멤버를 선언할 수 있습니다.

다음 표에는 C++ 언어 확장의 키워드가 나열되어 있습니다.

|키워드|상황에 맞는지 여부|용도|참조|
|-------------|-----------------------|-------------|---------------|
|**ref class**<br /><br /> **ref struct**|아니요|클래스를 선언합니다.|[클래스 및 구조체](classes-and-structs-cpp-component-extensions.md)|
|**value class**<br /><br /> **value struct**|아니요|값 클래스를 선언합니다.|[클래스 및 구조체](classes-and-structs-cpp-component-extensions.md)|
|**인터페이스 클래스**<br /><br /> **interface struct**|아니요|인터페이스를 선언합니다.|[인터페이스 클래스](interface-class-cpp-component-extensions.md)|
|**열거형 클래스**<br /><br /> **enum struct**|아니요|열거형을 선언합니다.|[열거형 클래스](enum-class-cpp-component-extensions.md)|
|**`property`**|예|속성을 선언합니다.|[property](property-cpp-component-extensions.md)|
|**delegate**|예|대리자를 선언합니다.|[위임(C++/CLI 및 C++/CX)](delegate-cpp-component-extensions.md)|
|**event**|예|이벤트를 선언합니다.|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Override 지정자

다음 키워드를 사용하여 파생의 재정의 동작을 정규화할 수 있습니다. 키워드는 **`new`** c + +의 확장이 아니지만 추가 컨텍스트에서 사용할 수 있기 때문에 여기에 나열 됩니다. 일부 지정자는 네이티브 프로그래밍에도 사용할 수 있습니다. 자세한 내용은 [방법: 네이티브 컴파일에 Override 지정자 선언 (c + +/cli)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)을 참조 하세요.

|키워드|상황에 맞는지 여부|용도|참조|
|-------------|-----------------------|-------------|---------------|
|**abstract**|예|함수 또는 클래스가 추상임을 나타냅니다.|[abstract](abstract-cpp-component-extensions.md)|
|**`new`**|아니요|함수가 기본 클래스 버전의 재정의가 아님을 나타냅니다.|[new(vtable의 new 슬롯)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|예|메서드가 기본 클래스 버전의 재정의이어야 함을 나타냅니다.|[override](override-cpp-component-extensions.md)|
|**sealed**|예|클래스를 기본 클래스로 사용할 수 없도록 합니다.|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>제네릭에 대한 키워드

다음은 제네릭 형식을 지원하도록 추가된 키워드입니다. 자세한 내용은 [제네릭](generics-cpp-component-extensions.md)을 참조하세요.

|키워드|상황에 맞는지 여부|용도|
|-------------|-----------------------|-------------|
|**범용**|아니요|제네릭 형식을 선언합니다.|
|**where**|예|제네릭 형식 매개 변수에 적용되는 제약 조건을 지정합니다.|

## <a name="miscellaneous-keywords"></a>기타 키워드

다음은 C++ 확장에 추가된 키워드입니다.

|키워드|상황에 맞는지 여부|용도|참조|
|-------------|-----------------------|-------------|---------------|
|**finally**|예|기본 예외 처리 동작을 나타냅니다.|[예외 처리](exception-handling-cpp-component-extensions.md)|
|**for each, in**|아니요|컬렉션의 요소를 열거합니다.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|아니요|가비지 수집 힙에 형식을 할당합니다. **`new`** 및 대신를 사용 **`delete`** 합니다.|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**ref new**|예|Windows 런타임 형식을 할당합니다. **`new`** 및 대신를 사용 **`delete`** 합니다.|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|예|선언 또는 정적 생성자에서만 멤버를 초기화할 수 있음을 나타냅니다.|[initonly(C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**literal**|예|리터럴 변수를 만듭니다.|[literal](literal-cpp-component-extensions.md)|
|**`nullptr`**|아니요|핸들 또는 포인터가 개체를 가리키지 않음을 나타냅니다.|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>템플릿 구문

다음 언어 구문은 키워드 대신 템플릿으로 구현됩니다. `/ZW` 컴파일러 옵션을 지정하는 경우 `lang` 네임스페이스에 정의됩니다. `/clr` 컴파일러 옵션을 지정하는 경우 `cli` 네임스페이스에 정의됩니다.

|키워드|용도|참조|
|-------------|-------------|---------------|
|**array**|배열을 선언합니다.|[배열](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(CLR에만 해당) 참조 형식의 데이터를 가리킵니다.|[interior_ptr (c + +/CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(CLR에만 해당) 가비지 수집 시스템을 일시적으로 표시하지 않도록 CLR 참조 형식을 가리킵니다.|[pin_ptr (c + +/CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|런타임 형식에 대한 최적의 캐스팅 메서드를 확인하고 실행합니다.|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**`typeid`**|(CLR에만 해당) 지정된 형식 또는 개체를 설명하는 <xref:System.Type?displayProperty=fullName>개체를 검색합니다.|[typeid](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>선언자

다음 형식 선언자는 할당된 개체의 수명 및 삭제를 자동으로 관리하도록 런타임에 지시합니다.

|연산자|용도|참조|
|--------------|-------------|---------------|
|`^`|개체에 대한 핸들, 즉 더 이상 사용할 수 없는 경우 자동으로 삭제되는 Windows 런타임 또는 CLR 개체에 대한 포인터를 선언합니다.|[개체 연산자에 대 한 핸들 (^)](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|추적 참조, 즉 더 이상 사용할 수 없는 경우 자동으로 삭제되는 Windows 런타임 또는 CLR 개체에 대한 참조를 선언합니다.|[추적 참조 연산자](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>추가 구문 및 관련 항목

이 섹션에서는 추가 프로그래밍 구문 및 CLR과 관련된 항목을 나열합니다.

|항목|설명|
|-----------|-----------------|
|[__identifier (c + +/CLI)](identifier-cpp-cli.md)|(Windows 런타임 및 CLR) 키워드를 식별자로 사용할 수 있습니다.|
|[가변 인수 목록 (...) (C + +/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows 런타임 및 CLR) 함수에서 가변 개수의 인수를 사용할 수 있습니다.|
|[C++ 네이티브 형식에 해당하는 .NET Framework(C++/CLI)](../dotnet/managed-types-cpp-cli.md#dotnet)|C++ 정수 계열 형식 대신 사용되는 CLR 유형을 나열합니다.|
|[appdomain](../cpp/appdomain.md) **`__declspec`** modifier|**`__declspec`** appdomain 당 정적 및 전역 변수가 존재 하도록 규정 하는 한정자입니다.|
|[/Clr을 사용한 c 스타일 캐스트 (c + +/CLI)](c-style-casts-with-clr-cpp-cli.md)|C 스타일 캐스트가 해석되는 방법을 설명합니다.|
|[__clrcall](../cpp/clrcall.md) 호출 규칙|CLR 규격 호출 규칙을 나타냅니다.|
|`__cplusplus_cli`|[미리 정의 된 매크로](../preprocessor/predefined-macros.md)|
|[사용자 지정 특성](user-defined-attributes-cpp-component-extensions.md)|사용자 고유의 CLR 특성을 정의하는 방법을 설명합니다.|
|[예외 처리](exception-handling-cpp-component-extensions.md)|예외 처리에 대한 개요를 제공합니다.|
|[명시적 재정의](explicit-overrides-cpp-component-extensions.md)|멤버 함수에서 임의 멤버를 재정의하는 방법을 보여 줍니다.|
|[Friend 어셈블리 (c + +)](../dotnet/friend-assemblies-cpp.md)|클라이언트 어셈블리에서 어셈블리 구성 요소의 모든 형식에 액세스할 수 있는 방법을 설명합니다.|
|[boxing](boxing-cpp-component-extensions.md)|값 형식이 boxing되는 조건을 보여 줍니다.|
|[형식 특성에 대 한 컴파일러 지원](compiler-support-for-type-traits-cpp-component-extensions.md)|컴파일 시간에 형식의 특성을 검색하는 방법을 설명합니다.|
|[관리 되는 관리 되지 않는](../preprocessor/managed-unmanaged.md) pragma|관리되는 함수와 관리되지 않는 함수가 동일한 모듈에 공존하는 방법을 보여 줍니다.|
|[프로세스](../cpp/process.md) **`__declspec`** modifier|**`__declspec`** 정적 및 전역 변수가 프로세스 별로 존재 하도록 규정 하는 한정자입니다.|
|[리플렉션(C++/CLI)](../dotnet/reflection-cpp-cli.md)|런타임 형식 정보의 CLR 버전을 보여 줍니다.|
|[String](string-cpp-component-extensions.md)|<xref:System.String>로 문자열 리터럴의 컴파일러 변환을 설명합니다.|
|[형식 전달 (c + +/CLI)](type-forwarding-cpp-cli.md)|클라이언트 코드를 다시 컴파일할 필요가 없도록 전달 어셈블리의 형식을 다른 어셈블리로 이동할 수 있습니다.|
|[사용자 정의 특성](user-defined-attributes-cpp-component-extensions.md)|사용자 정의 특성을 보여 줍니다.|
|[#using 지시문](../preprocessor/hash-using-directive-cpp.md)|외부 어셈블리를 가져옵니다.|
|[XML 문서](../build/reference/xml-documentation-visual-cpp.md)|[/doc(문서 주석 처리)(C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)를 사용하여 XML 기반 코드 문서를 설명합니다.|

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[네이티브 및 .NET 상호 운용성](../dotnet/native-and-dotnet-interoperability.md)
