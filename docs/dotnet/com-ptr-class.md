---
description: '자세한 정보: com::p tr 클래스'
title: com::ptr 클래스
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::com::ptr::ptr
- msclr::com::ptr::Attach
- msclr::com::ptr::CreateInstance
- msclr::com::ptr::Detach
- msclr::com::ptr::GetInterface
- msclr::com::ptr::QueryInterface
- msclr::com::ptr::Release
- msclr::com::ptr::operator=
- msclr::com::ptr::operator->
- msclr::com::ptr::operator!
helpviewer_keywords:
- msclr::ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: 73016d425d06ecbda12702afc1793a4bab81ccc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124399"
---
# <a name="comptr-class"></a>com::ptr 클래스

CLR 클래스의 멤버로 사용할 수 있는 COM 개체에 대한 래퍼입니다.  이 래퍼는 또한 COM 개체의 수명 주기 관리를 자동화하여 소멸자가 호출될 때 개체에서 모든 소유 참조를 해제합니다. [CComPtr 클래스](../atl/reference/ccomptr-class.md)와 유사 합니다.

## <a name="syntax"></a>구문

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>매개 변수

*_interface_type*<br/>
COM 인터페이스.

## <a name="remarks"></a>설명

또한 `com::ptr`은 로컬 함수 변수로 사용하여 여러 COM 작업을 간소화하고 수명 주기 관리를 자동화할 수 있습니다.

는 `com::ptr` 함수 매개 변수로 직접 사용할 수 없습니다. 대신 [추적 참조 연산자](../extensions/tracking-reference-operator-cpp-component-extensions.md) 또는 [개체 연산자 (^)에 대 한 핸들](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) 을 사용 하십시오.

는 `com::ptr` 함수에서 직접 반환 될 수 없습니다. 대신 핸들을 사용 하십시오.

## <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다.  클래스의 공용 메서드를 호출하면 포함된 `IXMLDOMDocument` 개체가 호출됩니다.  이 샘플은 XML 문서의 인스턴스를 만들고, 여기에 일부 간단한 XML을 채우고, 구문 분석된 문서 트리에서 간소화된 노드 작업을 수행하고 XML을 콘솔에 출력합니다.

```cpp
// comptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into the document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // simplified function to write just the first xml node to the console
   void WriteXml() {
      IXMLDOMNode* pNode = NULL;

      try {
         // the first child of the document is the first real xml node
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            WriteNode(pNode);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(IXMLDOMNode* pNode) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteXml();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<word>persnickety</word>
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|Name|설명|
|---------|-----------|
|[ptr::p tr](#ptr)|COM 개체를 래핑하는을 생성 `com::ptr` 합니다.|
|[ptr::~ptr](#tilde-ptr)|Destructs a `com::ptr` .|

### <a name="public-methods"></a>public 메서드

|Name|설명|
|---------|-----------|
|[ptr::Attach](#attach)|COM 개체를에 연결 `com::ptr` 합니다.|
|[ptr::CreateInstance](#createInstance)|내에서 COM 개체의 인스턴스를 만듭니다 `com::ptr` .|
|[ptr::Detach](#detach)|COM 개체의 소유권을 부여 하 여 개체에 대 한 포인터를 반환 합니다.|
|[ptr::GetInterface](#getInterface)|내에서 COM 개체의 인스턴스를 만듭니다 `com::ptr` .|
|[ptr::QueryInterface](#queryInterface)|소유 된 COM 개체를 쿼리하여 인터페이스에 연결 하 고 그 결과를 다른에 연결 `com::ptr` 합니다.|
|[ptr::Release](#release)|COM 개체에서 소유 된 모든 참조를 해제 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|---------|-----------|
|[ptr:: operator-&gt;](#operator-arrow)|소유 하는 COM 개체에서 메서드를 호출 하는 데 사용 되는 멤버 액세스 연산자입니다.|
|[ptr::operator=](#operator-assign)|COM 개체를에 연결 `com::ptr` 합니다.|
|[ptr:: operator &nbsp; bool](#operator-bool)|조건식에 사용 하기 위한 연산자 `com::ptr` 입니다.|
|[ptr:: operator!](#operator-logical-not)|소유 하는 COM 개체가 잘못 되었는지 여부를 확인 하는 연산자입니다.|

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\com\ptr.h>

**네임 스페이스** msclr:: com

## <a name="ptrptr"></a><a name="ptr"></a> ptr::p tr

소유 하는 COM 개체에 대 한 포인터를 반환 합니다.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>매개 변수

*P*<br/>
COM 인터페이스 포인터.

### <a name="remarks"></a>설명

인수가 없는 생성자는 **`nullptr`** 내부 개체 핸들에를 할당 합니다. 이후에를 호출 `com::ptr` 하면 내부 개체의 유효성이 검사 되 고 개체가 만들어지거나 연결 될 때까지 자동으로 실패 합니다.

단일 인수 생성자는 COM 개체에 대 한 참조를 추가 하지만 호출자의 참조를 해제 하지 않으므로 호출자가 `Release` com 개체에 대해를 호출 하 여 컨트롤을 실제로 지정 해야 합니다. `com::ptr`의 소멸자가 호출 되 면 해당 참조는 COM 개체에서 자동으로 해제 됩니다.

`NULL`이 생성자에 전달 하는 것은 인수가 없는 버전을 호출 하는 것과 같습니다.

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다. 이 예제에서는 두 가지 버전의 생성자를 모두 사용 하는 방법을 보여 줍니다.

```cpp
// comptr_ptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrptr"></a><a name="tilde-ptr"></a> ptr:: ~ ptr

