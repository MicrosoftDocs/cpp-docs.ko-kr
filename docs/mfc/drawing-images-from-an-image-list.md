---
description: '자세히 알아보기: 이미지 목록에서 이미지 그리기'
title: 이미지 목록에서 이미지 그리기
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: 2c413092e1e7568488a091acd2b0db175d03dab9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283461"
---
# <a name="drawing-images-from-an-image-list"></a>이미지 목록에서 이미지 그리기

이미지를 그리려면 [CImageList::D raw](reference/cimagelist-class.md#draw) 멤버 함수를 사용 합니다. 장치 컨텍스트 개체에 대 한 포인터, 그릴 이미지의 인덱스, 이미지를 그릴 장치 컨텍스트의 위치 및 그리기 스타일을 나타내는 플래그 집합을 지정 합니다.

**ILD_TRANSPARENT** 스타일을 지정 하면에서는 `Draw` 2 단계 프로세스를 사용 하 여 마스킹된 이미지를 그립니다. 첫 번째는 이미지의 비트와 마스크의 비트에 대해 논리적 AND 연산을 수행 합니다. 그런 다음 첫 번째 작업의 결과와 대상 장치 컨텍스트의 백그라운드 비트에 대해 논리 XOR 연산을 수행 합니다. 이 프로세스는 결과 이미지에 투명 영역을 만듭니다. 즉, 마스크의 각 흰색 비트 때문에 결과 이미지의 해당 비트가 투명 하 게 됩니다.

단색 배경에 마스킹된 이미지를 그리기 전에 [SetBkColor](reference/cimagelist-class.md#setbkcolor) 멤버 함수를 사용 하 여 이미지 목록의 배경색을 대상과 동일한 색으로 설정 해야 합니다. 색을 설정 하면 이미지에서 투명 한 영역을 만들 필요가 없으며 `Draw` 에서 이미지를 대상 장치 컨텍스트에 복사 하 여 성능이 크게 향상 될 수 있습니다. 이미지를 그리려면를 호출할 때 **ILD_NORMAL** 스타일을 지정 합니다 `Draw` .

언제 든 지 마스킹된 이미지 목록 ([CImageList](reference/cimagelist-class.md))에 대 한 배경색을 설정 하 여 단색 배경에 올바르게 그릴 수 있습니다. 배경색을 **CLR_NONE** 로 설정 하면 이미지는 기본적으로 투명 하 게 그려집니다. 이미지 목록의 배경색을 검색 하려면 [GetBkColor](reference/cimagelist-class.md#getbkcolor) 멤버 함수를 사용 합니다.

**ILD_BLEND25** 및 **ILD_BLEND50** 스타일은 시스템 강조 색을 사용 하 여 이미지를 디더링 합니다. 이러한 스타일은 마스킹된 이미지를 사용 하 여 사용자가 선택할 수 있는 개체를 나타내는 경우에 유용 합니다. 예를 들어 **ILD_BLEND50** 스타일을 사용 하 여 사용자가 이미지를 선택할 때 이미지를 그릴 수 있습니다.

Nonmasked 이미지는 래스터 작업을 사용 하 여 대상 장치 컨텍스트에 복사 됩니다 `SRCCOPY` . 장치 컨텍스트의 배경색에 관계 없이 이미지의 색은 동일 하 게 표시 됩니다. 또한에 지정 된 그리기 스타일은 `Draw` nonmasked 이미지의 모양에 영향을 주지 않습니다.

Draw 멤버 함수 외에도 다른 함수인 [DrawIndirect](reference/cimagelist-class.md#drawindirect)는 이미지를 렌더링 하는 기능을 확장 합니다. `DrawIndirect` 는 [Imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) 구조체를 매개 변수로 사용 합니다. 이 구조는 ROP (래스터 작업) 코드를 사용 하 여 현재 이미지의 렌더링을 사용자 지정 하는 데 사용할 수 있습니다. ROP 코드에 대 한 자세한 내용은 Windows SDK의 브러시로 [래스터 작업 코드](/windows/win32/gdi/raster-operation-codes) 및 [비트맵](/windows/win32/gdi/bitmaps-as-brushes) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CImageList 사용](using-cimagelist.md)<br/>
[컨트롤](controls-mfc.md)
