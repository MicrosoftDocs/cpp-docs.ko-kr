---
description: 파생 창 클래스에 대해 자세히 알아보세요.
title: 파생된 창 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: 9219267b5351f972257d9770f8e8b38039b85788
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335899"
---
# <a name="derived-window-classes"></a>파생된 창 클래스

[CWnd](reference/cwnd-class.md)에서 직접 창을 만들거나에서 새 창 클래스를 파생할 수 있습니다 `CWnd` . 이는 일반적으로 사용자 지정 창을 직접 만드는 방법입니다. 그러나 프레임 워크 프로그램에서 사용 되는 대부분의 windows는 `CWnd` MFC에서 제공 하는 파생 프레임 창 클래스 중 하나에서 만들어집니다.

## <a name="frame-window-classes"></a>프레임 창 클래스

[CFrameWnd](reference/cframewnd-class.md)<br/>
단일 문서 및 뷰를 프레임으로 사용 하는 SDI 프레임 창에 사용 됩니다. 프레임 창은 응용 프로그램의 주 프레임 창이 고 현재 문서에 대 한 프레임 창입니다.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
MDI 응용 프로그램의 주 프레임 창으로 사용 됩니다. 주 프레임 창은 모든 MDI 문서 창에 대 한 컨테이너 이며 메뉴 모음을 공유 합니다. MDI 프레임 창은 바탕 화면에 표시 되는 최상위 창입니다.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
MDI 주 프레임 창에서 열린 개별 문서에 사용 됩니다. 각 문서와 해당 뷰는 MDI 주 프레임 창에 포함 된 MDI 자식 프레임 창에 의해 포함 됩니다. MDI 자식 창은 일반적인 프레임 창과 비슷하지만 바탕 화면에 표시 되는 대신 MDI 프레임 창에 포함 되어 있습니다. 그러나 MDI 자식 창에는 자체의 메뉴 모음이 없으므로 해당 창에 포함 된 MDI 프레임 창의 메뉴 모음을 공유 해야 합니다.

자세한 내용은 [프레임 창](frame-windows.md)을 참조 하세요.

## <a name="other-window-classes-derived-from-cwnd"></a>CWnd에서 파생 된 다른 창 클래스

프레임 창 외에도 다음과 같은 몇 가지 주요 범주의 창을 파생 시킬 수 있습니다 `CWnd` .

*뷰*<br/>
뷰는 `CWnd` 파생 클래스 [CView](reference/cview-class.md) (또는 파생 클래스 중 하나)를 사용 하 여 만듭니다. 뷰는 문서에 첨부 되며 문서와 사용자 간의 중개자 역할을 합니다. 뷰는 일반적으로 SDI 프레임 창이 나 MDI 자식 프레임 창의 클라이언트 영역을 채우는 자식 창 (MDI 자식 아님) 이며, 도구 모음 및/또는 상태 표시줄에서 다루지 않는 클라이언트 영역의 일부입니다.

*대화 상자*<br/>
대화 상자는 `CWnd` -derived 클래스 [CDialog](reference/cdialog-class.md)를 사용 하 여 만듭니다.

*양식*<br/>
대화 상자와 같은 대화 상자 템플릿 리소스를 기반으로 하는 폼 보기는 [CFormView](reference/cformview-class.md), [CRecordView](reference/crecordview-class.md)또는 [CDaoRecordView](reference/cdaorecordview-class.md)클래스를 사용 하 여 만듭니다.

*컨트롤*<br/>
단추, 목록 상자, 콤보 상자 등의 컨트롤은에서 파생 된 다른 클래스를 사용 하 여 생성 됩니다 `CWnd` . [제어 항목](controls-mfc.md)을 참조 하세요.

*컨트롤 막대*<br/>
컨트롤을 포함 하는 자식 창입니다. 예제에는 도구 모음 및 상태 표시줄이 있습니다. [컨트롤 막대](control-bars.md)를 참조 하세요.

## <a name="window-class-hierarchy"></a>창 클래스 계층 구조

Mfc *참조* 에서 [mfc 계층 구조 차트](hierarchy-chart.md) 를 참조 하세요. 보기는 [문서/뷰 아키텍처](document-view-architecture.md)에서 설명 합니다. 대화 상자는 [대화](dialog-boxes.md)상자에 설명 되어 있습니다.

## <a name="creating-your-own-special-purpose-window-classes"></a>사용자 고유의 Special-Purpose 창 클래스 만들기

클래스 라이브러리에서 제공 하는 창 클래스 외에 특수 한 용도의 자식 창이 필요할 수 있습니다. 이러한 창을 만들려면 사용자 고유의 [CWnd](reference/cwnd-class.md)파생 클래스를 만들어 프레임 또는 뷰의 자식 창으로 만듭니다. 프레임 워크는 문서 프레임 창에서 클라이언트 영역의 범위를 관리 한다는 점에 유의 해야 합니다. 대부분의 클라이언트 영역은 뷰에서 관리 되지만 컨트롤 막대나 사용자 지정 창과 같은 다른 창에서 보기와의 공간을 공유할 수 있습니다. 프레임 창의 클라이언트 영역에서 자식 창의 위치를 지정 하기 위해 [CView](reference/cview-class.md) 및 [ccontrolbar](reference/ccontrolbar-class.md) 클래스의 메커니즘과 상호 작용 해야 할 수 있습니다.

창을 [만들면](creating-windows.md) 창 개체와 해당 개체를 관리 하는 창이 생성 됩니다.

## <a name="see-also"></a>참고 항목

[창 개체](window-objects.md)
