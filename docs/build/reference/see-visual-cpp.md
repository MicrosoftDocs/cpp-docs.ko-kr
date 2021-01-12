---
description: 자세한 내용은 다음을 &lt; 참조 하세요.&gt;
title: '&lt;> (c + + 문서 주석)을 참조 하세요.'
ms.date: 11/04/2016
f1_keywords:
- <see>
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: c1de0ec23854d159d661cd1b62df97169eab7317
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126223"
---
# <a name="ltseegt"></a>&lt;see&gt;

\<see> 태그를 사용하면 텍스트 내부에서 링크를 지정할 수 있습니다. [\<seealso>](seealso-visual-cpp.md)참고 항목 섹션에 표시할 텍스트를 나타내는 데 사용 합니다.

## <a name="syntax"></a>구문

```
<see cref="member"/>
```

#### <a name="parameters"></a>매개 변수

*구성원과*<br/>
현재 컴파일 환경에서 호출할 수 있는 멤버 또는 필드에 대한 참조입니다.  이름을 단일 또는 이중 따옴표로 묶습니다.

컴파일러는 지정된 코드 요소가 있는지 확인하고, 출력 XML의 요소 이름에 대한 `member`를 확인합니다.  `member`가 검색되지 않는 경우 컴파일러에서 경고가 발생합니다.

## <a name="remarks"></a>설명

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

\<see> 사용 예제는 [\<summary>](summary-visual-cpp.md)를 참조하세요.

MSVC 컴파일러는 문서 주석을 통해 한 번의 cref 참조를 확인 하려고 시도 합니다.  따라서 C++ 조회 규칙을 사용하는 경우 컴파일러에서 기호를 찾을 수 없으며 참조는 확인되지 않음으로 표시됩니다. [\<seealso>](seealso-visual-cpp.md)자세한 내용은을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 컴파일러가 참조를 확인하는 작업 등 제네릭 형식에 대한 cref 참조를 확인할 수 있는 방법을 보여줍니다.

```cpp
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
