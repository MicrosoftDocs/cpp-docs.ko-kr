---
description: CImageList 사용에 대 한 자세한 정보
title: CImageList 사용
ms.date: 11/04/2016
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: 9e0126e3d5b083dc4a88bfb1ca2130be0e9fbaaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202537"
---
# <a name="using-cimagelist"></a>CImageList 사용

[CImageList](../mfc/reference/cimagelist-class.md)클래스에 의해 표현 되는 이미지 목록은 각각 인덱스에서 참조할 수 있는 동일한 크기의 이미지 컬렉션입니다. 이미지 목록은 많은 아이콘이 나 비트맵 집합을 효율적으로 관리 하는 데 사용 됩니다. 이미지 목록은 windows가 아니기 때문에 컨트롤이 아닙니다. 그러나 목록 컨트롤 ([CListCtrl](../mfc/reference/clistctrl-class.md)), 트리 컨트롤 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 및 탭 컨트롤 ([ctabctrl](../mfc/reference/ctabctrl-class.md))을 비롯 한 다양 한 형식의 컨트롤과 함께 사용 됩니다.

이미지 목록의 모든 이미지는 화면 장치 형식의 단일 와이드 비트맵에 포함 되어 있습니다. 이미지 목록에는 투명 하 게 이미지를 그리는 데 사용 되는 마스크를 포함 하는 단색 비트맵 (아이콘 스타일)이 포함 될 수도 있습니다. `CImageList` 이미지를 그리거나, 이미지 목록을 만들고 삭제 하 고, 이미지를 추가 및 제거 하 고, 이미지를 바꾸고, 이미지를 끌 수 있도록 하는 멤버 함수를 제공 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [이미지 목록의 유형](../mfc/types-of-image-lists.md)

- [이미지 목록 사용](../mfc/using-an-image-list.md)

- [이미지 목록 조작](../mfc/manipulating-image-lists.md)

- [이미지 목록에서 이미지 그리기](../mfc/drawing-images-from-an-image-list.md)

- [이미지 목록의 이미지 오버레이](../mfc/image-overlays-in-image-lists.md)

- [이미지 목록에서 이미지 끌기](../mfc/dragging-images-from-an-image-list.md)

- [이미지 목록의 이미지 정보](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>참고 항목

[컨트롤](../mfc/controls-mfc.md)
