---
description: '자세히 알아보기: &lt; 포함&gt;'
title: '&lt;> 포함 (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- <include>
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
ms.openlocfilehash: 577281b293fcca9b9b0b9491dd239240d435f32c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199781"
---
# <a name="ltincludegt"></a>&lt;include&gt;

\<include> 태그를 사용하면 소스 코드의 형식과 멤버를 설명하는 다른 파일의 주석을 참조할 수 있습니다. 소스 코드 파일에 직접 문서 주석을 포함하는 대신 사용되는 대안입니다.  예를 들어를 사용 \<include> 하 여 팀 또는 회사 전체에서 사용 되는 표준 "상용구" 주석을 삽입할 수 있습니다.

## <a name="syntax"></a>구문

```
<include file='filename' path='tagpath' />
```

#### <a name="parameters"></a>매개 변수

*filename*<br/>
문서가 포함된 파일의 이름입니다. 경로를 사용하여 파일 이름을 정규화할 수 있습니다.  이름을 단일 또는 이중 따옴표로 묶습니다.  `filename`가 검색되지 않는 경우 컴파일러에서 경고가 발생합니다.

*tagpath*<br/>
파일에 포함된 원하는 노드 집합을 선택하는 유효한 XPath 식입니다.

*name*<br/>
주석 앞에 오는 태그의 이름 지정자입니다. `name`에는 `id`가 있습니다.

*id*<br/>
주석 앞에 오는 태그의 ID입니다.  이름을 단일 또는 이중 따옴표로 묶습니다.

## <a name="remarks"></a>설명

\<include> 태그는 XML XPath 구문을 사용합니다. 를 사용 하 여 사용자 지정 하는 방법은 XPath 설명서를 참조 하세요 \<include> .

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

## <a name="example"></a>예제

다중 파일 예제입니다. 에서 사용 하는 첫 번째 파일에는 \<include> 다음과 같은 문서 주석이 포함 되어 있습니다.

```cpp
// xml_include_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_include_tag.dll

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />
public ref class Test {
   void TestMethod() {
   }
};

/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />
public ref class Test2 {
   void Test() {
   }
};
```

두 번째 파일인 xml_include_tag.doc에는 다음과 같은 문서 주석이 포함되어 있습니다.

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a>프로그램 출력

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>t2</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
