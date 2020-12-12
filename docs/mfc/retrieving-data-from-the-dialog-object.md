---
description: '자세히 알아보기: 대화 상자 개체에서 데이터 검색'
title: 대화 상자 개체에서 데이터 검색
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
ms.openlocfilehash: 823006b7b892c8e6476d007eb5cc13fb1386458e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218045"
---
# <a name="retrieving-data-from-the-dialog-object"></a>대화 상자 개체에서 데이터 검색

프레임 워크는 대화 상자에서 컨트롤의 값을 초기화 하 고 컨트롤에서 값을 검색 하는 쉬운 방법을 제공 합니다. 더 복잡 한 수동 접근 방식은 `SetDlgItemText` `GetDlgItemText` `CWnd` 컨트롤 창에 적용 되는 클래스의 및 멤버 함수 등의 함수를 호출 하는 것입니다. 이러한 함수를 사용 하면 각 컨트롤에 개별적으로 액세스 하 여 및와 같은 함수를 호출 하는 값을 설정 하거나 가져올 수 있습니다 `SetWindowText` `GetWindowText` . 프레임 워크의 접근 방식은 초기화와 검색을 자동화 합니다.

DDX (대화 상자 데이터 교환)를 사용 하면 대화 상자의 컨트롤과 대화 상자 개체의 멤버 변수 간에 데이터를 보다 쉽게 교환할 수 있습니다. 이 exchange는 두 가지 방식으로 작동 합니다. 대화 상자에서 컨트롤을 초기화 하려면 대화 상자 개체에서 데이터 멤버의 값을 설정 하면 됩니다. 그러면 대화 상자가 표시 되기 전에 프레임 워크에서 컨트롤로 값을 전송 합니다. 그런 다음 언제 든 지 사용자가 입력 한 데이터를 사용 하 여 대화 상자 데이터 멤버를 업데이트할 수 있습니다. 이 시점에서 데이터 멤버 변수를 참조 하 여 데이터를 사용할 수 있습니다.

DDV (대화 상자 데이터 유효성 검사)를 사용 하 여 대화 상자 컨트롤의 값을 자동으로 확인할 수 있도록 정렬할 수도 있습니다.

DDX 및 DDV는 [대화 상자 데이터 교환 및 유효성 검사](../mfc/dialog-data-exchange-and-validation.md)에 자세히 설명 되어 있습니다.

모달 대화 상자의 경우 사용자가 `DoModal` IDOK를 반환 하지만 대화 상자 개체가 제거 되기 전에 사용자가 입력 한 모든 데이터를 검색할 수 있습니다. 모덜리스 대화 상자의 경우에는 `UpdateData` 인수를 **TRUE로 설정** 하 고 대화 상자 클래스 멤버 변수에 액세스 하 여 언제 든 지 대화 상자 개체에서 데이터를 검색할 수 있습니다. 이 주제는 [대화 상자 데이터 교환 및 유효성 검사](../mfc/dialog-data-exchange-and-validation.md)에 자세히 설명 되어 있습니다.

## <a name="see-also"></a>참고 항목

[MFC에서 대화 상자를 통해 작업](../mfc/life-cycle-of-a-dialog-box.md)