Destructs a `com::ptr` .

```cpp
~ptr();
```

### <a name="remarks"></a>설명

소멸 시는 소유 하 고 있는 `com::ptr` 모든 참조를 COM 개체에 해제 합니다. COM 개체에 대 한 다른 참조가 없다는 가정 하에 COM 개체가 삭제 되 고 해당 메모리가 확보 됩니다.

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다.  함수에서 `main` 두 `XmlDocument` 개체의 소멸자가 블록 범위를 벗어날 때 호출 되어 **`try`** 기본 소멸자가 호출 되어 `com::ptr` COM 개체에 대 한 모든 소유 된 참조를 해제 합니다.

```cpp
// comptr_dtor.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrattach"></a><a name="attach"></a> ptr:: Attach

COM 개체를에 연결 `com::ptr` 합니다.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>매개 변수

*_right*<br/>
연결할 COM 인터페이스 포인터입니다.

### <a name="exceptions"></a>예외

가 `com::ptr` COM 개체에 대 한 참조를 이미 소유 하 고 있으면이 `Attach` throw <xref:System.InvalidOperationException> 됩니다.

### <a name="remarks"></a>설명

에 대 한 호출은 `Attach` COM 개체를 참조 하지만 해당 개체에 대 한 호출자 참조는 해제 하지 않습니다.

`NULL`에를 전달 하면 `Attach` 작업이 수행 되지 않습니다.

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다. `ReplaceDocument`멤버 함수는 먼저 `Release` 이전에 소유한 개체에 대해를 호출한 다음 `Attach` 를 호출 하 여 새 문서 개체를 연결 합니다.

```cpp
// comptr_attach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptrcreateinstance"></a><a name="createInstance"></a> ptr:: CreateInstance

내에서 COM 개체의 인스턴스를 만듭니다 `com::ptr` .

```cpp
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

### <a name="parameters"></a>매개 변수

*progid*<br/>
`ProgID` 문자열입니다.

*pouter*<br/>
집계 개체의 IUnknown 인터페이스에 대 한 포인터입니다 (IUnknown 제어). `pouter`을 지정 하지 않으면 `NULL` 가 사용 됩니다.

*cls_context*<br/>
새로 만든 개체를 관리 하는 코드가 실행 되는 컨텍스트입니다. 값은 열거형에서 가져옵니다 `CLSCTX` . `cls_context`을 지정 하지 않으면 CLSCTX_ALL 값이 사용 됩니다.

*rclsid*<br/>
`CLSID` 개체를 만드는 데 사용 되는 데이터 및 코드와 연결 됩니다.

### <a name="exceptions"></a>예외

가 `com::ptr` COM 개체에 대 한 참조를 이미 소유 하 고 있으면이 `CreateInstance` throw <xref:System.InvalidOperationException> 됩니다.

이 함수는를 호출 하 `CoCreateInstance` 고를 사용 하 여 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 모든 오류 `HRESULT` 를 적절 한 예외로 변환 합니다.

### <a name="remarks"></a>설명

`CreateInstance` 를 사용 하 여 `CoCreateInstance` ProgID 또는 CLSID에서 식별 된 지정 된 개체의 새 인스턴스를 만듭니다. 는 `com::ptr` 새로 만든 개체를 참조 하 고 소멸 될 때 소유 된 모든 참조를 자동으로 해제 합니다.

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다. 클래스 생성자는의 두 가지 형태 `CreateInstance` 를 사용 하 여 ProgID 또는 CLSID와 CLSCTX에서 문서 개체를 만듭니다.

```cpp
// comptr_createinstance.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="ptrdetach"></a><a name="detach"></a> ptr::D etach

