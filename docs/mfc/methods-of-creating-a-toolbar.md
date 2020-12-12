---
description: '자세히 알아보기: 도구 모음을 만드는 방법'
title: 도구 모음을 만드는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: 14626f398d3ccabd002cc21be682c1a5616a0410
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203083"
---
# <a name="methods-of-creating-a-toolbar"></a>도구 모음을 만드는 방법

MFC에서는 [CToolBar](reference/ctoolbar-class.md) 및 [CToolBarCtrl](reference/ctoolbarctrl-class.md) (Windows 공용 컨트롤 API를 래핑하는) 도구 모음을 만드는 두 가지 클래스를 제공 합니다. `CToolBar` 는 도구 모음 공용 컨트롤의 모든 기능을 제공 하 고 필요한 일반적인 컨트롤 설정 및 구조체의 대부분을 처리 합니다. 그러나 결과로 생성 되는 실행 파일은 일반적으로를 사용 하 여 만든 것 보다 큽니다 `CToolBarCtrl` .

`CToolBarCtrl` 일반적으로는 작은 실행 파일을 생성 하 고, `CToolBarCtrl` 도구 모음을 MFC 아키텍처에 통합 하지 않으려는 경우를 사용 하는 것이 좋습니다. 를 사용 하 여 `CToolBarCtrl` 도구 모음을 mfc 아키텍처에 통합 하려는 경우에는 도구 모음 컨트롤 조작을 mfc에 전달 하기 위해 추가로 주의를 기울여야 합니다. 이 통신은 어렵지 않습니다. 그러나를 사용 하는 경우에는 불필요 한 추가 작업이 있습니다 `CToolBar` .

Visual C++ 도구 모음 공용 컨트롤을 활용 하는 두 가지 방법을 제공 합니다.

- 를 사용 하 여 도구 모음을 만든 `CToolBar` 다음 [CToolBar:: GetToolBarCtrl](reference/ctoolbar-class.md#gettoolbarctrl) 를 호출 하 여 `CToolBarCtrl` 멤버 함수에 대 한 액세스를 가져옵니다.

- [CToolBarCtrl](reference/ctoolbarctrl-class.md)의 생성자를 사용 하 여 도구 모음을 만듭니다.

어느 방법을 사용 하 든 toolbar 컨트롤의 멤버 함수에 대 한 액세스를 제공 합니다. 를 호출 하면 `CToolBar::GetToolBarCtrl` `CToolBarCtrl` 두 멤버 함수 집합을 사용할 수 있도록 개체에 대 한 참조를 반환 합니다. 을 사용 하 여 도구 모음을 생성 및 만드는 방법에 대 한 자세한 내용은 [CToolBar](reference/ctoolbar-class.md) 를 참조 하세요 `CToolBar` .

## <a name="see-also"></a>참고 항목

[CToolBarCtrl 사용](using-ctoolbarctrl.md)<br/>
[컨트롤](controls-mfc.md)
