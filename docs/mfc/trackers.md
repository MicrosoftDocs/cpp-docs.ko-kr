---
description: '에 대 한 자세한 정보: 추적기'
title: 추적기
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
ms.openlocfilehash: e82766ecfabf2b5ebb0147b9f2c462f3b4460869
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264249"
---
# <a name="trackers"></a>추적기

[CRectTracker](../mfc/reference/crecttracker-class.md) 클래스는 다양 한 표시 스타일을 제공 하 여 응용 프로그램의 사각형 항목과 사용자의 사용자 인터페이스를 제공 합니다. 이러한 스타일은 단색, 빗금 또는 점선 테두리를 포함 합니다. 항목을 포함 하는 해치 패턴입니다. 테두리의 바깥쪽 이나 내부에 있을 수 있는 크기 조정 핸들 추적기는 OLE 항목, 즉에서 파생 된 개체와 함께 사용 되는 경우가 많습니다 `COleClientItem` . Tracker 사각형은 항목의 현재 상태에 대 한 시각적 신호를 제공 합니다.

MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md) 는 컨테이너 응용 프로그램의 관점에서 추적기 및 OLE 클라이언트 항목을 사용 하는 일반적인 인터페이스를 보여 줍니다. Tracker 개체의 다양 한 스타일 및 기능에 대 한 데모는 MFC 일반 샘플 [추적기](../overview/visual-cpp-samples.md)를 참조 하세요.

OLE 응용 프로그램에서 추적기를 구현 하는 방법에 대 한 자세한 내용은 [추적기: Ole 응용 프로그램에서 추적기 구현](../mfc/trackers-implementing-trackers-in-your-ole-application.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem 클래스](../mfc/reference/coleclientitem-class.md)
