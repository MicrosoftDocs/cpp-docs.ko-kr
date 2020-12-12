---
description: '자세히 알아보기: 표준 컨트롤에서 컨트롤 파생'
title: 표준 컨트롤에서 컨트롤 파생시키기
ms.date: 11/04/2016
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
ms.openlocfilehash: 80e63464a7ad6d869582c66d5047a255e303a6a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327872"
---
# <a name="deriving-controls-from-a-standard-control"></a>표준 컨트롤에서 컨트롤 파생시키기

모든 [CWnd](reference/cwnd-class.md)파생 클래스와 마찬가지로 기존 컨트롤 클래스에서 새 클래스를 파생 하 여 컨트롤의 동작을 수정할 수 있습니다.

### <a name="to-create-a-derived-control-class"></a>파생 컨트롤 클래스를 만들려면

1. 기존 컨트롤 클래스에서 클래스를 파생 하 고 필요에 따라 `Create` 기본 클래스 함수에 필요한 인수를 제공 하도록 멤버 함수를 재정의 `Create` 합니다.

1. 메시지 처리기 멤버 함수 및 메시지 맵 항목을 제공 하 여 특정 Windows 메시지에 대 한 응답으로 컨트롤의 동작을 수정 합니다. [함수에 메시지 매핑을](reference/mapping-messages-to-functions.md)참조 하세요.

1. 새 멤버 함수를 제공 하 여 컨트롤의 기능을 확장 합니다 (선택 사항).

대화 상자에서 파생 컨트롤을 사용 하려면 추가 작업이 필요 합니다. 대화 상자에서 컨트롤의 형식과 위치는 일반적으로 대화 상자 템플릿 리소스에 지정 됩니다. 파생 된 컨트롤 클래스를 만드는 경우 리소스 컴파일러가 파생 된 클래스에 대해 알지 못하므로 해당 클래스를 대화 상자 템플릿에 지정할 수 없습니다.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>대화 상자에 파생 컨트롤을 추가 하려면

1. 파생 된 대화 상자 클래스의 선언에 파생 컨트롤 클래스의 개체를 포함 합니다.

1. `OnInitDialog` `SubclassDlgItem` 파생 컨트롤에 대 한 멤버 함수를 호출 하도록 대화 상자 클래스의 멤버 함수를 재정의 합니다.

`SubclassDlgItem` 대화 상자 템플릿에서 생성 된 컨트롤을 "동적으로 서브 클래스" 합니다. 컨트롤이 동적으로 서브클래싱된 경우 Windows에 연결 하 여 응용 프로그램 내에서 일부 메시지를 처리 한 다음 나머지 메시지를 Windows에 전달 합니다. 자세한 내용은 MFC 참조에서 클래스의 [SubclassDlgItem](reference/cwnd-class.md#subclassdlgitem) 멤버 함수를 참조 `CWnd` 하세요 . 다음 예제에서는 `OnInitDialog` 를 호출 하기 위해의 재정의를 작성할 수 있는 방법을 보여 줍니다 `SubclassDlgItem` .

[!code-cpp[NVC_MFCControlLadenDialog#3](codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

파생 된 컨트롤은 대화 상자 클래스에 포함 되기 때문에 대화 상자가 생성 될 때 생성 되 고 대화 상자가 소멸 될 때 소멸 됩니다. 이 코드를 [직접 컨트롤 추가](adding-controls-by-hand.md)의 예제와 비교 합니다.

## <a name="see-also"></a>참고 항목

[컨트롤 만들기 및 사용](making-and-using-controls.md)<br/>
[컨트롤](controls-mfc.md)
