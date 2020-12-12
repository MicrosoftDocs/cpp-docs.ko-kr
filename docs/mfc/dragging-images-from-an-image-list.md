---
description: '자세히 알아보기: 이미지 목록에서 이미지 끌기'
title: 이미지 목록에서 이미지 끌기
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 4d81be73484d32d9b26e5aa4ae48b7e550306493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118851"
---
# <a name="dragging-images-from-an-image-list"></a>이미지 목록에서 이미지 끌기

[CImageList](reference/cimagelist-class.md) 는 화면에서 이미지를 끌기 위한 함수를 포함 합니다. 끌기 함수는 커서의 깜박임을 사용 하지 않고 이미지를 색으로 부드럽게 이동 합니다. 마스킹된 이미지와 마스크 해제 된 이미지를 모두 끌 수 있습니다.

[Begindrag](reference/cimagelist-class.md#begindrag) 멤버 함수는 끌기 작업을 시작 합니다. 매개 변수에는 끌어올 이미지의 인덱스와 이미지 내 핫 스폿의 위치가 포함 됩니다. 핫 스폿은 끌기 함수가 이미지의 정확한 화면 위치로 인식 하는 단일 픽셀입니다. 일반적으로 응용 프로그램은 마우스 커서의 핫 스폿과 일치 하도록 핫 스폿을 설정 합니다. [Dragmove](reference/cimagelist-class.md#dragmove) 멤버 함수는 이미지를 새 위치로 이동 합니다.

[System.windows.dragdrop.dragenter>](reference/cimagelist-class.md#dragenter) 멤버 함수는 창 내에서 끌기 이미지의 초기 위치를 설정 하 고 위치에 이미지를 그립니다. 매개 변수에는 이미지를 그릴 창에 대 한 포인터와 창 내에서 초기 위치의 좌표를 지정 하는 점이 포함 됩니다. 좌표는 클라이언트 영역이 아니라 창의 왼쪽 위 모퉁이를 기준으로 합니다. 좌표를 매개 변수로 사용 하는 모든 이미지 끌기 함수의 경우에도 마찬가지입니다. 즉, 좌표를 지정할 때 테두리, 제목 표시줄 및 메뉴 모음 등의 창 요소 너비를 보정 해야 합니다. 를 호출할 때 **NULL** 창 핸들을 지정 하는 경우 `DragEnter` 끌기 함수는 바탕 화면 창과 연결 된 장치 컨텍스트에서 이미지를 그리고 좌표는 화면의 왼쪽 위 모퉁이를 기준으로 합니다.

`DragEnter` 끌기 작업을 수행 하는 동안 지정 된 창에 대 한 다른 모든 업데이트를 잠급니다. 끌기 작업을 수행 하는 동안 그리기를 수행 해야 하는 경우 (예: 끌어서 놓기 작업의 대상 강조 표시) [system.windows.dragdrop.dragleave>](reference/cimagelist-class.md#dragleave) 멤버 함수를 사용 하 여 끌어 온 이미지를 일시적으로 숨길 수 있습니다. [Dragshownolock](reference/cimagelist-class.md#dragshownolock) 멤버 함수를 사용할 수도 있습니다.

이미지 끌기를 완료 하면 [Enddrag](reference/cimagelist-class.md#enddrag) 를 호출 합니다.

[SetDragCursorImage](reference/cimagelist-class.md#setdragcursorimage) member 함수는 지정 된 이미지 (일반적으로 마우스 커서 이미지)와 현재 끌기 이미지를 결합 하 여 새 끌기 이미지를 만듭니다. 끌기 작업을 수행 하는 동안 끌기 함수는 새 이미지를 사용 하기 때문에를 호출한 후에는 Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) 함수를 사용 하 여 실제 마우스 커서를 숨겨야 합니다 `SetDragCursorImage` . 그렇지 않으면 끌기 작업 기간 동안 두 개의 마우스 커서가 있는 시스템에 표시 될 수 있습니다.

응용 프로그램에서를 호출 하면 `BeginDrag` 시스템은 임시 내부 이미지 목록을 만들고 지정 된 끌기 이미지를 내부 목록에 복사 합니다. [Getdragimage](reference/cimagelist-class.md#getdragimage) 멤버 함수를 사용 하 여 임시 끌어서 이미지 목록에 대 한 포인터를 검색할 수 있습니다. 또한 함수는 현재 끌기 위치와 끌기 위치를 기준으로 하는 끌기 이미지의 오프셋을 검색 합니다.

## <a name="see-also"></a>참고 항목

[CImageList 사용](using-cimagelist.md)<br/>
[컨트롤](controls-mfc.md)
