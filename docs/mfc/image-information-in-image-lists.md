---
description: '자세히 알아보기: 이미지 목록의 이미지 정보'
title: 이미지 목록의 이미지 정보
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: c3a5f1cee0a06177d12b72673bf0ebf8e1a73933
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290143"
---
# <a name="image-information-in-image-lists"></a>이미지 목록의 이미지 정보

[CImageList](reference/cimagelist-class.md) 에는 이미지 목록에서 정보를 검색 하는 많은 함수가 포함 되어 있습니다. [Getimageinfo](reference/cimagelist-class.md#getimageinfo) 멤버 함수는 `IMAGEINFO` 이미지 및 마스크 비트맵의 핸들, 픽셀당 색 평면 수 및 비트 수를 비롯 한 단일 이미지에 대 한 정보로 구조를 채우고 이미지 비트맵 내에서 이미지의 경계 사각형입니다. 이 정보를 사용 하 여 이미지에 대 한 비트맵을 직접 조작할 수 있습니다.

[GetImageCount](reference/cimagelist-class.md#getimagecount) member 함수는 이미지 목록의 이미지 수를 검색 합니다.

[ExtractIcon](reference/cimagelist-class.md#extracticon) 멤버 함수를 사용 하 여 이미지 목록에서 이미지 및 마스크를 기반으로 아이콘을 만들 수 있습니다. 함수는 새 아이콘의 핸들을 반환 합니다.

## <a name="see-also"></a>참고 항목

[CImageList 사용](using-cimagelist.md)<br/>
[컨트롤](controls-mfc.md)
