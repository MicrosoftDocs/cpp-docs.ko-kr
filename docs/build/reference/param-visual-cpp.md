---
description: '자세한 정보: &lt; param&gt;'
title: '&lt;param> (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- <param>
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
ms.openlocfilehash: 1de18bd050cfd6986f1fba7f1ae7acc289a41e14
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126210"
---
# <a name="ltparamgt"></a>&lt;param&gt;

\<param> 태그는 메서드의 매개 변수 중 하나를 설명하기 위해 메서드 선언에 대한 주석에서 사용해야 합니다.

## <a name="syntax"></a>구문

```
<param name='name'>description</param>
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
메서드 매개 변수의 이름입니다.  이름을 단일 또는 이중 따옴표로 묶습니다.  `name`가 검색되지 않는 경우 컴파일러에서 경고가 발생합니다.

*description*<br/>
매개 변수에 대한 설명입니다.

## <a name="remarks"></a>설명

태그에 대 한 텍스트는 \<param> IntelliSense, [개체 브라우저](/visualstudio/ide/viewing-the-structure-of-code)및 코드 주석 웹 보고서에 표시 됩니다.

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

## <a name="example"></a>예제

```cpp
// xml_param_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_param_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <param name="Int1">Used to indicate status.</param>
   void MyMethod(int Int1) {
   }
};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
