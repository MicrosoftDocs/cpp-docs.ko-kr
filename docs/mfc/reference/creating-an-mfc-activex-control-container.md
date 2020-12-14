---
description: '자세한 정보: MFC ActiveX 컨트롤 컨테이너 만들기'
title: MFC ActiveX 컨트롤 컨테이너 만들기
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.container
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
ms.openlocfilehash: 221edf8cfaefb55b919c1117becc074cdfd880ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343194"
---
# <a name="creating-an-mfc-activex-control-container"></a>MFC ActiveX 컨트롤 컨테이너 만들기

ActiveX 컨트롤 컨테이너는 ActiveX (이전의 OLE) 컨트롤이 실행 되는 환경을 제공 하는 부모 프로그램입니다. MFC를 사용 하거나 사용 하지 않고 ActiveX 컨트롤을 포함할 수 있는 응용 프로그램을 만들 수 있지만 MFC를 사용 하는 것이 훨씬 쉽습니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](../activex-controls.md)을 참조 하세요.

Mfc [응용 프로그램 마법사](../../mfc/reference/mfc-application-wizard.md) 를 사용 하 여 mfc 컨테이너 프로그램을 만들면 Mfc 및 activex 클래스에서 구현 하는 ActiveX 컨트롤 및 자동화의 많은 기능에 액세스할 수 있습니다. 이러한 기능에는 시각적 편집, 자동화, 복합 파일 만들기 및 컨트롤에 대 한 지원이 포함 됩니다. 부모 프로그램에서 지원할 MFC 응용 프로그램 마법사 비주얼 편집 옵션에는 컨테이너, 미니 서버, 전체 서버 및 컨테이너와 서버 모두에 해당 하는 프로그램을 만드는 작업이 포함 됩니다.

- **새 MFC 응용 프로그램** 입니다. 자동화, 시각적 편집, 복합 파일 또는 컨트롤 지원을 포함 하는 새로운 MFC 프로그램을 만들려면 MFC 응용 프로그램 마법사를 사용 하 여 적절 한 자동화 옵션을 선택 합니다.

- **기존 MFC 응용 프로그램** 입니다. 기존 MFC 응용 프로그램에 컨트롤 포함을 추가 하는 경우 ole 컨트롤 [컨테이너: Ole 컨트롤 포함을 수동으로 사용](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)을 참조 하세요.

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>다음 유형의 응용 프로그램에 대 한 ActiveX 컨테이너를 만들려면

1. [컨테이너](../../mfc/containers.md)

1. [시각적 편집](../../mfc/ole-mfc.md)

1. [MFC ActiveX 컨트롤](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>참조

[Visual Studio의 C++ 프로젝트 형식](../../build/reference/visual-cpp-project-types.md)
