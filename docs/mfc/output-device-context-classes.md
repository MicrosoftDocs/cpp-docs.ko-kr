---
description: '자세히 알아보기: 출력 (장치 컨텍스트) 클래스'
title: 출력(디바이스 컨텍스트) 클래스
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: e148999f2423165e7026bf68970fe9fc145930d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331782"
---
# <a name="output-device-context-classes"></a>출력(디바이스 컨텍스트) 클래스

이러한 클래스는 Windows에서 사용할 수 있는 다양 한 유형의 장치 컨텍스트를 캡슐화 합니다.

다음 클래스 대부분은 Windows 장치 컨텍스트에 대 한 핸들을 캡슐화 합니다. 장치 컨텍스트는 디스플레이 또는 프린터와 같은 장치의 그리기 특성에 대 한 정보가 포함 된 Windows 개체입니다. 모든 그리기 호출은 장치 컨텍스트 개체를 통해 수행 됩니다. 에서 파생 된 추가 클래스는 `CDC` Windows 메타 파일에 대 한 지원을 포함 하 여 특수화 된 장치 컨텍스트 기능을 캡슐화 합니다.

[CDC](reference/cdc-class.md)<br/>
장치 컨텍스트의 기본 클래스입니다. 전체 표시에 액세스 하 고 프린터와 같은 표시 되지 않는 컨텍스트에 액세스 하는 데 직접 사용 됩니다.

[CPaintDC](reference/cpaintdc-class.md)<br/>
Windows의 멤버 함수에 사용 되는 표시 컨텍스트입니다 `OnPaint` . `BeginPaint`생성 시 및 소멸 시를 자동으로 호출 `EndPaint` 합니다.

[CClientDC](reference/cclientdc-class.md)<br/>
Windows 클라이언트 영역에 대 한 표시 컨텍스트입니다. 예를 들어 마우스 이벤트에 대 한 즉각적인 응답으로 그리기 위해 사용 됩니다.

[CWindowDC](reference/cwindowdc-class.md)<br/>
클라이언트 및 비클라이언트 영역을 포함 하 여 전체 창의 표시 컨텍스트입니다.

[CMetaFileDC](reference/cmetafiledc-class.md)<br/>
Windows 메타 파일에 대 한 장치 컨텍스트입니다. Windows 메타 파일에는 이미지를 만들기 위해 재생할 수 있는 GDI (그래픽 장치 인터페이스) 명령 시퀀스가 포함 되어 있습니다. 의 멤버 함수에 대 한 호출은 `CMetaFileDC` 메타 파일에 기록 됩니다.

## <a name="related-classes"></a>관련 클래스

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
좌표(x, y) 쌍을 저장합니다.

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
거리, 상대 위치 또는 쌍으로 이뤄진 값을 저장합니다.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
사각형 영역의 좌표를 저장합니다.

[CRgn](reference/crgn-class.md)<br/>
창 내에서 타원형, 다각형 또는 불규칙 한 영역을 조작 하기 위한 GDI 영역을 캡슐화 합니다. 클래스의 클리핑 멤버 함수와 함께 사용 `CDC` 됩니다.

[CRectTracker](reference/crecttracker-class.md)<br/>
사각형 개체의 크기를 조정 하 고 이동 하기 위한 사용자 인터페이스를 표시 하 고 처리 합니다.

[CColorDialog](reference/ccolordialog-class.md)<br/>
색을 선택할 때 표준 대화 상자를 제공 합니다.

[CFontDialog](reference/cfontdialog-class.md)<br/>
글꼴을 선택 하는 표준 대화 상자를 제공 합니다.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
파일 인쇄를 위한 표준 대화 상자를 제공 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
