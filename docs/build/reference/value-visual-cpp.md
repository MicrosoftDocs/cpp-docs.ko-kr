---
description: '자세히 알아보기: &lt; 값&gt;'
title: '&lt;값> (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 5ebab554a33ff0d90b9306f3aec56b2552e18c5a
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126327"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

\<value>태그를 사용 하 여 속성 및 속성 접근자 메서드를 설명할 수 있습니다. Visual Studio 통합 개발 환경에서 코드 마법사를 사용 하 여 속성을 추가 하면 [\<summary>](summary-visual-cpp.md) 새 속성의 태그가 추가 됩니다. 그런 다음, \<value> 태그를 수동으로 추가하여 속성이 나타내는 값을 설명해야 합니다.

## <a name="syntax"></a>구문

```
<value>property-description</value>
```

#### <a name="parameters"></a>매개 변수

*property-description*<br/>
속성에 대한 설명입니다.

## <a name="remarks"></a>설명

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

## <a name="example"></a>예제

```cpp
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
