---
title: 프레임워크의 대화 상자 구성 요소
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
ms.openlocfilehash: 15d01924be811a9c9ec8ea333870f444bf9aa61a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685827"
---
# <a name="dialog-box-components-in-the-framework"></a>프레임워크의 대화 상자 구성 요소

MFC 프레임 워크에서 대화 상자에는 다음과 같은 두 가지 구성 요소가 있습니다.

- 대화 상자의 컨트롤 및 해당 배치를 지정 하는 대화 상자 템플릿 리소스입니다.

   대화 상자 리소스는 Windows에서 대화 상자 창을 만들고 표시 하는 데 사용할 수 있는 대화 상자 템플릿을 저장 합니다. 템플릿은 대화 상자의 컨트롤 크기, 위치, 스타일, 형식 및 위치를 포함 하 여 대화 상자의 특성을 지정 합니다. 일반적으로 리소스로 저장 된 대화 상자 템플릿을 사용 하지만 메모리에서 고유한 템플릿을 만들 수도 있습니다.

- 대화 상자를 관리 하기 위한 프로그래밍 인터페이스를 제공 하기 위해 [CDialog](../mfc/reference/cdialog-class.md)에서 파생 된 대화 상자 클래스입니다.

   대화 상자는 창이 며 표시 될 때 Windows 창에 연결 됩니다. 대화 상자 창이 만들어지면 대화 상자 템플릿 리소스는 대화 상자에 대 한 자식 창 컨트롤을 만들기 위한 템플릿으로 사용 됩니다.

## <a name="see-also"></a>참조

[대화 상자](../mfc/dialog-boxes.md)<br/>
[MFC에서 대화 상자 작업](../mfc/life-cycle-of-a-dialog-box.md)
