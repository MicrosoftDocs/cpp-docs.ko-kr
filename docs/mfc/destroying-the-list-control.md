---
description: '자세히 알아보기: 목록 컨트롤 제거'
title: 목록 컨트롤 소멸시키기
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: b909889a6365de639f67359859641af6e2bc6525
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327835"
---
# <a name="destroying-the-list-control"></a>목록 컨트롤 소멸시키기

[CListCtrl](reference/clistctrl-class.md) 개체를 뷰 또는 대화 상자 클래스의 데이터 멤버로 포함 하는 경우 해당 소유자가 소멸 될 때 소멸 됩니다. [CListView](reference/clistview-class.md)를 사용 하는 경우 프레임 워크는 뷰를 소멸 시 컨트롤을 소멸 시킵니다.

목록 컨트롤이 아닌 응용 프로그램에 저장 되는 일부 목록 데이터를 정렬 하는 경우에는 해당 할당 취소를 정렬 해야 합니다. 자세한 내용은 Windows SDK에서 [콜백 항목 및 콜백 마스크](/windows/win32/Controls/using-list-view-controls) 를 참조 하세요.

또한 사용자가 만들고 목록 컨트롤 개체와 연결 된 모든 이미지 목록의 할당을 취소 해야 합니다.

## <a name="see-also"></a>참고 항목

[CListCtrl 사용](using-clistctrl.md)<br/>
[컨트롤](controls-mfc.md)
