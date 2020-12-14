---
description: '자세히 알아보기: 이미지 목록 사용'
title: 이미지 목록 사용
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 92587bd80a4f613a04cae22322ab258e9869d247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202693"
---
# <a name="using-an-image-list"></a>이미지 목록 사용

이미지 목록의 일반적인 사용법은 다음 패턴을 따릅니다.

- [CImageList](../mfc/reference/cimagelist-class.md) 개체를 생성 하 고 [create](../mfc/reference/cimagelist-class.md#create) 함수의 오버 로드 중 하나를 호출 하 여 이미지 목록을 만들고이를 개체에 연결 `CImageList` 합니다.

- 이미지 목록을 만들 때 이미지를 추가 하지 않은 경우 [추가](../mfc/reference/cimagelist-class.md#add) 또는 [읽기](../mfc/reference/cimagelist-class.md#read) 멤버 함수를 호출 하 여 이미지 목록에 이미지를 추가 합니다.

- 해당 컨트롤의 적절 한 멤버 함수를 호출 하 여 이미지 목록을 컨트롤과 연결 하거나 이미지 목록의 [그리기](../mfc/reference/cimagelist-class.md#draw) 멤버 함수를 사용 하 여 이미지 목록에서 이미지를 직접 그립니다.

- 사용자가 이미지를 끌 때 이미지 목록의 기본 제공 지원을 사용 하 여 이미지를 끌 수 있습니다.

> [!NOTE]
> 연산자를 사용 하 여 이미지 목록을 만든 경우 개체를 사용 하 여 **`new`** 작업을 완료 하면 개체를 삭제 해야 합니다 `CImageList` .

## <a name="see-also"></a>참고 항목

[CImageList 사용](../mfc/using-cimagelist.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
