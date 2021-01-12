---
description: '자세히 알아보기: &lt; 요약&gt;'
title: '&lt;요약> (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 3003a3226a67d864be1a07a47151e7003c5514a4
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126340"
---
# <a name="ltsummarygt"></a>&lt;summary&gt;

\<summary> 태그를 사용하여 형식 또는 형식 멤버를 설명해야 합니다. [\<remarks>](remarks-visual-cpp.md)를 사용하여 형식 설명에 보충 정보를 추가할 수 있습니다.

## <a name="syntax"></a>구문

```
<summary>description</summary>
```

#### <a name="parameters"></a>매개 변수

*description*<br/>
개체에 대한 요약입니다.

## <a name="remarks"></a>설명

태그에 대 한 텍스트는 \<summary> IntelliSense의 형식에 대 한 유일한 정보 소스 이며 [개체 브라우저](/visualstudio/ide/viewing-the-structure-of-code) 및 코드 주석 웹 보고서에도 표시 됩니다.

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

## <a name="example"></a>예제

```cpp
// xml_summary_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_summary_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>MyMethod is a method in the MyClass class.
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>
   /// <seealso cref="MyClass::MyMethod2"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void MyMethod2() {}
};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
