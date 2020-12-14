---
description: '자세히 알아보기: 이미지 목록 조작'
title: 이미지 목록 조작
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: dc2b136e1aed5266ea7cc910cf10839f59dfcf00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281134"
---
# <a name="manipulating-image-lists"></a>이미지 목록 조작

[Replace](reference/cimagelist-class.md#replace) member 함수는 이미지 목록의 이미지 ([CImageList](reference/cimagelist-class.md))를 새 이미지로 바꿉니다. 또한 이 기능은 이미지 목록 개체에서 이미지 수를 동적으로 늘려야 할 경우에 유용합니다. [SetImageCount](reference/cimagelist-class.md#setimagecount) 함수는 이미지 목록에 저장 된 이미지의 수를 동적으로 변경 합니다. 이미지 목록의 크기를 늘리면를 호출 `Replace` 하 여 새 이미지 슬롯에 이미지를 추가 합니다. 이미지 목록의 크기를 줄이면 새 크기를 넘어서는 이미지가 비워집니다.

[Remove](reference/cimagelist-class.md#remove) member 함수는 이미지 목록에서 이미지를 제거 합니다. [Copy](reference/cimagelist-class.md#copy) 멤버 함수는 이미지 목록 내에서 이미지를 복사 하거나 교환할 수 있습니다. 이 함수에서는 소스 이미지를 대상 인덱스에 복사해야 하는지 또는 소스와 대상 이미지를 스왑해야 하는지를 나타낼 수 있습니다.

두 개의 이미지 목록을 병합 하 여 새 이미지 목록을 만들려면 [create](reference/cimagelist-class.md#create) member 함수의 적절 한 오버 로드를 사용 합니다. 의이 오버 로드는 `Create` 기존 이미지 목록의 첫 번째 이미지를 병합 하 고 결과 이미지를 새 이미지 목록 개체에 저장 합니다. 새 이미지는 그리기로 생성되고, 두 번째 이미지는 첫 번째 이미지 위에 투명하게 표시됩니다. 새 이미지에 대한 마스크는 두 개의 기존 이미지에 대한 마스크의 비트에서 논리적 OR 연산을 수행한 결과입니다.

이 작업은 모든 이미지가 병합되고 새 이미지 목록 개체에 추가될 때까지 반복됩니다.

[Write](reference/cimagelist-class.md#write) 멤버 함수를 호출 하 여 보관에 이미지 정보를 쓰고 [읽기](reference/cimagelist-class.md#read) 멤버 함수를 호출 하 여 다시 읽을 수 있습니다.

[Getsafehandle](reference/cimagelist-class.md#getsafehandle), [Attach](reference/cimagelist-class.md#attach)및 [Detach](reference/cimagelist-class.md#detach) 멤버 함수를 사용 하면 개체에 연결 된 이미지 목록의 핸들을 조작할 수 있으며 `CImageList` , [deleteimagelist](reference/cimagelist-class.md#deleteimagelist) 멤버 함수는 개체를 삭제 하지 않고 이미지 목록을 삭제 합니다 `CImageList` .

## <a name="see-also"></a>참고 항목

[CImageList 사용](using-cimagelist.md)<br/>
[컨트롤](controls-mfc.md)
