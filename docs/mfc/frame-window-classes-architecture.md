---
title: 프레임 창 클래스 (아키텍처) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.frame
dev_langs:
- C++
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7de72b77be9be90ca876cfef943500a0312d183
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="frame-window-classes-architecture"></a>프레임 창 클래스(아키텍처)
문서/뷰 아키텍처의 프레임 창이 있는 뷰 창을 포함 하는 창입니다. 또한 지원 제어 있으면 여기에 연결 된 막대입니다.  
  
 다중 문서 MDI (인터페이스) 응용 프로그램의 주 창에서 파생 된 `CMDIFrameWnd`합니다. 직접 포함 하지는 문서 프레임 `CMDIChildWnd` 개체입니다. `CMDIChildWnd` 개체를 차례로 문서 뷰를 포함 합니다.  
  
 단일 문서 SDI (인터페이스) 응용 프로그램의 주 창에서 파생 `CFrameWnd`, 현재 문서 보기를 포함 합니다.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 SDI 응용 프로그램의 주 프레임 창에 대 한 기본 클래스입니다. 또한의 기본 클래스에 대 한 다른 모든 프레임 창 클래스.  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 MDI 응용 프로그램의 주 프레임 창에 대 한 기본 클래스입니다.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 MDI 응용 프로그램의 문서 프레임 창에 대 한 기본 클래스입니다.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 서버 문서 위치에서 편집 되는 경우 보기에 대 한 프레임 창을 제공 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 개요](../mfc/class-library-overview.md)

