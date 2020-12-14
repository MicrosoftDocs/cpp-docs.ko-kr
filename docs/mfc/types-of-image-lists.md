---
description: '자세히 알아보기: 이미지 목록 형식'
title: 이미지 목록 형식
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
ms.openlocfilehash: be18a523db366813a236fd4fd94bbb001345f0d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263740"
---
# <a name="types-of-image-lists"></a>이미지 목록 형식

[CImageList](../mfc/reference/cimagelist-class.md)(이미지 목록)의 두 가지 유형이 있습니다 (nonmasked). "Nonmasked 이미지 목록"은 하나 이상의 이미지를 포함 하는 색 비트맵으로 구성 됩니다. "마스킹된 이미지 목록"은 같은 크기의 두 비트맵으로 구성 됩니다. 첫 번째는 이미지를 포함 하는 색 비트맵 이며, 두 번째는 첫 번째 비트맵의 각 이미지에 대해 하나씩, 일련의 마스크를 포함 하는 단색 비트맵입니다.

멤버 함수의 오버 로드 중 하나는 `Create` 이미지 목록이 마스킹 되었는지 여부를 나타내는 플래그를 사용 합니다. 다른 오버 로드는 마스킹된 이미지 목록을 만듭니다.

Nonmasked 이미지를 그리면 대상 장치 컨텍스트에 복사 됩니다. 즉, 장치 컨텍스트의 기존 배경색 위에 그려집니다. 마스킹된 이미지를 그리면 이미지의 비트가 마스크의 비트와 결합 됩니다. 일반적으로 비트맵에서 대상 장치 컨텍스트의 배경색이 표시 되는 투명 영역을 생성 합니다. 마스킹된 이미지를 그릴 때 여러 그리기 스타일을 지정할 수 있습니다. 예를 들어 이미지를 디더링 하 여 선택한 개체를 나타내도록 지정할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CImageList 사용](../mfc/using-cimagelist.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
