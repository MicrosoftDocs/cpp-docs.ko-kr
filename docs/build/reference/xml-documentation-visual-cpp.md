---
description: '자세한 정보: XML 문서 (Visual C++)'
title: XML 문서(Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: 762380d08483292866cb96b34be4d85f7a2f510a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260945"
---
# <a name="xml-documentation-visual-c"></a>XML 문서(Visual C++)

Visual C++에서 .xml 파일로 처리될 소스 코드에 주석을 추가할 수 있습니다. 그러면 코드의 클래스에 대한 문서를 만드는 프로세스에 이 파일을 입력할 수 있습니다.

Visual C++ 코드 파일에서 XML 문서 주석은 메서드 또는 형식 정의 바로 앞에 있어야 합니다. 이 주석은 다음 시나리오에서 IntelliSense QuickInfo 데이터 팁을 채우는 데 사용할 수 있습니다.

1. 코드가 .winmd 파일과 함께 Windows 런타임 구성 요소로 컴파일되는 경우

1. 소스 코드가 현재 프로젝트에 포함된 경우

1. 형식 선언 및 구현이 동일한 헤더 파일에 있는 라이브러리

> [!NOTE]
> 현재 릴리스에서는 코드 주석이 템플릿 또는 템플릿 형식을 포함하는 모든 항목(예: 매개 변수를 템플릿으로 사용하는 함수)에서 처리되지 않습니다. 이러한 주석을 추가하면 정의되지 않은 동작이 발생합니다.

문서 주석이 있는 .xml 파일을 만드는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.

|원하는 정보|참조 항목|
|---------------------------|---------|
|사용할 컴파일러 옵션|[/doc](doc-process-documentation-comments-c-cpp.md)|
|문서에서 일반적으로 사용되는 기능을 제공하는 데 사용할 수 있는 태그|[문서 주석에 대한 권장 태그](recommended-tags-for-documentation-comments-visual-cpp.md)|
|컴파일러에서 코드의 구문을 식별하기 위해 생성하는 ID 문자열|[.Xml 파일 처리](dot-xml-file-processing.md)|
|문서 태그를 구분하는 방법|[Visual C++ 문서 태그의 구분 기호](delimiters-for-visual-cpp-documentation-tags.md)|
|하나 이상의 .xdc 파일에서.xml 파일을 생성합니다.|[XDCMake 참조](xdcmake-reference.md)|
|Visual Studio 기능 영역과 관련된 XML에 대한 정보 링크|[Visual Studio의 XML](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

문서 주석의 텍스트에 XML 특수 문자를 넣어야 하는 경우 XML 엔터티 또는 CDATA 섹션을 사용해야 합니다.

## <a name="see-also"></a>참고 항목

[런타임 플랫폼용 구성 요소 확장](../../extensions/component-extensions-for-runtime-platforms.md)
