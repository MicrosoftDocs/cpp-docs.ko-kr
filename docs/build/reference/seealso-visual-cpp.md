---
description: '자세히 알아보기: &lt; seealso&gt;'
title: '&lt;seealso> (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 70f5f0147ff56dd6327e99f073f80c28a7cce539
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224727"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

\<seealso> 태그를 사용하면 참고 항목 섹션에 표시할 텍스트를 지정할 수 있습니다. 텍스트 내에서 링크를 지정하려면 [\<see>](see-visual-cpp.md)를 사용합니다.

## <a name="syntax"></a>구문

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>매개 변수

*구성원과*<br/>
현재 컴파일 환경에서 호출할 수 있는 멤버 또는 필드에 대한 참조입니다.  이름을 단일 또는 이중 따옴표로 묶습니다.

컴파일러는 지정된 코드 요소가 있는지 확인하고, 출력 XML의 요소 이름에 대한 `member`를 확인합니다.  `member`가 검색되지 않는 경우 컴파일러에서 경고가 발생합니다.

제네릭 형식에 대 한 cref 참조를 만드는 방법에 대 한 자세한 내용은을 참조 하십시오 [\<see>](see-visual-cpp.md) .

## <a name="remarks"></a>설명

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

\<seealso> 사용 예제는 [\<summary>](summary-visual-cpp.md)를 참조하세요.

MSVC 컴파일러는 문서 주석을 통해 한 번의 cref 참조를 확인 하려고 시도 합니다.  따라서 C++ 조회 규칙을 사용하는 경우 컴파일러에서 기호를 찾을 수 없으며 참조는 확인되지 않음으로 표시됩니다.

## <a name="example"></a>예제

다음 샘플에서 확인되지 않은 기호는 cref에서 참조됩니다. B::Test에 대한 cref의 XML 주석은 `<seealso cref="!:B::Test" />`인 반면, A::Test에 대한 참조는 올바른 형식의 `<seealso cref="M:A.Test" />`입니다.

```cpp
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
