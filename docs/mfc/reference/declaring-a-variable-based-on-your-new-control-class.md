---
title: 새 컨트롤 클래스에 따라 변수 선언 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.control.variable
dev_langs:
- C++
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 677006d441c940f478b3d23744d1057667307e1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370616"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>새 컨트롤 클래스 기반의 변수 선언
MFC 컨트롤 클래스를 만든 후에 따라 변수를 선언할 수 있습니다. 새 변수에 대 한 컨텍스트를 제공 하려면 대화 상자 편집기를 열고 편집 대화 상자를 다시 사용할 수 있는 컨트롤을 사용 하려면. 또한 대화 상자에는 관련 된 클래스가 있어야 합니다. 대화 상자 편집기를 사용 하는 방법은 참조 하십시오. [대화 상자 편집기](../../windows/dialog-editor.md)합니다.  
  
### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>다시 사용할 수 있는 클래스에 따라 변수를 선언 하려면  
  
1.  대화 상자를 편집 하는 동안 대화 상자 컨트롤 도구 모음에서 새 컨트롤의 기본 클래스와 동일한 형식의 컨트롤을 끕니다.  
  
2.  삭제 된 컨트롤 위로 마우스 포인터를 놓습니다.  
  
3.  CTRL 키를 누른 채 컨트롤을 두 번 클릭 합니다.  
  
     [멤버 변수 추가](../../ide/add-member-variable-wizard.md) 대화 상자가 나타납니다.  
  
4.  에 **액세스** 상자 컨트롤에 대 한 올바른 액세스를 선택 합니다.  
  
5.  클릭는 **제어 변수** 확인란 합니다.  
  
6.  에 **변수 이름** 상자에 이름을 입력 합니다.  
  
7.  아래 **범주**, 클릭 **컨트롤**합니다.  
  
8.  에 **컨트롤 ID** 목록, 사용자가 추가한 컨트롤을 선택 합니다. **변수 형식** 목록에 올바른 변수 유형, 표시 및 **컨트롤 형식과** 상자 올바른 컨트롤 형식이 표시 되어야 합니다.  
  
9. 에 **주석** 상자를 표시 하려면 코드에 주석을 추가 합니다.  
  
10. **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [함수에 메시지 매핑](../../mfc/reference/mapping-messages-to-functions.md)   
 [코드 마법사로 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [클래스 추가](../../ide/adding-a-class-visual-cpp.md)   
 [멤버 함수 추가](../../ide/adding-a-member-function-visual-cpp.md)   
 [멤버 변수 추가](../../ide/adding-a-member-variable-visual-cpp.md)   
 [가상 함수 재정의](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 메시지 처리기](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [클래스 구조 탐색](../../ide/navigating-the-class-structure-visual-cpp.md)
