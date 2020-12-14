---
description: '자세히 알아보기: 특성 프로그래밍 FAQ'
title: 특성 프로그래밍 FAQ
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 7a3bdfc8749297d11c5bc33b706265a1f5913a69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240431"
---
# <a name="attribute-programming-faq"></a>특성 프로그래밍 FAQ

이 항목에서는 다음과 같은 질문과 대답에 대해 설명 합니다.

- [HRESULT 란 무엇 인가요?](#vcconattributeprogrammmingfaqanchor1)

- [특성에 대 한 매개 변수 이름을 지정 해야 하는 경우](#vcconattributeprogrammmingfaqanchor2)

- [특성 블록에서 주석을 사용할 수 있나요?](#vcconattributeprogrammmingfaqanchor3)

- [특성은 상속을 사용 하 여 상호 작용 하는 방법](#vcconattributeprogrammmingfaqanchor4)

- [특성을 사용 하지 않는 ATL 프로젝트에서 특성을 사용 하려면 어떻게 해야 하나요?](#vcconattributeprogrammmingfaqanchor5)

- [특성을 사용 하는 프로젝트에서 .idl 파일을 사용 하려면 어떻게 해야 하나요?](#vcconattributeprogrammmingfaqanchor6)

- [특성에 의해 삽입 된 코드를 수정할 수 있습니까?](#vcconattributeprogrammmingfaqanchor7)

- [특성 사용 인터페이스를 전달 하려면 어떻게 해야 하나요?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [특성을 사용 하는 클래스에서 파생 된 클래스에서 특성을 사용할 수 있나요?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a> HRESULT 란 무엇 인가요?

HRESULT는 일반적으로 특성 및 ATL에서 반환 값으로 자주 사용 되는 단순 데이터 형식입니다. 다음 표에서는 다양 한 값에 대해 설명 합니다. 추가 값은 헤더 파일 winerror.h에 포함 되어 있습니다.

|Name|설명|값|
|----------|-----------------|-----------|
|S_OK|작업이 성공했습니다.|0x00000000|
|E_UNEXPECTED|예기치 않은 오류|0x8000FFFF|
|E_NOTIMPL|구현되지 않음|0x80004001|
|E_OUTOFMEMORY|필요한 메모리를 할당 하지 못했습니다.|0x8007000E|
|E_INVALIDARG|하나 이상의 인수가 잘못 되었습니다.|0x80070057|
|E_NOINTERFACE|이러한 인터페이스는 지원 되지 않습니다.|0x80004002|
|E_POINTER|잘못 된 포인터|0x80004003|
|E_HANDLE|잘못 된 핸들|0x80070006|
|E_ABORT|작업 중단 됨|0x80004004|
|E_FAIL|지정 되지 않은 오류|0x80004005|
|E_ACCESSDENIED|일반 액세스 거부 오류|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a> 특성에 대 한 매개 변수 이름을 지정 해야 하는 경우

대부분의 경우 특성에 단일 매개 변수가 있는 경우 해당 매개 변수의 이름은입니다. 이 이름은 코드에 특성을 삽입할 때 필요 하지 않습니다. 예를 들어 [집계](aggregatable.md) 가능한 특성을 다음과 같이 사용 합니다.

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

는와 정확히 동일 합니다.

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

그러나 다음 특성에는 명명 되지 않은 단일 매개 변수가 있습니다.

:::row:::
   :::column span="":::
      [`call_as`](call-as.md)\
      [`case`](case-cpp.md)\
      [`cpp_quote`](cpp-quote.md)\
      [`default`](default-cpp.md)\
      [`defaultvalue`](defaultvalue.md)\
      [`defaultvtable`](defaultvtable.md)\
      [`emitidl`](emitidl.md)\
      [`entry`](entry.md)\
      [`first_is`](first-is.md)
   :::column-end:::
   :::column span="":::
      [`helpcontext`](helpcontext.md)\
      [`helpfile`](helpfile.md)\
      [`helpstring`](helpstring.md)\
      [`helpstringcontext`](helpstringcontext.md)\
      [`helpstringdll`](helpstringdll.md)\
      [`id`](id.md)\
      [`iid_is`](iid-is.md)\
      [`import`](import.md)
   :::column-end:::
   :::column span="":::
      [`importlib`](importlib.md)\
      [`include`](include-cpp.md)\
      [`includelib`](includelib-cpp.md)\
      [`last_is`](last-is.md)\
      [`length_is`](length-is.md)\
      [`max_is`](max-is.md)\
      [`no_injected_text`](no-injected-text.md)\
      [`pointer_default`](pointer-default.md)
   :::column-end:::
   :::column span="":::
      [`pragma`](pragma.md)\
      [`restricted`](restricted.md)\
      [`size_is`](size-is.md)\
      [`source`](source-cpp.md)\
      [`switch_is`](switch-is.md)\
      [`switch_type`](switch-type.md)\
      [`transmit_as`](transmit-as.md)\
      [`wire_marshal`](wire-marshal.md)
   :::column-end:::
:::row-end:::

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a> 특성 블록에서 주석을 사용할 수 있나요?

특성 블록 내에서 한 줄과 여러 줄로 된 주석을 모두 사용할 수 있습니다. 그러나 특성에 대 한 매개 변수를 포함 하는 괄호 안에서는 주석 스타일을 사용할 수 없습니다.

허용 되는 기능은 다음과 같습니다.

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

다음은 허용 되지 않습니다.

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a> 특성은 상속을 사용 하 여 상호 작용 하는 방법

특성을 사용 하거나 사용 하지 않을 수 있는 다른 클래스에서 특성 사용 및 특성 클래스를 모두 상속할 수 있습니다. 특성 공급자가 해당 코드를 변환한 후에는 특성 사용 클래스에서 파생 된 결과가 해당 클래스에서 파생 되는 것과 같습니다. 특성은 c + + 상속을 통해 파생 클래스로 전송 되지 않습니다. 특성 공급자는 해당 특성의 주변 에서만 코드를 변환 합니다.

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a> 특성을 사용 하지 않는 ATL 프로젝트에서 특성을 사용 하려면 어떻게 해야 하나요?

.Idl 파일이 있는 특성을 사용 하지 않는 ATL 프로젝트가 있을 수 있으며, 특성 사용 개체를 추가 하기 시작할 수 있습니다. 이 경우 **클래스 추가 마법사** 를 사용 하 여 코드를 제공 합니다.

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a> 특성을 사용 하는 프로젝트에서 .idl 파일을 사용 하려면 어떻게 해야 하나요?

ATL 특성 사용 프로젝트에서 사용 하려는 .idl 파일이 있을 수 있습니다. 이 경우 [importidl](importidl.md) 특성을 사용 하 고 .idl 파일을 .h 파일로 컴파일한 다음 (프로젝트의 **속성 페이지** 대화 상자에서 [MIDL 속성 페이지](../../build/reference/midl-property-pages.md) 참조) 프로젝트에 .h 파일을 포함 합니다.

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a> 특성에 의해 삽입 된 코드를 수정할 수 있습니까?

일부 특성은 프로젝트에 코드를 삽입 합니다. [/Fx](../../build/reference/fx-merge-injected-code.md) 컴파일러 옵션을 사용 하 여 삽입 된 코드를 볼 수 있습니다. 또한 삽입 된 파일에서 코드를 복사 하 여 소스 코드에 붙여 넣을 수 있습니다. 이렇게 하면 특성의 동작을 수정할 수 있습니다. 그러나 코드의 다른 부분만 수정 해야 할 수도 있습니다.

다음 샘플은 삽입 된 코드를 소스 코드 파일로 복사 하는 결과입니다.

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")
]

class ATL_NO_VTABLE CTestTest : public ITestTest,
// the following base classes support added injected code
public IConnectionPointContainerImpl<CTestTest>,
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>
{
public:
   CTestTest() {
   }
   // this line would be commented out from original file
   // __event __interface _ITestTestEvents;
   DECLARE_PROTECT_FINAL_CONSTRUCT()
   HRESULT FinalConstruct() {
      return S_OK;
   }

void FinalRelease() {}

public:
   CComBSTR m_value;
   STDMETHOD(DoTest)(BSTR str) {
      VARIANT_BOOL bCancel = FALSE;
      BeforeChange(str,&bCancel);
      if (bCancel) {
          return Error("Error : Someone don't want us to change the value");
      }

   m_value =str;
   return S_OK;
    }
// the following was copied in from the injected code.
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {
   HRESULT hr = S_OK;
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;
   VARIANT rgvars[2];
   Lock();
   IUnknown** pp = p->m_vec.begin();
   Unlock();
   while (pp < p->m_vec.end()) {
      if (*pp != NULL) {
         IDispatch* pDispatch = (IDispatch*) *pp;
         ::VariantInit(&rgvars[1]);
         rgvars[1].vt = VT_BSTR;
         V_BSTR(&rgvars[1])= (BSTR) i1;
         ::VariantInit(&rgvars[0]);
         rgvars[0].vt = (VT_BOOL | VT_BYREF);
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };
         VARIANT ret_val;
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);
         if (FAILED(hr))
            break;
      }
      pp++;
   }
   return hr;
}

BEGIN_CONNECTION_POINT_MAP(CTestTest)
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))
END_CONNECTION_POINT_MAP()
// end added code section

// _ITestCtrlEvents Methods
public:
};

int main() {}
```

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> 특성 사용 인터페이스를 전달 하려면 어떻게 해야 하나요?

특성 사용 인터페이스의 전방 선언을 만들려면 실제 인터페이스 선언에 적용 하는 전방 선언에 동일한 특성을 적용 해야 합니다. 또한 [내보내기](export.md) 특성을 전방 선언에 적용 해야 합니다.

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> 특성을 사용 하는 클래스에서 파생 된 클래스에서 특성을 사용할 수 있나요?

아니요, 특성을 사용 하는 클래스에서 파생 된 클래스에 특성을 사용 하는 것도 지원 되지 않습니다.

## <a name="see-also"></a>참고 항목

[COM 및 .NET의 C++ 특성](cpp-attributes-com-net.md)
