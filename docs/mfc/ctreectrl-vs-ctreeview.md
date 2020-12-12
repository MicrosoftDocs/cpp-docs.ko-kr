---
description: '자세히 알아보기: CTreeCtrl 및 CTreeView'
title: CTreeCtrl과 CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: edaf2662d483a23c7618a143ee4aabe7910cf121
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309422"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl과 CTreeView

MFC는 트리 컨트롤 [CTreeCtrl](reference/ctreectrl-class.md) 및 [ctreeview](reference/ctreeview-class.md)를 캡슐화 하는 두 개의 클래스를 제공 합니다. 각 클래스는 여러 상황에서 유용 합니다.

예 `CTreeCtrl` 를 들어 대화 상자에서 일반 자식 창 컨트롤이 필요한 경우를 사용 합니다. `CTreeCtrl`일반적인 대화 상자와 같이 창에 다른 자식 컨트롤이 있는 경우에는 특히를 사용 하는 것이 좋습니다.

트리 컨트롤이 `CTreeView` 문서/뷰 아키텍처에서 뷰 창 처럼 동작 하 게 하려는 경우와 트리 컨트롤을 사용 합니다. 는 `CTreeView` 프레임 창이 나 분할자 창의 전체 클라이언트 영역을 차지 합니다. 부모 창의 크기를 조정 하면 자동으로 크기가 조정 되 고 메뉴, 액셀러레이터 키 및 도구 모음에서 명령 메시지를 처리할 수 있습니다. 트리 컨트롤에는 트리를 표시 하는 데 필요한 데이터가 포함 되어 있기 때문에 해당 문서 개체는 복잡할 필요는 없습니다. 문서 템플릿에서 [CDocument](reference/cdocument-class.md) 를 문서 형식으로 사용할 수도 있습니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](using-ctreectrl.md)<br/>
[컨트롤](controls-mfc.md)
