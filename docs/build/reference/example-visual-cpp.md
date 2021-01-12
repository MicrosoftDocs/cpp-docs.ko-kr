---
description: '자세한 정보: &lt; 예제&gt;'
title: '&lt;예제> (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- <example>
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
ms.openlocfilehash: 61624efd34c02d75c7109a3211914b2018c513ae
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98125885"
---
# <a name="ltexamplegt"></a>&lt;example&gt;

\<example> 태그를 사용하면 메서드 또는 기타 라이브러리 멤버를 사용하는 방법의 예제를 지정할 수 있습니다. 일반적으로이 경우에도 태그의 사용이 포함 됩니다 [\<code>](code-visual-cpp.md) .

## <a name="syntax"></a>구문

```
<example>description</example>
```

#### <a name="parameters"></a>매개 변수

*description*<br/>
코드 샘플에 대한 설명입니다.

## <a name="remarks"></a>설명

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

## <a name="example"></a>예제

```cpp
// xml_example_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_example_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>
   /// GetZero method
   /// </summary>
   /// <example> This sample shows how to call the GetZero method.
   /// <code>
   /// int main()
   /// {
   ///    return GetZero();
   /// }
   /// </code>
   /// </example>
   static int GetZero() {
      return 0;
   }
};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
