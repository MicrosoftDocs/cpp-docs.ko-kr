---
description: '자세히 알아보기: 컨트롤에 열 추가 (보고서 뷰)'
title: 컨트롤에 열 추가(보고서 뷰)
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: 62e874f77d326b80a362791888e75df0a92781d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339099"
---
# <a name="adding-columns-to-the-control-report-view"></a>컨트롤에 열 추가(보고서 뷰)

> [!NOTE]
> 다음 프로시저는 [CListView](reference/clistview-class.md) 또는 [CListCtrl](reference/clistctrl-class.md) 개체에 적용 됩니다.

목록 컨트롤이 보고서 뷰에 있는 경우 각 목록 컨트롤 항목의 여러 하위 항목을 구성 하는 방법을 제공 하는 열이 표시 됩니다. 이 조직은 목록 컨트롤의 열과 목록 컨트롤 항목의 연결 된 하위 항목 사이에 일 대 일 대응을 사용 하 여 구현 됩니다. 하위 항목에 대 한 자세한 내용은 [컨트롤에 항목 추가](adding-items-to-the-control.md)를 참조 하세요. 보고서 보기의 목록 컨트롤 예제는 Windows 95 및 Windows 98 탐색기의 자세히 보기에서 제공 됩니다. 첫 번째 열에는 폴더, 파일 아이콘 및 레이블이 나열 됩니다. 기타 열 목록 파일 크기, 파일 형식, 마지막으로 수정한 날짜 등

열은 언제 든 지 목록 컨트롤에 추가할 수 있지만 컨트롤에서 스타일 비트가 설정 되어 있는 경우에만 열이 표시 됩니다 `LVS_REPORT` .

각 열에는 열에 레이블을 지정할 수 있고 사용자가 열의 크기를 조정할 수 있는 연결 된 헤더 항목 ( [CHeaderCtrl](reference/cheaderctrl-class.md)참조) 개체가 있습니다.

목록 컨트롤이 보고서 뷰를 지 원하는 경우 목록 컨트롤 항목에서 가능한 각 하위 항목에 대 한 열을 추가 해야 합니다. [Lvcolumn](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) 구조를 준비한 다음 [insertcolumn](reference/clistctrl-class.md#insertcolumn)에 대 한 호출을 수행 하 여 열을 추가 합니다. 필요한 열 (헤더 항목이 라고도 함)을 추가한 후에는 포함 헤더 컨트롤에 속하는 멤버 함수 및 스타일을 사용 하 여 순서를 변경할 수 있습니다. 자세한 내용은 [헤더 컨트롤에서 항목 순서](ordering-items-in-the-header-control.md)지정을 참조 하세요.

> [!NOTE]
> **LVS_NOCOLUMNHEADER** 스타일을 사용 하 여 목록 컨트롤을 만드는 경우에는 열 삽입 시도가 무시 됩니다.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](using-clistctrl.md)<br/>
[컨트롤](controls-mfc.md)
