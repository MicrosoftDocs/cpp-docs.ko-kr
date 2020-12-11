---
description: '자세한 정보: ATL과 MFC 중 선택에 대 한 권장 사항'
title: ATL과 MFC 중 선택에 대 한 권장 사항
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
ms.openlocfilehash: 506df04ebbd3bc9079e1d40cf14773d9d9a6bd1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159156"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>ATL과 MFC 중 선택에 대 한 권장 사항

구성 요소 및 응용 프로그램을 개발할 때 두 가지 방법, 즉 ATL과 MFC (MFC 라이브러리) 중에서 선택할 수 있습니다.

## <a name="using-atl"></a>ATL 사용

ATL은 c + +에서 COM 구성 요소를 만들고 작은 사용 공간을 유지 하는 빠르고 쉬운 방법입니다. MFC에서 자동으로 제공 하는 기본 제공 기능이 모두 필요 하지 않은 경우 ATL을 사용 하 여 컨트롤을 만듭니다.

## <a name="using-mfc"></a>MFC 사용

MFC를 사용 하 여 전체 응용 프로그램, ActiveX 컨트롤 및 활성 문서를 만들 수 있습니다. MFC를 사용 하 여 컨트롤을 이미 만든 경우에는 MFC에서 개발을 계속 하는 것이 좋습니다. 새 컨트롤을 만들 때 MFC의 기본 제공 기능이 모두 필요 하지 않은 경우 ATL을 사용 하는 것이 좋습니다.

## <a name="using-atl-in-an-mfc-project"></a>MFC 프로젝트에서 ATL 사용

마법사를 실행 하 여 기존 MFC 프로젝트에서 ATL 사용에 대 한 지원을 추가할 수 있습니다. 자세한 내용은 [MFC 프로젝트에 ATL 지원 추가](../mfc/reference/adding-atl-support-to-your-mfc-project.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[ATL 소개](../atl/introduction-to-atl.md)
