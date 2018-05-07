---
title: OnIdle 멤버 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnIdle
dev_langs:
- C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbe912db448e424f18b6d72f6e148312c5940687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="onidle-member-function"></a>OnIdle 멤버 함수
프레임 워크를 호출 하는 경우 Windows 메시지가 처리 되는 경우는 [CWinApp](../mfc/reference/cwinapp-class.md) 멤버 함수 [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (MFC 라이브러리 참조에서 설명).  
  
 재정의 `OnIdle` 백그라운드 작업을 수행할 수 있습니다. 기본 버전 도구 모음 단추와 같은 사용자 인터페이스 개체의 상태를 업데이트 하 고 해당 작업 과정에서 프레임 워크에 의해 생성 된 임시 개체의 정리를 수행 합니다. 다음 그림은 메시지 루프 호출 하는 방법을 `OnIdle` 큐에 메시지가 없는 경우.  
  
 ![메시지 루프 프로세스](../mfc/media/vc387c1.gif "vc387c1")  
메시지 루프  
  
 유휴 루프에서 수행할 수 있는 작업에 대 한 자세한 내용은 참조 [유휴 루프 처리](../mfc/idle-loop-processing.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CWinApp: 응용 프로그램 클래스](../mfc/cwinapp-the-application-class.md)
