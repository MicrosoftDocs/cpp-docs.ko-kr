---
description: '자세히 알아보기: 문서 주석에 대 한 권장 태그'
title: 문서 주석에 대 한 권장 태그 (c + + 문서 주석)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 34bae4043231abed87770aec252303bd99707afe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225351"
---
# <a name="recommended-tags-for-documentation-comments"></a>문서 주석에 대한 권장 태그

MSVC 컴파일러는 코드에서 문서 주석을 처리 하 고 각 compiland에 대 한 .xdc 파일을 만들며 xdcmake.exe, .xdc 파일을 .xml 파일로 처리 합니다. 문서를 만들기 위해 .xml 파일을 처리하는 것은 사이트에서 구현해야 하는 세부 사항입니다.

태그는 형식, 형식 멤버와 같은 구문에서 처리됩니다.

태그는 형식 또는 멤버 바로 앞에 와야 합니다.

> [!NOTE]
> 문서 주석은 속성 및 이벤트에 대한 네임스페이스 또는 라인 외부 정의에 적용할 수 없습니다. 문서 주석은 클래스 내 선언에 있어야 합니다.

컴파일러는 유효한 XML인 태그를 모두 처리합니다. 다음 태그는 사용자 문서에서 일반적으로 사용되는 기능을 제공합니다.

[`<c>`](c-visual-cpp.md)
[`<code>`](code-visual-cpp.md)
[`<example>`](example-visual-cpp.md)
[`<exception>`](exception-visual-cpp.md)<sup></sup> 
 1 [`<include>`](include-visual-cpp.md) <sup></sup> 
 [`<list>`](list-visual-cpp.md) 1 
 [`<para>`](para-visual-cpp.md) 
 [`<param>`](param-visual-cpp.md) <sup></sup> 
 1 [`<paramref>`](paramref-visual-cpp.md) <sup></sup> 
 1 [`<permission>`](permission-visual-cpp.md) <sup></sup> 
 [`<remarks>`](remarks-visual-cpp.md) 1 
 [`<returns>`](returns-visual-cpp.md) 
 [`<see>`](see-visual-cpp.md) <sup></sup> 
 1 [`<seealso>`](seealso-visual-cpp.md) <sup>1</sup>
[`<summary>`](summary-visual-cpp.md)
[`<value>`](value-visual-cpp.md)

1. 컴파일러가 구문을 확인합니다.

현재 릴리스에서 MSVC 컴파일러는 `<paramref>` 다른 Visual Studio 컴파일러에서 지원 되는 태그를 지원 하지 않습니다. Visual C++는 이후 릴리스에서 `<paramref>`를 지원할 수 있습니다.

## <a name="see-also"></a>참고 항목

[XML 문서](xml-documentation-visual-cpp.md)
