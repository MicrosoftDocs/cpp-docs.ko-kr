---
description: '자세히 알아보기: 대화 상자 데이터 교환'
title: 대화 상자 데이터 교환
ms.date: 11/19/2018
helpviewer_keywords:
- initializing dialog boxes
- canceling data exchange
- dialog box data, retrieving
- DDX (dialog data exchange), data exchange mechanism
- dialog boxes [MFC], initializing
- dialog boxes [MFC], retrieving user input using DDX
- dialog box data
- dialog boxes [MFC], data exchange
- CDataExchange class [MFC], using DDX
- DoDataExchange method [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- transferring dialog box data
- DDX (dialog data exchange), canceling
- UpdateData method [MFC]
- retrieving dialog box data [MFC]
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
ms.openlocfilehash: 7ed592e8e6a452d4c6958c3c5f7b573c1be7fe07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261478"
---
# <a name="dialog-data-exchange"></a>대화 상자 데이터 교환

DDX 메커니즘을 사용 하는 경우 일반적으로 `OnInitDialog` 처리기 또는 대화 상자 생성자에서 대화 상자 개체의 멤버 변수에 대 한 초기 값을 설정 합니다. 대화 상자가 표시 되기 직전에 프레임 워크의 DDX 메커니즘은 멤버 변수의 값을 대화 상자의 컨트롤에 전송 합니다. 그러면 대화 상자 자체가 또는에 대 한 응답에 표시 될 때 표시 됩니다 `DoModal` `Create` . 의 기본 구현에서는 `OnInitDialog` `CDialog` `UpdateData` 클래스의 멤버 함수 `CWnd` 를 호출 하 여 대화 상자의 컨트롤을 초기화 합니다.

사용자가 확인 단추를 클릭 하거나 인수 TRUE를 사용 하 여 멤버 함수를 호출할 때마다 동일한 메커니즘에서 컨트롤의 값을 멤버 변수로 전송 합니다 `UpdateData` .  대화 상자 데이터 유효성 검사 메커니즘은 유효성 검사 규칙을 지정한 데이터 항목의 유효성을 검사 합니다.

다음 그림은 대화 상자 데이터 교환을 보여 줍니다.

![대화 상자 데이터 교환](../mfc/media/vc379d1.gif "대화 상자 데이터 교환") <br/>
대화 상자 데이터 교환

`UpdateData` 은 전달 된 **BOOL** 매개 변수로 지정 된 대로 양방향으로 작동 합니다. 교환을 수행 하려면에서 개체를 `UpdateData` 설정 하 `CDataExchange` 고의 멤버 함수에 대 한 대화 상자 클래스의 재정의를 호출 `CDialog` `DoDataExchange` 합니다. `DoDataExchange` 형식의 인수를 사용 `CDataExchange` 합니다. `CDataExchange`에 전달 되는 개체는 exchange의 `UpdateData` 방향으로 해당 정보를 정의 하는 exchange의 컨텍스트를 나타냅니다.

사용자가 (또는 코드 마법사)를 재정의할 때 `DoDataExchange` 데이터 멤버 (컨트롤) 마다 하나의 DDX 함수 호출을 지정 합니다. 각 DDX 함수는로 전달 된 인수에서 제공 된 컨텍스트를 기반으로 양방향으로 데이터를 교환 하는 방법을 알고 `CDataExchange` `DoDataExchange` `UpdateData` 있습니다.

MFC는 다양 한 종류의 exchange에 대해 다양 한 DDX 함수를 제공 합니다. 다음 예에서는 `DoDataExchange` 두 개의 DDX 함수와 하나의 DDV 함수가 호출 되는를 재정의 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCControlLadenDialog#49](codesnippet/cpp/dialog-data-exchange_1.cpp)]

`DDX_`및 `DDV_` 줄은 데이터 맵입니다. 표시 되는 샘플 DDX 및 DDV 함수는 각각 확인란 컨트롤과 편집 상자 컨트롤에 대 한 것입니다.

사용자가 모달 대화 상자를 취소 하면 `OnCancel` 멤버 함수는 대화 상자를 종료 하 고 `DoModal` **IDCANCEL** 값을 반환 합니다. 이 경우 대화 상자와 대화 상자 개체 간에 데이터가 교환 되지 않습니다.

## <a name="see-also"></a>참고 항목

[대화 상자 데이터 교환 및 유효성 검사](dialog-data-exchange-and-validation.md)<br/>
[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)<br/>
[대화 상자 데이터 유효성 검사](dialog-data-validation.md)
