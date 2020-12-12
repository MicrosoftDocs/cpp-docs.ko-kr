---
description: '자세한 정보: MFC MBCS DLL 추가 기능'
title: MFC MBCS DLL 추가 기능
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 8961fe65937d53c2aa056b7061548710e0c80286
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122774"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 추가 기능

MFC 및 해당 MBCS (멀티 바이트 문자 집합) 라이브러리를 지원 하려면 Visual Studio 2013 이상에서 Visual Studio를 설치 하는 동안 추가 단계가 필요 합니다.

**Visual Studio 2013**: 기본적으로 Visual Studio 2013에 설치 된 MFC 라이브러리는 유니코드 개발만 지원 합니다. Visual Studio 2013에서 **문자 집합** 속성이 **멀티 바이트 문자 집합 사용** 또는 **설정 안 함** 으로 설정 된 MFC 프로젝트를 빌드하기 위해 MBCS dll이 필요 합니다. [Visual Studio 2013 용 멀티 바이트 MFC 라이브러리](https://www.microsoft.com/download/details.aspx?id=40770)에서 DLL을 다운로드 합니다.

**Visual Studio 2015**: 유니코드 및 MBCS MFC dll은 모두 Visual C++ 설치 구성 요소에 포함 되어 있지만 MFC에 대 한 지원은 기본적으로 설치 되지 않습니다. Visual C++ 및 MFC는 Visual Studio 설치 프로그램에서 선택적 설치 구성입니다. MFC가 설치되었는지 확인하려면 설치 프로그램에서 **사용자 지정** 을 선택하고 **프로그래밍 언어** 에서 **Visual C++** 및 **C++용 Microsoft Foundation Classes** 가 선택되어 있는지 확인합니다. Visual Studio를 이미 설치한 경우 MFC 프로젝트를 만들려고 하면 Visual C++ 및/또는 MFC를 설치하라는 메시지가 표시됩니다.

**Visual Studio 2017 이상**: 유니코드 및 MBCS mfc dll은 Visual Studio 설치 관리자 프로그램의 **선택적 구성 요소** 창에서 **MFC 및 ATL 지원을** 선택할 때 **c + +를 사용한 데스크톱 개발** 워크 로드와 함께 설치 됩니다. 설치에 이러한 구성 요소가 포함 되지 않은 경우 해당 파일로 이동 합니다. **새 프로젝트** 대화 상자를 **열고 Visual Studio 설치 관리자 열기** 링크를 클릭 합니다. 자세한 내용은 [Visual Studio 설치](/visualstudio/install/install-visual-studio)를 참조하세요.

## <a name="see-also"></a>참고 항목

[MFC 라이브러리 버전](mfc-library-versions.md)
