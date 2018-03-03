---
title: "현재 뷰 관리 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1510b005f452174acfe8ad65ae3f66cf8aafaa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="managing-the-current-view"></a>현재 뷰 관리
프레임 창의 기본 구현의 일부로 프레임 창은 현재 활성 뷰의 추적을 유지합니다. 프레임 창에 두 개 이상의 뷰가 포함된 경우(예: 분할자 창), 현재 뷰가 최근에 사용된 뷰입니다. 활성 뷰는 Windows의 활성 창 또는 현재 입력 포커스와 독립적입니다.  
  
 활성 뷰가 변경 되는 경우 프레임 워크를 호출 하 여 현재 뷰에 알립니다 해당 [OnActivateView](../mfc/reference/cview-class.md#onactivateview) 멤버 함수입니다. `OnActivateView`의 `bActivate` 매개 변수를 조사하여 뷰가 활성화 또는 비활성화되었는지를 확인할 수 있습니다. 기본적으로 `OnActivateView`는 활성화될 때 현재 뷰에 포커스를 설정합니다. `OnActivateView`를 재정의하여 뷰가 비활성화되거나 다시 활성화될 때 특수한 처리를 수행할 수 있습니다. 예를 들어 활성 뷰를 다른 비활성 뷰와 구분하기 위해 특수한 시각적 큐를 제공해야 할 수 있습니다.  
  
 프레임 창에 설명 된 대로 해당 현재 (활성) 뷰에 명령을 전달 [명령 라우팅](../mfc/command-routing.md), 표준 명령 라우팅의 일부로 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프레임 창 사용](../mfc/using-frame-windows.md)

