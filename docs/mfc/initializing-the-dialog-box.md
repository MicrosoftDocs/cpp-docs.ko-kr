---
title: "대화 상자 초기화 | Microsoft Docs"
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
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2af05011e8f2af2993edf3ea2f82716137b17857
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-the-dialog-box"></a>대화 상자 초기화
후 대화 상자와 모든 컨트롤이 만들어집니다 나타나기 방금 전에 대화 상자 (두 가지 형식의) 화면에 대화 상자 개체의 [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) 멤버 함수를 호출 합니다. 모달 대화 상자에 대 한 동안이 오류가 발생 된 `DoModal` 호출 합니다. 모덜리스 대화 상자에 대 한 `OnInitDialog` 될 때 호출 됩니다 **만들기** 호출 됩니다. 일반적으로 재정의 `OnInitDialog` 입력란의 초기 텍스트를 설정 하는 등 대화 상자의 컨트롤을 초기화 합니다. 호출 해야 합니다는 `OnInitDialog` 기본 클래스의 멤버 함수 `CDialog`에서 프로그램 `OnInitDialog` 재정의 합니다.  
  
 대화 상자의 배경색 (및 응용 프로그램에서 다른 모든 대화 상자의)을 설정 하는 경우 참조 [대화 상자의 배경색 설정](../mfc/setting-the-dialog-boxs-background-color.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [대화 상자의 수명 주기](../mfc/life-cycle-of-a-dialog-box.md)

