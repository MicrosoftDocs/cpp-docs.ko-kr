---
description: '자세히 알아보기: 새 컨트롤 클래스를 기반으로 변수 선언'
title: 새 컨트롤 클래스 기반의 변수 선언
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: aa38a38b3113e4c4826756b020860d79e03ef16b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220229"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>새 컨트롤 클래스 기반의 변수 선언

MFC 컨트롤 클래스를 만든 후에는이를 기반으로 변수를 선언할 수 있습니다. 새 변수에 대 한 컨텍스트를 제공 하려면 대화 상자 편집기를 열고 재사용 가능한 컨트롤을 사용 하려는 대화 상자를 편집 해야 합니다. 또한 대화 상자에는 연결 된 클래스가 이미 있어야 합니다. 대화 상자 편집기를 사용 하는 방법에 대 한 자세한 내용은 [대화 상자 편집기](../../windows/dialog-editor.md)를 참조 하십시오.

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>재사용 가능한 클래스를 기반으로 변수를 선언 하려면

1. 대화 상자를 편집 하는 동안 컨트롤 도구 모음에서 대화 상자로 새 컨트롤의 기본 클래스와 같은 형식의 컨트롤을 끌어 옵니다.

1. 끌어 놓은 컨트롤 위에 마우스 포인터를 놓습니다.

1. CTRL 키를 누른 상태에서 컨트롤을 두 번 클릭 합니다.

   [멤버 변수 추가](../../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) 대화 상자가 나타납니다.

1. **액세스** 상자에서 컨트롤에 대 한 올바른 액세스를 선택 합니다.

1. **제어 변수** 확인란을 클릭 합니다.

1. **변수 이름** 상자에 이름을 입력 합니다.

1. **범주** 아래에서 **제어** 를 클릭 합니다.

1. **컨트롤 ID** 목록에서 추가한 컨트롤을 선택 합니다. **변수 형식** 목록에 올바른 변수 형식이 표시 되 고 **컨트롤 형식** 상자에 올바른 컨트롤 형식이 표시 됩니다.

1. **설명** 상자에 코드에 표시 하려는 모든 주석을 추가 합니다.

1. **확인** 을 클릭합니다.

## <a name="see-also"></a>참조

[함수에 메시지 매핑](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[코드 마법사에서 기능 추가](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[클래스 추가](../../ide/adding-a-class-visual-cpp.md)<br/>
[멤버 함수 추가](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[멤버 변수 추가](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[가상 함수 재정의](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 메시지 처리기](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[클래스 구조 탐색](../../ide/navigate-code-cpp.md)
