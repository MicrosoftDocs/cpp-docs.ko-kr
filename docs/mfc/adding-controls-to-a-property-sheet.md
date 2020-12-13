---
description: '자세히 알아보기: 속성 시트에 컨트롤 추가'
title: 속성 시트에 컨트롤 추가
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: e220d08b46f1db7e09ad1f1398731ce7a98f2dc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339075"
---
# <a name="adding-controls-to-a-property-sheet"></a>속성 시트에 컨트롤 추가

기본적으로 속성 시트는 속성 페이지, 탭 인덱스 및 확인, 취소 및 적용 단추에 대 한 창 영역을 할당 합니다. 모덜리스 속성 시트에는 확인, 취소 및 적용 단추가 없습니다. 속성 시트에 다른 컨트롤을 추가할 수 있습니다. 예를 들어 속성 페이지 영역의 오른쪽에 미리 보기 창을 추가 하 여 외부 개체에 적용 된 것과 같은 현재 설정을 사용자에 게 표시할 수 있습니다.

처리기의 속성 시트 대화 상자에 컨트롤을 추가할 수 있습니다 `OnCreate` . 일반적으로 추가 컨트롤을 수용 하려면 속성 시트 대화 상자의 크기를 확장 해야 합니다. 기본 클래스 **CPropertySheet:: OnCreate** 를 호출한 후 [getwindowrect](reference/cwnd-class.md#getwindowrect) 를 호출 하 여 현재 할당 된 속성 시트 창의 너비와 높이를 가져오고, 사각형의 크기를 확장 하 고, [movewindow](reference/cwnd-class.md#movewindow) 를 호출 하 여 속성 시트 창의 크기를 변경 합니다.

## <a name="see-also"></a>참고 항목

[속성 시트](property-sheets-mfc.md)<br/>
[CPropertyPage 클래스](reference/cpropertypage-class.md)<br/>
[CPropertySheet 클래스](reference/cpropertysheet-class.md)
