---
title: 이미지 목록 사용 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4dc30d418ae57205e4566dad7f490a773321768e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391672"
---
# <a name="using-an-image-list"></a>이미지 목록 사용

이미지 목록의 일반적인 사용량 아래의 패턴을 따릅니다.

- 생성을 [CImageList](../mfc/reference/cimagelist-class.md) 개체 및 오버 로드 중 하나를 호출 해당 [만들기](../mfc/reference/cimagelist-class.md#create) 이미지 목록 만들기에 연결 하는 함수는 `CImageList` 개체입니다.

- 이미지 목록을 만들 때 이미지에 추가 하지 않은 경우 이미지는 이미지 목록 호출 하 여 추가 합니다 [추가](../mfc/reference/cimagelist-class.md#add) 또는 [읽기](../mfc/reference/cimagelist-class.md#read) 멤버 함수입니다.

- 해당 컨트롤의 적절 한 멤버 함수를 호출 하 여 이미지 목록 컨트롤을 연결 하거나 이미지 목록을 사용 하 여 직접 이미지 목록에서 이미지를 그릴 [그리기](../mfc/reference/cimagelist-class.md#draw) 멤버 함수입니다.

- 아마도 끌기를 위한 이미지 목록의 기본 제공 지원을 사용 하 여 이미지를 끌어서 놓을 수 있습니다.

> [!NOTE]
>  이미지 목록을 사용 하 여 만든 경우는 **새** 파기 해야 합니다 연산자는 `CImageList` 되어 완료 되 면 개체입니다.

## <a name="see-also"></a>참고 항목

[CImageList 사용](../mfc/using-cimagelist.md)<br/>
[컨트롤](../mfc/controls-mfc.md)

