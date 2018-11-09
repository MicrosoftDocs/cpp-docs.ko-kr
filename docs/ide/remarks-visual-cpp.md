---
title: '&lt;remarks&gt;(Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: bf81c1e9ef51caf1a3f30591d0df559ea4dfc631
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461531"
---
# <a name="ltremarksgt-visual-c"></a>&lt;remarks&gt;(Visual C++)

\<remarks> 태그는 형식에 대한 정보를 추가하여 [\<summary>](../ide/summary-visual-cpp.md)로 지정된 정보를 보완하기 위해 사용됩니다. 이 정보는 [개체 브라우저](/visualstudio/ide/viewing-the-structure-of-code) 및 코드 주석 웹 보고서에 표시됩니다.

## <a name="syntax"></a>구문

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>매개 변수

*description*<br/>
멤버에 대한 설명입니다.

## <a name="remarks"></a>설명

[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)로 컴파일하여 문서 주석을 파일로 처리합니다.

## <a name="example"></a>예

```
// xml_remarks_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_remarks_tag.dll

using namespace System;

/// <summary>
/// You may have some primary information about this class.
/// </summary>
/// <remarks>
/// You may have some additional information about this class.
/// </remarks>
public ref class MyClass {};
```

## <a name="see-also"></a>참고 항목

[XML 문서](../ide/xml-documentation-visual-cpp.md)