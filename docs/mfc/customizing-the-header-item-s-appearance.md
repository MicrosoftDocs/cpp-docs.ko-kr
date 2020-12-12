---
description: '자세한 정보: 머리글 항목&#39;s 모양 사용자 지정'
title: 머리글 항목&#39;s 모양 사용자 지정
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 9cddb0f30dc2b7183952bd114990d1a608782ec3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309370"
---
# <a name="customizing-the-header-item39s-appearance"></a>머리글 항목&#39;s 모양 사용자 지정

헤더 컨트롤 ([CHeaderCtrl:: create](reference/cheaderctrl-class.md#create))을 처음 만들 때 *dwstyle* 매개 변수를 설정 하면 헤더 항목의 모양 및 동작을 정의 하거나 헤더 컨트롤의 동작을 정의할 수 있습니다.

다음은 설정할 수 있는 스타일 및 해당 용도에 대 한 샘플링입니다.

- 머리글 항목을 누름 단추 처럼 보이게 하려면 **HDS_BUTTONS** 스타일을 사용 합니다.

   Microsoft Outlook에서와 같이 특정 열을 기준으로 데이터를 정렬 하는 것과 같이 머리글 항목에 대 한 마우스 클릭에 대 한 응답으로 작업을 수행 하려는 경우이 스타일을 사용 합니다.

- 마우스 커서가 지나갈 때 헤더 항목에 "핫 추적" 모양을 지정 하려면 **HDS_HOTTRACK** 스타일을 사용 합니다.

   핫 트래킹은 포인터가 아닌 평평한 막대에서 항목을 지나갈 때 3D 윤곽선을 표시 합니다.

- 헤더 컨트롤을 숨겨야 함을 나타내려면 **HDS_HIDDEN** 스타일을 사용 합니다.

   **HDS_HIDDEN** 스타일은 헤더 컨트롤이 시각적 컨트롤이 아니라 데이터 컨테이너로 사용 됨을 나타냅니다. 이 스타일은 컨트롤을 자동으로 숨기지 않지만 대신의 동작에 영향을 줍니다 `CHeaderCtrl::Layout` . 구조체의 *cy* 멤버에서 반환 된 값은 `WINDOWPOS` 컨트롤이 사용자에 게 표시 되지 않아야 함을 나타내는 0이 됩니다.

이러한 속성에 대 한 자세한 내용은 Windows SDK [항목](/windows/win32/Controls/header-controls) 을 참조 하세요. 헤더 컨트롤에 항목을 추가 하는 방법에 대 한 자세한 내용은 [헤더 컨트롤에 항목 추가](adding-items-to-the-header-control.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CHeaderCtrl 사용](using-cheaderctrl.md)<br/>
[컨트롤](controls-mfc.md)