COM 개체의 소유권을 부여 하 여 개체에 대 한 포인터를 반환 합니다.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>반환 값

COM 개체에 대 한 포인터입니다.

소유 하는 개체가 없는 경우 NULL이 반환 됩니다.

### <a name="exceptions"></a>예외

내부적으로 `QueryInterface` 는 소유 된 COM 개체에서 호출 되 고 오류는에 `HRESULT` 의해 예외로 변환 됩니다 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> .

### <a name="remarks"></a>설명

`Detach` 는 먼저 호출자를 대신 하 여 COM 개체에 대 한 참조를 추가한 다음에서 소유 하는 모든 참조를 해제 `com::ptr` 합니다.  호출자는 궁극적으로 반환 된 개체를 해제 하 여 제거 해야 합니다.

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다.  `DetachDocument`멤버 함수는 `Detach` 를 호출 하 여 COM 개체의 소유권을 부여 하 고 호출자에 게 포인터를 반환 합니다.

```cpp
// comptr_detach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // detach the COM object and return it
   // this releases the internal reference to the object
   IXMLDOMDocument* DetachDocument() {
      return m_ptrDoc.Detach();
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.DetachDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release document object as the ref class no longer owns it
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

## <a name="ptrgetinterface"></a><a name="getInterface"></a> ptr:: GetInterface

소유 하는 COM 개체에 대 한 포인터를 반환 합니다.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>반환 값

소유 된 COM 개체에 대 한 포인터입니다.

### <a name="exceptions"></a>예외

내부적으로 `QueryInterface` 는 소유 된 COM 개체에서 호출 되 고 오류는에 `HRESULT` 의해 예외로 변환 됩니다 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> .

### <a name="remarks"></a>설명

는 `com::ptr` 호출자를 대신 하 여 com 개체에 대 한 참조를 추가 하 고 com 개체에 대 한 참조도 유지 합니다. 호출자는 궁극적으로 반환 된 개체에 대 한 참조를 해제 해야 합니다. 그렇지 않으면 소멸 되지 않습니다.

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다. `GetDocument`멤버 함수는를 사용 하 여 `GetInterface` COM 개체에 대 한 포인터를 반환 합니다.

```cpp
// comptr_getinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a> ptr:: QueryInterface

소유 된 COM 개체를 쿼리하여 인터페이스에 연결 하 고 그 결과를 다른에 연결 `com::ptr` 합니다.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>매개 변수

*다른*<br/>
`com::ptr`인터페이스를 가져올입니다.

### <a name="exceptions"></a>예외

내부적으로 `QueryInterface` 는 소유 된 COM 개체에서 호출 되 고 오류는에 `HRESULT` 의해 예외로 변환 됩니다 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> .

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 현재 래퍼가 소유 하는 COM 개체의 다른 인터페이스에 대 한 COM 래퍼를 만들 수 있습니다. 이 메서드는 `QueryInterface` 소유 된 com 개체를 호출 하 여 com 개체의 특정 인터페이스에 대 한 포인터를 요청 하 고 반환 된 인터페이스 포인터를 전달 된에 연결 합니다 `com::ptr` .

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다. `WriteTopLevelNode`멤버 함수는 `QueryInterface` 를 사용 하 여 로컬을로 채운 다음, `com::ptr` `IXMLDOMNode` `com::ptr` 노드의 이름과 텍스트 속성을 콘솔에 쓰는 전용 멤버 함수에 (추적 참조)를 전달 합니다.

```cpp
// comptr_queryinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into our document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // write the top level node to the console
   void WriteTopLevelNode() {
      com::ptr<IXMLDOMNode> ptrNode;

      // query for the top level node interface
      m_ptrDoc.QueryInterface(ptrNode);
      WriteNode(ptrNode);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(com::ptr<IXMLDOMNode> % node) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(node->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(node->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteTopLevelNode();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<#document>persnickety</#document>
```

## <a name="ptrrelease"></a><a name="release"></a> ptr:: Release

COM 개체에서 소유 된 모든 참조를 해제 합니다.

```cpp
void Release();
```

### <a name="remarks"></a>설명

