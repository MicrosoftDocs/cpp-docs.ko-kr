---
title: 이미지 목록의 이미지 오버레이
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: ec795193a28a68d8aee61e9932481a89c4b3e8e0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508384"
---
# <a name="image-overlays-in-image-lists"></a>이미지 목록의 이미지 오버레이

모든 이미지 목록 ([CImageList](../mfc/reference/cimagelist-class.md))에는 오버레이 마스크로 사용할 이미지 목록이 포함 되어 있습니다. "오버레이 마스크"는 다른 이미지 위에 투명 하 게 그려진 이미지입니다. 모든 이미지를 오버레이 마스크로 사용할 수 있습니다. 이미지 목록 마다 오버레이 마스크를 4 개까지 지정할 수 있습니다.

[SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) 멤버 함수, 이미지의 인덱스 및 오버레이 마스크의 인덱스를 사용 하 여 오버레이 마스크 목록에 이미지의 인덱스를 추가 합니다. 오버레이 마스크의 인덱스는 0부터 시작 하는 것이 아니라 1부터 시작 합니다.

에 대 `Draw`한 단일 호출을 사용 하 여 이미지에 오버레이 마스크를 그릴 수 있습니다. 매개 변수에는 그릴 이미지의 인덱스와 오버레이 마스크의 인덱스가 포함 됩니다. [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) 매크로를 사용 하 여 오버레이 마스크의 인덱스를 지정 해야 합니다. [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) 멤버 함수를 호출할 때 오버레이 이미지를 지정할 수도 있습니다.

## <a name="see-also"></a>참고자료

[CImageList 사용](../mfc/using-cimagelist.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
