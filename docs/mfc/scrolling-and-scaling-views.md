---
description: '자세히 알아보기: 뷰 스크롤 및 크기 조정'
title: 뷰 스크롤 및 크기 조정
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: f18b774eadf875f61fcb1f3f3a8dc9e0e370f9a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217811"
---
# <a name="scrolling-and-scaling-views"></a>뷰 스크롤 및 크기 조정

MFC는 스크롤 및 뷰를 표시 하는 프레임 창의 크기에 맞게 자동으로 조정 되는 뷰를 지원 합니다. 클래스 `CScrollView` 는 두 종류의 뷰를 모두 지원 합니다.

스크롤 및 크기 조정에 대 한 자세한 내용은 *MFC 참조* 의 클래스 [CScrollView](../mfc/reference/cscrollview-class.md) 를 참조 하세요. 스크롤 예제를 보려면 [Scribble 샘플](../overview/visual-cpp-samples.md)을 참조 하세요.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- 뷰 스크롤

- 보기 크기 조정

- [뷰 좌표](/windows/win32/gdi/window-coordinate-system)

## <a name="scrolling-a-view"></a><a name="_core_scrolling_a_view"></a> 뷰 스크롤

문서 크기가 보기에 표시 될 수 있는 크기 보다 큰 경우가 많습니다. 이 문제는 문서의 데이터가 늘어나거나 사용자가 뷰를 프레임으로 사용 하는 창을 축소 하기 때문에 발생할 수 있습니다. 이 경우 뷰는 스크롤을 지원 해야 합니다.

모든 뷰에서는 `OnHScroll` 및 멤버 함수에서 스크롤 막대 메시지를 처리할 수 있습니다 `OnVScroll` . 이러한 함수에서 스크롤 막대 메시지 처리를 구현 하거나, 모든 작업을 직접 수행 하거나, 클래스를 사용 하 여 스크롤을 처리할 수 있습니다 `CScrollView` .

`CScrollView`은 다음을 수행합니다.

- 창 및 뷰포트 크기 및 매핑 모드를 관리 합니다.

- 스크롤 막대 메시지에 응답 하 여 자동으로 스크롤

"페이지" (사용자가 스크롤 막대 샤프트에서 클릭 하는 경우)와 "선" (사용자가 스크롤 화살표를 클릭 한 경우)에 대해 스크롤할 크기를 지정할 수 있습니다. 보기의 특성에 맞게 이러한 값을 계획 합니다. 예를 들어, 그래픽 뷰에 대해 1 픽셀 증분으로 스크롤할 수 있지만 텍스트 문서의 줄 높이를 기준으로 증가값은 증가 시킬 수 있습니다.

## <a name="scaling-a-view"></a><a name="_core_scaling_a_view"></a> 보기 크기 조정

뷰가 자동으로 프레임 창의 크기에 맞게 조정 되도록 하려면 스크롤 대신를 사용 하 여 크기를 `CScrollView` 조정 합니다. 논리적 보기는 창의 클라이언트 영역에 맞게 확대 또는 축소 됩니다. 배율이 조정 된 뷰에는 스크롤 막대가 없습니다.

## <a name="see-also"></a>참고 항목

[뷰 사용](../mfc/using-views.md)
