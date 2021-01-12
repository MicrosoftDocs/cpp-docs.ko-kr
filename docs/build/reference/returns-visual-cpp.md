---
description: '자세한 정보: &lt; 반환&gt;'
title: '&lt;> 반환 (c + + 문서 주석)'
ms.date: 11/04/2016
f1_keywords:
- <returns>
helpviewer_keywords:
- returns C++ XML tag
- <returns> C++ XML tag
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
ms.openlocfilehash: 59b9a7d33a3b2695a2a5e22fdac465f17c915492
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126119"
---
# <a name="ltreturnsgt"></a>&lt;returns&gt;

\<returns> 태그는 메서드 선언의 주석에서 반환 값을 설명하는 데 사용해야 합니다.

## <a name="syntax"></a>구문

```
<returns>description</returns>
```

#### <a name="parameters"></a>매개 변수

*description*<br/>
반환 값에 대한 설명입니다.

## <a name="remarks"></a>설명

[/Doc](doc-process-documentation-comments-c-cpp.md) 를 사용 하 여 컴파일하여 문서 주석을 파일로 처리 합니다.

## <a name="example"></a>예제

```cpp
// xml_returns_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_returns_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <returns>Returns zero.</returns>
   int GetZero() { return 0; }
};
```

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
