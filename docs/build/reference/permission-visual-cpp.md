---
description: '자세한 정보: &lt; 사용 권한&gt;'
title: '&lt;권한> (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: faade1711afa1f086d26104242dbdb3cb8814462
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126106"
---
# <a name="ltpermissiongt"></a>&lt;permission&gt;

\<permission> 태그를 사용하면 멤버 액세스 권한을 문서화할 수 있습니다. <xref:System.Security.PermissionSet>를 사용하면 멤버 액세스 권한을 지정할 수 있습니다.

## <a name="syntax"></a>구문

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>매개 변수

*구성원과*<br/>
현재 컴파일 환경에서 호출할 수 있는 멤버 또는 필드에 대한 참조입니다. 컴파일러는 지정된 코드 요소가 있으며 `member`를 출력 XML의 정식 요소 이름으로 변환하는지 확인합니다.  이름을 단일 또는 이중 따옴표로 묶습니다.

`member`가 검색되지 않는 경우 컴파일러에서 경고가 발생합니다.

제네릭 형식에 대 한 cref 참조를 만드는 방법에 대 한 자세한 내용은을 참조 하십시오 [\<see>](see-visual-cpp.md) .

*description*<br/>
멤버 액세스 권한에 대한 설명입니다.

## <a name="remarks"></a>설명

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

MSVC 컴파일러는 문서 주석을 통해 한 번의 cref 참조를 확인 하려고 시도 합니다.  따라서 C++ 조회 규칙을 사용하는 경우 컴파일러에서 기호를 찾을 수 없으며 참조는 확인되지 않음으로 표시됩니다. [\<seealso>](seealso-visual-cpp.md)자세한 내용은을 참조 하세요.

## <a name="example"></a>예제

```cpp
// xml_permission_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_permission_tag.dll
using namespace System;
/// Text for class TestClass.
public ref class TestClass {
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>
   void Test() {}
};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