이 함수를 호출 하면 COM 개체에서 소유 된 모든 참조가 해제 되 고 COM 개체에 대 한 내부 핸들이로 설정 **`nullptr`** 됩니다.  COM 개체에 대 한 다른 참조가 없으면 소멸 됩니다.

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다.  `ReplaceDocument`멤버 함수는를 사용 하 여 `Release` 새 문서를 연결 하기 전에 이전 문서 개체를 모두 해제 합니다.

```cpp
// comptr_release.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a> ptr:: operator-&gt;

소유 하는 COM 개체에서 메서드를 호출 하는 데 사용 되는 멤버 액세스 연산자입니다.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>반환 값

`smart_com_ptr`COM 개체에 대 한입니다.

### <a name="exceptions"></a>예외

내부적으로 `QueryInterface` 는 소유 된 COM 개체에서 호출 되 고 오류는에 `HRESULT` 의해 예외로 변환 됩니다 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> .

### <a name="remarks"></a>설명

이 연산자를 사용 하면 소유 된 COM 개체의 메서드를 호출할 수 있습니다. `smart_com_ptr`자체 및를 자동으로 처리 하는 임시를 반환 합니다 `AddRef` `Release` .

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다. `WriteDocument`함수는 `operator->` 를 사용 하 여 `get_firstChild` 문서 개체의 멤버를 호출 합니다.

```cpp
// comptr_op_member.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="ptroperator"></a><a name="operator-assign"></a> ptr:: operator =

COM 개체를에 연결 `com::ptr` 합니다.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>매개 변수

*_right*<br/>
연결할 COM 인터페이스 포인터입니다.

### <a name="return-value"></a>반환 값

에 대 한 추적 참조 `com::ptr` 입니다.

### <a name="exceptions"></a>예외

가 `com::ptr` COM 개체에 대 한 참조를 이미 소유 하 고 있으면이 `operator=` throw <xref:System.InvalidOperationException> 됩니다.

### <a name="remarks"></a>설명

COM 개체를에 할당 하는 `com::ptr` 것은 com 개체를 참조 하지만 해당 개체에 대 한 호출자 참조는 해제 하지 않습니다.

이 연산자는와 동일한 결과를 가집니다 `Attach` .

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다.  `ReplaceDocument`멤버 함수는 먼저 `Release` 이전에 소유한 개체에 대해를 호출한 다음 `operator=` 를 사용 하 여 새 문서 개체를 연결 합니다.

```cpp
// comptr_op_assign.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc = pDoc;
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by the ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="ptroperator-bool"></a><a name="operator-bool"></a> ptr:: operator bool

조건식에 사용 하기 위한 연산자 `com::ptr` 입니다.

```cpp
operator bool();
```

### <a name="return-value"></a>반환 값

**`true`** 소유 된 COM 개체가 유효 하면이 고, 그렇지 않으면입니다. **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

소유 하 고 있는 COM 개체는 유효 하지 않은 경우 유효 합니다 **`nullptr`** .

이 연산자는 `_detail_class::_safe_bool` **`bool`** 정수 계열 형식으로 변환할 수 없기 때문에 보다 안전한로 변환 합니다.

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다. `CreateInstance`멤버 함수는 `operator bool` 새 문서 개체를 만든 후를 사용 하 여 유효한 지 확인 하 고, 있는 경우 콘솔에 씁니다.

```cpp
// comptr_op_bool.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) { // uses operator bool
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="ptroperator"></a><a name="operator-logical-not"></a> ptr:: operator!

소유 하는 COM 개체가 잘못 되었는지 여부를 확인 하는 연산자입니다.

```cpp
bool operator!();
```

### <a name="return-value"></a>반환 값

**`true`** 소유 된 COM 개체가 잘못 된 경우 **`false`** 그렇지 않으면입니다.

### <a name="remarks"></a>설명

소유 하 고 있는 COM 개체는 유효 하지 않은 경우 유효 합니다 **`nullptr`** .

### <a name="example"></a>예제

이 예제에서는 `com::ptr`을 사용해서 해당 개인 멤버 `IXMLDOMDocument` 개체를 래핑하는 CLR 클래스를 구현합니다.  `CreateInstance`멤버 함수는 `operator!` 를 사용 하 여 문서 개체가 이미 소유 되었는지 여부를 확인 하 고 개체가 잘못 된 경우에만 새 인스턴스를 만듭니다.

```cpp
// comptr_op_not.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) {
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```
