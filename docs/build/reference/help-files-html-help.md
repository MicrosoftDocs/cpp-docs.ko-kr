---
title: 도움말 파일(HTML 도움말)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
ms.openlocfilehash: 7fbac8bfa0427e8d6c60e88da92a525e62fb1a24
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446285"
---
# <a name="help-files-html-help"></a>도움말 파일(HTML 도움말)

다음 파일은 **상황에 맞는 도움말** 확인란을 선택한 다음, MFC 애플리케이션 마법사의 [고급 기능](../../mfc/reference/advanced-features-mfc-application-wizard.md) 페이지에서 **HTML 도움말 형식**을 선택하여 애플리케이션에 HTML 도움말 형식의 도움말 지원을 추가하면 만들어집니다.

|파일 이름|디렉터리 위치|솔루션 탐색기 위치|설명|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hhp|*Projname*\hlp|HTML 도움말 파일|도움말 프로젝트 파일. 도움말 파일을 .hxs 파일 또는 .chm 파일로 컴파일하는 데 필요한 데이터가 들어 있습니다.|
|*Projname*.hhk|*Projname*\hlp|HTML 도움말 파일|도움말 항목의 인덱스를 포함합니다.|
|*Projname*.hhc|*Projname*\hlp|HTML 도움말 파일|도움말 프로젝트의 콘텐츠입니다.|
|Makehtmlhelp.bat|*Projname*|소스 파일|프로젝트가 컴파일될 때 시스템이 도움말 프로젝트를 빌드하는 데 사용합니다.|
|Afxcore.htm|*Projname*\hlp|HTML 도움말 항목|표준 MFC 명령 및 화면 개체에 대한 표준 도움말 항목이 포함되어 있습니다. 이 파일에 사용자 지정 도움말 항목을 추가합니다.|
|Afxprint.htm|*Projname*\hlp|HTML 도움말 항목|인쇄 명령에 대한 도움말 항목이 포함되어 있습니다.|
|*.jpg; \*.gif|*Projname*\hlp\Images|리소스 파일|생성된 여러 도움말 파일 항목에 대한 이미지를 포함합니다.|

## <a name="see-also"></a>참고자료

[시각적 개체에 대해 만들어지는 형식 파일 C++ 프로젝트](file-types-created-for-visual-cpp-projects.md)
