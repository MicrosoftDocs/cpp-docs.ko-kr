---
description: '자세히 알아보기: 탭 및 탭 컨트롤 특성'
title: 탭 및 탭 컨트롤 특성
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: 9b79e2ae6558d812fa96d0b62c07eb1c41176ee5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216355"
---
# <a name="tabs-and-tab-control-attributes"></a>탭 및 탭 컨트롤 특성

탭 컨트롤 ([Ctabctrl](../mfc/reference/ctabctrl-class.md))을 구성 하는 탭의 모양과 동작에 대 한 제어 기능이 크게 설정 되어 있습니다. 각 탭에는 레이블, 아이콘, 항목 상태 및 이와 연결 된 응용 프로그램 정의 32 비트 값이 있을 수 있습니다. 각 탭에 대해 아이콘, 레이블 또는 둘 다를 표시할 수 있습니다.

또한 각 탭 항목에는 누름, unpressed 또는 강조 됨의 세 가지 상태를 사용할 수 있습니다. 이 상태는 기존 탭 항목을 수정 하는 방법 으로만 설정할 수 있습니다. 기존 탭 항목을 수정 하려면 [GetItem](../mfc/reference/ctabctrl-class.md#getitem)에 대 한 호출을 사용 하 여 해당 항목을 검색 하 고, `TCITEM` 구조 (구체적으로 *dwstate* 및 *dwStateMask* 데이터 멤버)를 수정한 다음 `TCITEM` [SetItem](../mfc/reference/ctabctrl-class.md#setitem)에 대 한 호출을 사용 하 여 수정 된 구조체를 반환 합니다. 개체에 있는 모든 탭 항목의 항목 상태를 지워야 하는 경우 `CTabCtrl` [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall)를 호출 합니다. 이 함수는 현재 선택 된 항목을 제외 하 고 모든 탭 항목 또는 모든 항목의 상태를 다시 설정 합니다.

다음 코드는 모든 탭 항목의 상태를 지운 다음 세 번째 항목의 상태를 수정 합니다.

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

탭 특성에 대 한 자세한 내용은 Windows SDK 탭 [및 탭 특성](/windows/win32/Controls/tab-controls) 을 참조 하세요. 탭 컨트롤에 탭을 추가 하는 방법에 대 한 자세한 내용은이 항목의 뒷부분에 있는 [탭 컨트롤에 탭 추가](../mfc/adding-tabs-to-a-tab-control.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CTabCtrl 사용](../mfc/using-ctabctrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
