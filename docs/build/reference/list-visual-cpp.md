---
title: '&lt;> 목록 (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- list
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: 24f9b17c67b8f951743fd51c04266b05dad235c7
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041967"
---
# <a name="ltlistgt-and-ltlistheadergt"></a>&lt;목록 &gt; 및 &lt; listheader&gt;

\<listheader> 블록은 테이블 또는 정의 목록의 머리글 행을 정의하는 데 사용됩니다. 테이블을 정의할 때는 머리글에 용어 항목만 제공하면 됩니다.

## <a name="syntax"></a>구문

```xml
<list type="bullet" | "number" | "table">
   <listheader>
      <term>term</term>
      <description>description</description>
   </listheader>
   <item>
      <term>term</term>
      <description>description</description>
   </item>
</list>
```

#### <a name="parameters"></a>매개 변수

*부채*<br/>
`description`에서 정의되는, 정의할 용어입니다.

*description*<br/>
글머리 기호 또는 번호 매기기 목록의 항목이나 `term`의 정의입니다.

## <a name="remarks"></a>설명

목록의 각 항목은 \<item> 블록을 사용하여 지정됩니다. 정의 목록을 만들 때는 `term`과 `description`을 모두 지정해야 합니다. 그러나 테이블, 글머리 기호 목록 또는 번호 매기기 목록의 경우 `description` 항목만 제공하면 됩니다.

목록 또는 테이블에 \<item> 블록을 필요한 개수만큼 포함할 수 있습니다.

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

## <a name="example"></a>예제

```cpp
// xml_list_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_list_tag.dll
/// <remarks>Here is an example of a bulleted list:
/// <list type="bullet">
/// <item>
/// <description>Item 1.</description>
/// </item>
/// <item>
/// <description>Item 2.</description>
/// </item>
/// </list>
/// </remarks>
class MyClass {};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
