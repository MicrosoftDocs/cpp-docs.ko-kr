---
description: '자세히 알아보기: 현재 뷰 관리'
title: 현재 뷰 관리
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
ms.openlocfilehash: 9c9acd315636ea33c52fbe63374b5afacef95247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283344"
---
# <a name="managing-the-current-view"></a>현재 뷰 관리

프레임 창의 기본 구현의 일부로 프레임 창은 현재 활성 뷰의 추적을 유지합니다. 프레임 창에 두 개 이상의 뷰가 포함된 경우(예: 분할자 창), 현재 뷰가 최근에 사용된 뷰입니다. 활성 뷰는 Windows의 활성 창 또는 현재 입력 포커스와 독립적입니다.

활성 뷰가 변경 되 면 프레임 워크는 해당 [onactivateview](reference/cview-class.md#onactivateview) 멤버 함수를 호출 하 여 현재 뷰에 알립니다. `OnActivateView` *Bactivate* 매개 변수를 검사 하 여 뷰가 활성화 또는 비활성화 되는지 여부를 확인할 수 있습니다. 기본적으로 `OnActivateView`는 활성화될 때 현재 뷰에 포커스를 설정합니다. `OnActivateView`를 재정의하여 뷰가 비활성화되거나 다시 활성화될 때 특수한 처리를 수행할 수 있습니다. 예를 들어 활성 뷰를 다른 비활성 뷰와 구분하기 위해 특수한 시각적 큐를 제공해야 할 수 있습니다.

[명령 라우팅](command-routing.md)에 설명 된 것 처럼 프레임 창은 현재 (활성) 뷰로 명령을 전달 합니다.

## <a name="see-also"></a>참고 항목

[프레임 창 사용](using-frame-windows.md)
