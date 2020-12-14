---
description: '자세한 정보: MFC ActiveX 컨트롤 마법사'
title: MFC ActiveX 컨트롤 마법사
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.mfc.ctl.overview
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
ms.openlocfilehash: f313f2a218c06a20eddbfff33e936109e4be2cf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219267"
---
# <a name="mfc-activex-control-wizard"></a>MFC ActiveX 컨트롤 마법사

ActiveX 컨트롤은 특정 형식의 [자동화 서버](../../mfc/automation-servers.md)입니다. 재사용 가능한 구성 요소입니다. ActiveX 컨트롤을 호스트 하는 응용 프로그램은 해당 컨트롤의 [자동화 클라이언트](../../mfc/automation-clients.md) 입니다. 이러한 재사용 가능한 구성 요소를 만드는 것이 목표 라면이 마법사를 사용 하 여 컨트롤을 만듭니다. 자세한 내용은 [MFC ActiveX 컨트롤](../../mfc/mfc-activex-controls.md) 을 참조 하세요.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](../activex-controls.md)을 참조 하세요.

또는 [Mfc 응용 프로그램 마법사](../../mfc/reference/mfc-application-wizard.md)를 사용 하 여 자동화 서버 mfc 응용 프로그램을 만들 수 있습니다.

이 마법사를 사용 하 여 만든 ActiveX 컨트롤은 사용자 인터페이스를 포함 하거나 숨길 수 있습니다. 마법사의 [컨트롤 설정](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) 페이지에서이 옵션을 지정할 수 있습니다. 타이머 컨트롤은 표시 하지 않으려는 ActiveX 컨트롤의 예입니다.

ActiveX 컨트롤에는 복잡 한 사용자 인터페이스가 있을 수 있습니다. 일부 컨트롤은 캡슐화 된 형태 (여러 필드를 포함 하는 단일 컨트롤)와 같을 수 있습니다. 각 컨트롤은 고유한 오른쪽에 있는 Windows 컨트롤입니다. 예를 들어, MFC ActiveX 컨트롤로 구현 되는 자동 파트 개체는 사용자가 파트 번호, 파트 이름 및 기타 정보를 읽고 편집할 수 있는 양식 형태의 사용자 인터페이스를 제공할 수 있습니다. 자세한 내용은 [MFC ActiveX 컨트롤](../../mfc/mfc-activex-controls.md) 을 참조 하세요.

ActiveX 개체에 대 한 컨테이너를 만들어야 하는 경우 [Activex 컨트롤 컨테이너 만들기](../../mfc/reference/creating-an-mfc-activex-control-container.md)를 참조 하세요.

MFC 스타터 프로그램에는 c + + 소스 파일 (.cpp), 리소스 (.rc) 파일 및 프로젝트 파일 (.vcxproj)이 포함 되어 있습니다. 이러한 스타터 파일에서 생성 된 코드는 MFC를 기반으로 합니다.

다음 샘플 목록에서는 ActiveX 컨트롤에 대 한 향상 된 기능 및 작업 유형을 보여 줍니다.

- [ActiveX 컨트롤 최적화](../../mfc/mfc-activex-controls-optimization.md)

- [ActiveX 컨트롤에 스톡 이벤트 추가](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [사용자 지정 이벤트 추가](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [스톡 메서드 추가](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [사용자 지정 메서드 추가](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [스톡 속성 추가](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [사용자 지정 속성 추가](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [ActiveX 컨트롤 컨테이너에서 ActiveX 컨트롤 프로그래밍](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>개요

이 마법사 페이지에서는 사용자가 만드는 MFC ActiveX 컨트롤 프로젝트에 대 한 현재 응용 프로그램 설정을 설명 합니다. 기본적으로 마법사는 다음과 같이 프로젝트를 만듭니다.

- 기본 프로젝트에서 런타임 라이선스 또는 도움말 파일을 생성 하지 않습니다. [응용 프로그램 설정](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) 페이지에서 이러한 기본 설정을 변경할 수 있습니다. ActiveX 컨트롤 마법사의이 페이지에서 선택한 항목만 **개요** 페이지에 반영 됩니다.

- 프로젝트에는 프로젝트의 이름을 기반으로 하는 컨트롤 클래스와 속성 페이지 클래스가 포함 됩니다. [컨트롤 이름](../../mfc/reference/control-names-mfc-activex-control-wizard.md) 페이지에서 프로젝트 이름 및 파일 이름을 편집할 수 있습니다.

- 컨트롤은 기존 Windows 컨트롤을 기반으로 하 고, 표시 되 면 활성화 하 고, 사용자 인터페이스를 포함 하 고, **정보** 대화 상자를 포함 합니다. 이러한 기본 설정은 [컨트롤 설정](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) 페이지에서 변경할 수 있습니다.

## <a name="see-also"></a>참조

[Visual Studio 프로젝트 - C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Visual Studio의 C++ 프로젝트 형식](../../build/reference/visual-cpp-project-types.md)<br/>
[개념](../../atl/active-template-library-atl-concepts.md)
