---
description: '자세히 알아보기: 트리 컨트롤 항목 정보'
title: 트리 컨트롤 항목 정보
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
ms.openlocfilehash: ced75bdf6ed6a10e3a34536adf4af0ed1c7e0c86
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264143"
---
# <a name="tree-control-item-information"></a>트리 컨트롤 항목 정보

Tree controls ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))에는 컨트롤의 항목에 대 한 정보를 검색 하는 다양 한 멤버 함수가 있습니다. [GetItem](../mfc/reference/ctreectrl-class.md#getitem) 멤버 함수는 항목과 연결 된 데이터의 일부 또는 전체를 검색 합니다. 이 데이터에는 항목의 텍스트, 상태, 이미지, 자식 항목 수 및 응용 프로그램 정의 32 비트 데이터 값이 포함 될 수 있습니다. 항목과 연결 된 데이터의 일부 또는 모두를 설정할 수 있는 [SetItem](../mfc/reference/ctreectrl-class.md#setitem) 함수도 있습니다.

[Getitemstate](../mfc/reference/ctreectrl-class.md#getitemstate), [getitemstate](../mfc/reference/ctreectrl-class.md#getitemtext), [Getitemdata](../mfc/reference/ctreectrl-class.md#getitemdata)및 [getitemstate](../mfc/reference/ctreectrl-class.md#getitemimage) 멤버 함수는 항목의 개별 특성을 검색 합니다. 이러한 각 함수에는 항목의 특성을 설정 하기 위한 해당 Set 함수가 있습니다.

[GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) member 함수는 현재 항목에 대해 지정 된 관계를 가진 트리 컨트롤 항목을 검색 합니다. 이 함수는 항목의 부모, 다음 또는 이전 표시 항목, 첫 번째 자식 항목 등을 검색할 수 있습니다. 또한 [Getrootitem](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [getrootitem](../mfc/reference/ctreectrl-class.md#getselecteditem)및 [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem)등의 트리를 트래버스 하는 멤버 함수도 있습니다.

[Getitemrect](../mfc/reference/ctreectrl-class.md#getitemrect) 멤버 함수는 트리 컨트롤 항목에 대 한 경계 사각형을 검색 합니다. [Getcount](../mfc/reference/ctreectrl-class.md#getcount) 및 [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) 멤버 함수는 트리 컨트롤의 항목 수와 트리 컨트롤의 창에 현재 표시 되는 항목 수를 각각 검색 합니다. [Ensurevisible\](../mfc/reference/ctreectrl-class.md#ensurevisible) 멤버 함수를 호출 하 여 특정 항목이 표시 되도록 할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CTreeCtrl 사용](../mfc/using-ctreectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
