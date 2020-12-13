---
description: '자세히 알아보기: 목록 컨트롤 스타일 변경'
title: 목록 컨트롤 스타일 변경
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: a6712baf5ea1e161ec1fd73e25ea01fedd650670
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339737"
---
# <a name="changing-list-control-styles"></a>목록 컨트롤 스타일 변경

목록 컨트롤 ([CListCtrl](reference/clistctrl-class.md))의 창 스타일을 만든 후 언제 든 지 변경할 수 있습니다. 창 스타일을 변경 하 여 컨트롤에서 사용 하는 뷰의 종류를 변경 합니다. 예를 들어 탐색기를 에뮬레이트 하기 위해 메뉴 항목 또는 도구 모음 단추를 제공 하 여 여러 보기 간에 컨트롤을 전환할 수 있습니다. 아이콘 보기, 목록 뷰 등이 있습니다.

예를 들어 사용자가 메뉴 항목을 선택할 때 [Getwindowlong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) 을 호출 하 여 컨트롤의 현재 스타일을 검색 한 다음 [setwindowlong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) 을 호출 하 여 스타일을 다시 설정할 수 있습니다. 자세한 내용은 Windows SDK에서 [목록 뷰 컨트롤 사용](/windows/win32/Controls/using-list-view-controls) 을 참조 하세요.

사용 가능한 스타일은 [만들기](reference/clistctrl-class.md#create)에 나열 됩니다. 스타일 **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST** 및 **LVS_REPORT** 는 네 개의 목록 컨트롤 뷰를 지정 합니다.

## <a name="extended-styles"></a>확장 스타일

목록 컨트롤의 표준 스타일 외에도 확장 스타일 이라고 하는 다른 집합이 있습니다. Windows SDK [확장 목록 뷰 스타일](/windows/win32/Controls/extended-list-view-styles) 에서 설명 하는 이러한 스타일은 목록 컨트롤의 동작을 사용자 지정 하는 다양 한 유용한 기능을 제공 합니다. 특정 스타일의 동작을 구현 하려면 (예: 가리킨 항목 선택) [CListCtrl:: SetExtendedStyle](reference/clistctrl-class.md#setextendedstyle)를 호출 하 여 필요한 스타일을 전달 합니다. 다음 예제에서는 함수 호출을 보여 줍니다.

[!code-cpp[NVC_MFCControlLadenDialog#22](codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> 가리키기 선택이 작동 하려면 **LVS_EX_ONECLICKACTIVATE** 또는 **LVS_EX_TWOCLICKACTIVATE** 설정 되어 있어야 합니다.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](using-clistctrl.md)<br/>
[컨트롤](controls-mfc.md)
