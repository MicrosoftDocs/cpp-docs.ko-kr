---
description: '자세히 알아보기: Rich Edit 컨트롤 관련 클래스'
title: Rich Edit 컨트롤 관련 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
ms.openlocfilehash: b44c5a874c7f48c132f31483bf5ee73eafbe4da5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176680"
---
# <a name="classes-related-to-rich-edit-controls"></a>Rich Edit 컨트롤 관련 클래스

[CRichEditView](reference/cricheditview-class.md), [CRichEditDoc](reference/cricheditdoc-class.md)및 [CRichEditCntrItem](reference/cricheditcntritem-class.md) 클래스는 MFC의 문서/뷰 아키텍처 컨텍스트 내에서 rich edit 컨트롤 ([CRichEditCtrl](reference/cricheditctrl-class.md))의 기능을 제공 합니다. `CRichEditView` 텍스트의 텍스트와 서식 특성을 유지 합니다. `CRichEditDoc` 뷰에 있는 OLE 클라이언트 항목의 목록을 유지 관리 합니다. `CRichEditCntrItem` OLE 클라이언트 항목에 대 한 컨테이너 쪽 액세스를 제공 합니다. 의 내용을 수정 하려면 `CRichEditView` [CRichEditView:: GetRichEditCtrl](reference/cricheditview-class.md#getricheditctrl) 를 사용 하 여 기본 rich edit 컨트롤에 액세스 합니다.

## <a name="see-also"></a>참고 항목

[CRichEditCtrl 사용](using-cricheditctrl.md)<br/>
[컨트롤](controls-mfc.md)
