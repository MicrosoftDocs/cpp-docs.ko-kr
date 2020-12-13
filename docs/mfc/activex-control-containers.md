---
description: '자세한 정보: ActiveX 컨트롤 컨테이너'
title: ActiveX 컨트롤 컨테이너
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 6de379cc152ff35e16366c1b5e920bf3548f4cd4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339110"
---
# <a name="activex-control-containers"></a>ActiveX 컨트롤 컨테이너

ActiveX 컨트롤 컨테이너는 ActiveX 컨트롤을 완전히 지원하는 컨테이너이며, 이를 고유한 창 또는 대화 상자에 포함할 수 있습니다. ActiveX 컨트롤은 여러 개발 프로젝트에서 사용할 수 있는 재사용 가능한 소프트웨어 요소입니다. 컨트롤은 애플리케이션의 사용자가 데이터베이스에 액세스하고, 데이터를 모니터링하고, 애플리케이션 내에서 여러 항목을 선택할 수 있게 해줍니다. ActiveX 컨트롤에 대 한 자세한 내용은 [MFC Activex 컨트롤](mfc-activex-controls.md)문서를 참조 하세요.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. 자세한 내용은 [ActiveX Controls](activex-controls.md)을 참조 하세요.

일반적으로 프로젝트에서 컨트롤 컨테이너에는 다음 두 가지 형식이 사용됩니다.

- 대화 상자의 특정 위치에서 ActiveX 컨트롤이 사용되는 대화 상자 및 대화 상자와 비슷한 창(예: 폼 뷰).

- ActiveX 컨트롤이 도구 모음 또는 사용자 창의 다른 위치에서 사용되는 애플리케이션의 창.

ActiveX 컨트롤 컨테이너는 노출 된 [메서드](mfc-activex-controls-methods.md) 및 [속성](mfc-activex-controls-properties.md)을 통해 컨트롤과 상호 작용 합니다. 컨트롤 컨테이너가 액세스하고 수정할 수 있는 이러한 메서드 및 속성은 ActiveX 컨트롤 컨테이너 프로젝트에서 래퍼 클래스를 통해 액세스됩니다. 포함 된 ActiveX 컨트롤은 이벤트가 발생 했음을 컨테이너에 알리기 위해 [이벤트](mfc-activex-controls-events.md) 를 발생 시켜 컨테이너와 상호 작용할 수도 있습니다. 컨트롤 컨테이너는 이러한 알림에 따라 작업을 수행할지 여부를 선택할 수 있습니다.

추가 문서에서는 ActiveX 컨트롤 컨테이너 프로젝트 만들기부터 Visual C++로 작성된 ActiveX 컨트롤 컨테이너와 관련된 기본 구현 문제까지 여러 가지 항목에 대해 설명합니다.

- [MFC ActiveX 컨트롤 컨테이너 만들기](reference/creating-an-mfc-activex-control-container.md)

- [ActiveX 컨트롤용 컨테이너](containers-for-activex-controls.md)

- [ActiveX 컨트롤 컨테이너: ActiveX 컨트롤 포함 수동 사용](activex-control-containers-manually-enabling-activex-control-containment.md)

- [ActiveX 컨트롤 컨테이너: 컨트롤 컨테이너 응용 프로그램에 컨트롤 삽입](inserting-a-control-into-a-control-container-application.md)

- [ActiveX 컨트롤 컨테이너: ActiveX 컨트롤을 멤버 변수에 연결](activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [ActiveX 컨트롤 컨테이너: ActiveX 컨트롤의 이벤트 처리](activex-control-containers-handling-events-from-an-activex-control.md)

- [ActiveX 컨트롤 컨테이너: 컨트롤 속성 보기 및 수정](activex-control-containers-viewing-and-modifying-control-properties.md)

- [ActiveX 컨트롤 컨테이너: activex 컨트롤 컨테이너에서 ActiveX 컨트롤 프로그래밍](programming-activex-controls-in-a-activex-control-container.md)

- [ActiveX 컨트롤 컨테이너: 대화 상자가 아닌 컨테이너에서 컨트롤 사용](activex-control-containers-using-controls-in-a-non-dialog-container.md)

대화 상자에서 ActiveX 컨트롤을 사용 하는 방법에 대 한 자세한 내용은 [대화 상자 편집기](../windows/dialog-editor.md) 항목을 참조 하세요.

Visual C++ 및 MFC ActiveX 컨트롤 클래스를 사용 하 여 ActiveX 컨트롤을 개발 하는 방법에 대 한 자세한 내용을 설명 하는 문서 목록은 [Mfc activex 컨트롤](mfc-activex-controls.md)을 참조 하세요. 이러한 문서는 기능적 범주에 따라 그룹화되어 있습니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
