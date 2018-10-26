---
title: 속성 (C + + /cli 및 C + + /cli CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- property_cpp
- property
dev_langs:
- C++
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24028ac403092404ddf7fd279864273fcf6016ab
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075868"
---
# <a name="property--ccli-and-ccx"></a>속성 (C + + /cli 및 C + + /cli CX)

선언 된 *속성*, 동작 및 데이터 멤버 또는 배열 요소 처럼 액세스 되는 멤버 함수는 합니다.

## <a name="all-runtimes"></a>모든 런타임

다음 형식의 속성 중 하나를 선언할 수 있습니다.

*단순 속성*<br/>
기본적으로 만듭니다는 *set 접근자* 속성 값을 할당 하는 *get 접근자* 속성 값 및 속성 값을 포함 하는 컴파일러에서 생성 된 전용 데이터 멤버를 검색 하는 합니다.

*속성 블록*<br/>
사용자 정의 get 및/또는 set 접근자를 만드는 데 사용합니다. 속성은 get 및 set 접근자를 둘 다 정의하면 읽기/쓰기이고, get 접근자만 정의하는 읽기 전용이고, set 접근자만 정의하면 쓰기 전용입니다.

속성 값을 포함하려면 데이터 멤버를 명시적으로 선언해야 합니다.

*인덱싱된 속성*<br/>
하나 이상의 인덱스로 지정된 속성 값을 가져오고 설정하는 데 사용할 수 있는 속성 블록입니다.

인덱싱된 속성을 가진 사용자 정의 속성 이름을 만들 수 있습니다 또는 *기본* 속성 이름입니다. 기본 인덱스 속성의 이름은 속성이 정의된 클래스의 이름입니다. 기본 속성을 선언 하려면 지정 된 **기본** 속성 이름 대신 키워드입니다.

속성 값을 포함하려면 데이터 멤버를 명시적으로 선언해야 합니다. 인덱싱된 속성의 경우 데이터 멤버는 대개 배열 또는 컬렉션입니다.

### <a name="syntax"></a>구문

```cpp
property type property_name;

property type property_name {
   access-modifier type get() inheritance-modifier {property_body};
   access-modifier void set(type value) inheritance-modifier {property_body};
}

property type property_name[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}

property type default[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}
```

### <a name="parameters"></a>매개 변수

*type*<br/>
속성 값의 데이터 형식 및 결과적으로 속성 자체입니다.

*property_name*<br/>
속성의 이름입니다.

*액세스 한정자*<br/>
액세스 한정자입니다. 유효한 한정자는 **정적** 하 고 **가상**합니다.

Get 또는 set 접근자 일치할 필요가 합니다 **가상** 한정자가 있지만에 동의 해야 합니다는 **정적** 한정자.

*상속 한정자*<br/>
상속 한정자입니다. 유효한 한정자는 **추상** 하 고 **봉인**합니다.

*index_list*<br/>
인덱스 하나 이상의 쉼표로 구분된 목록입니다. 각 인덱스는 인덱스 형식 및 속성 메서드 본문에서 사용할 수 있는 선택적 식별자로 구성됩니다.

*값*<br/>
set 작업에서 속성에 할당하거나 get 작업에서 검색할 값입니다.

*property_body*<br/>
set 또는 get 접근자의 속성 메서드 본문입니다. *property_body* 사용할 수는 *index_list* 기본 속성 데이터 멤버에 액세스 하거나 사용자 정의 처리에서 매개 변수로 합니다.

## <a name="windows-runtime"></a>Windows 런타임

자세한 내용은 [속성 (C + + /cli CX)](https://msdn.microsoft.com/library/windows/apps/hh755807.aspx)합니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="syntax"></a>구문

```cpp
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}
```

### <a name="parameters"></a>매개 변수

*한정자*<br/>
속성 선언 또는 get/set 접근자 메서드에 사용할 수 있는 한정자입니다. 가능한 값은 **정적** 하 고 **가상**합니다.

*type*<br/>
속성으로 나타내는 값의 형식입니다.

*property_name*<br/>
raise 메서드에 대한 매개 변수는 대리자의 서명과 일치해야 합니다.

*index_list*<br/>
대괄호(아래 첨자 연산자, ([])) 안에 지정된 인덱스 하나 이상의 쉼표로 구분된 목록입니다. 각 인덱스의 경우 형식 및 선택적으로 속성 메서드 본문에서 사용할 수 있는 식별자를 지정합니다.

### <a name="remarks"></a>설명

첫 번째 구문 예제는 *단순 속성*를 암시적으로 선언 하는 둘 다를 `set` 및 `get` 메서드. 컴파일러에서는 속성 값을 저장할 전용 필드를 자동으로 만듭니다.

두 번째 구문 예제는 *속성 블록*를 명시적으로 선언 하는 둘 다를 `set` 및 `get` 메서드.

세 번째 구문 예제에서는 고객이 정의한 *index 속성*합니다. 인덱스 속성은 설정 또는 검색할 값 이외에 매개 변수를 사용합니다. 속성 이름을 지정해야 합니다. 단순 속성과 달리 인덱스 속성의 `set` 및/또는 `get` 메서드는 명시적으로 정의해야 하고 속성 이름을 지정해야 합니다.

네 번째 구문 예제는 *기본* 형식의 인스턴스에 대 한 배열 유사 액세스를 제공 하는 속성입니다. 키워드 **기본**, 기본 속성을 지정 하는 데에 사용 됩니다. 기본 속성의 이름은 속성이 정의된 형식의 이름입니다.

합니다 **속성** 키워드는 클래스, 인터페이스 또는 값 형식에 나타날 수 있습니다. 속성은 get 함수(읽기 전용), set 함수(쓰기 전용) 또는 두 가지 모두(읽기/쓰기)를 포함할 수 있습니다.

속성 이름은 자신이 포함된 관리되는 클래스의 이름과 일치할 수 없습니다. getter 함수의 반환 형식은 해당 setter 함수의 마지막 매개 변수 형식과 반드시 일치해야 합니다.

클라이언트 코드에서 속성은 일반 데이터 멤버 형태로 표시되고 데이터 멤버와 같은 구문을 사용하여 쓰거나 읽을 수 있습니다.

Get 및 set 메서드가 일치할 필요가 합니다 **가상** 한정자입니다.

get 및 set 메서드의 접근성은 다를 수 있습니다.

속성 메서드의 정의는 일반 메서드처럼 클래스 본문 외부에 나타날 수 있습니다.

Get 및 set 메서드를 속성에 대 한 일치 해야 합니다 **정적** 한정자입니다.

속성의 get 및 set 메서드가 다음 설명에 해당하면 속성은 스칼라 속성입니다.

- get 메서드에 매개 변수가 없고 반환 형식은 `T`입니다.

- Set 메서드 형식 매개 변수가 `T`, 및 반환 형식을 **void**합니다.

같은 식별자가 포함된 한 범위에 선언된 스칼라 속성은 하나만 있어야 합니다. 스칼라 속성은 오버로드할 수 없습니다.

속성 데이터 멤버가 선언되면 컴파일러에서는 데이터 멤버(“백업 저장소”라고도 함)를 클래스에 주입합니다. 그러나 데이터 멤버의 이름은 포함하는 클래스의 실제 데이터 멤버였던 것처럼 소스에서 멤버를 참조할 수 없는 형태입니다. ildasm.exe를 사용하여 형식에 대한 메타데이터를 표시하고 속성 백업 저장소의 컴파일러에서 생성된 이름을 확인합니다.

속성 블록에서 접근자 메서드에 대해 서로 다른 접근성을 사용할 수 있습니다.  즉, set 메서드는 공용일 수 있고 get 메서드는 전용일 수 있습니다.  그러나 접근자 메서드에 속성 자체의 선언에 대한 접근성보다 덜 제한적인 접근성을 포함하면 오류가 발생합니다.

**속성** 상황에 맞는 키워드입니다.  자세한 내용은 [상황에 맞는 키워드](../windows/context-sensitive-keywords-cpp-component-extensions.md)합니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 예제에서는 속성 데이터 멤버 및 속성 블록의 선언 및 사용을 보여 줍니다.  속성 접근자를 클래스 외부에서 정의할 수 있다는 것도 보여 줍니다.

```cpp
// mcppv2_property.cpp
// compile with: /clr
using namespace System;
public ref class C {
   int MyInt;
public:

   // property data member
   property String ^ Simple_Property;

   // property block
   property int Property_Block {

      int get();

      void set(int value) {
         MyInt = value;
      }
   }
};

int C::Property_Block::get() {
   return MyInt;
}

int main() {
   C ^ MyC = gcnew C();
   MyC->Simple_Property = "test";
   Console::WriteLine(MyC->Simple_Property);

   MyC->Property_Block = 21;
   Console::WriteLine(MyC->Property_Block);
}
```

```Output
test

21
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP용 구성 요소 확장](../windows/component-extensions-for-runtime-platforms.md)