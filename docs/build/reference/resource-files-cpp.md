---
title: 프로젝트 리소스 파일 (c + +)
ms.date: 05/14/2019
helpviewer_keywords:
- resource files
- resources [C++]
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: d37c3602d8939db609fc8af42dd764655195b24b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041018"
---
# <a name="project-resource-files-c"></a>프로젝트 리소스 파일 (c + +)

리소스는 사용자에게 정보를 제공하는 인터페이스 요소입니다. 비트맵, 아이콘, 도구 모음 및 커서는 모두 리소스입니다. 일부 리소스는 메뉴에서 선택하거나 대화 상자에 데이터를 입력하는 등의 작업을 수행할 수 있습니다.

자세한 내용은 [리소스 사용](../../windows/working-with-resource-files.md)을 참조하세요.

|파일 이름|디렉터리 위치|솔루션 탐색기 위치|Description|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.rc|*Projname*|소스 파일|프로젝트의 리소스 스크립트 파일입니다. 리소스 스크립트 파일에는 프로젝트의 형식에 따라 프로젝트에 대해 선택된 지원(예: 도구 모음, 대화 상자 또는 HTML) 및 다음이 포함되어 있습니다.<br /><br />- 기본 메뉴 정의<br />- 가속기 및 문자열 테이블<br />-기본 **정보** 대화 상자<br />- 기타 대화 상자<br />-아이콘 파일 (res \\ *Projname*.ico)<br />- 버전 정보<br />- 비트맵<br />- 도구 모음<br />- HTML 파일<br /><br /> 리소스 파일에는 표준 Microsoft Foundation Class 리소스에 대한 Afxres.rc 파일이 포함됩니다.|
|Resource.h|*Projname*|헤더 파일|프로젝트에서 사용하는 리소스에 대한 정의를 포함하는 리소스 헤더 파일입니다.|
|*Projname*.rc2|*Projname*\res|소스 파일|프로젝트에서 사용하는 추가 리소스를 포함하는 스크립트 파일입니다. 프로젝트의 .rc 파일 아래에 .rc2 파일을 포함할 수 있습니다.<br /><br /> .rc2 파일은 여러 가지 다른 프로젝트에서 사용하는 리소스를 포함하는 데 유용합니다. 다른 프로젝트에서 여러 번 동일한 리소스를 만드는 대신 .rc2 파일에 배치하고, .rc2 파일을 기본 .rc 파일에 포함할 수 있습니다.|
|*Projname*.def|*Projname*|소스 파일|DLL 프로젝트의 모듈 정의 파일입니다. 컨트롤의 경우 런타임 힙의 크기뿐만 아니라 컨트롤의 이름 및 설명을 제공합니다.|
|*Projname*.ico|*Projname*\res|리소스 파일|프로젝트 또는 컨트롤의 아이콘 파일입니다. 이 아이콘은 애플리케이션이 최소화될 때 나타납니다. 애플리케이션의 **정보** 상자에서도 사용됩니다. 기본적으로 MFC는 MFC 아이콘을 제공하고 ATL은 ATL 아이콘을 제공합니다.|
|*Projname*Doc.ico|*Projname*\res|리소스 파일|문서/보기 아키텍처에 대한 지원을 포함하는 MFC 프로젝트의 아이콘 파일입니다.|
|Toolbar.bmp|*Projname*\res|리소스 파일|도구 모음이나 색상표에서 애플리케이션 또는 컨트롤을 나타내는 비트맵 파일입니다. 이 비트맵은 프로젝트의 리소스 파일에 포함됩니다. 초기 도구 모음 및 상태 표시줄은 **CMainFrame** 클래스에 생성됩니다.|
|ribbon.mfcribbon-ms|*Projname*\res|리소스 파일|리본의 단추, 컨트롤 및 특성을 정의하는 XML 코드가 포함된 리소스 파일입니다. 자세한 내용은 [Ribbon Designer (MFC)](../../mfc/ribbon-designer-mfc.md)을 참조하세요.|

## <a name="see-also"></a>참고 항목

[Visual Studio C++ 프로젝트용으로 만든 파일 형식](file-types-created-for-visual-cpp-projects.md)
