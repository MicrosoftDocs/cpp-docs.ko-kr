---
description: '자세히 알아보기: 대화 상자의 컨트롤에 대 한 액세스 Type-Safe'
title: 대화 상자의 컨트롤에 대한 형식이 안전한 액세스
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
ms.openlocfilehash: 1c8b3482ee723e95142c9cd19fa6068f32f4ebd0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263831"
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>대화 상자의 컨트롤에 대한 형식이 안전한 액세스

대화 상자의 컨트롤에서 `CListBox` 및 `CEdit` 같은 MFC 컨트롤 클래스의 인터페이스를 사용할 수 있습니다. 컨트롤 개체를 만들어 대화 상자 컨트롤에 연결할 수 있습니다. 그런 다음 컨트롤에서 작동하는 멤버 함수를 호출하여 해당 클래스 인터페이스를 통해 컨트롤에 액세스할 수 있습니다. 컨트롤에 대한 형식 안전 액세스를 제공하기 위해 여기서 설명한 방법이 설계되었습니다. 특히 입력란 및 목록 상자 같은 컨트롤에 유용합니다.

`CDialog`에서 파생된 클래스에서 대화 상자의 컨트롤과 C++ 컨트롤 멤버 변수 간에 연결하기 위한 두 가지 방법은 다음과 같습니다.

- [코드 마법사를 사용하지 않는 경우](../mfc/type-safe-access-to-controls-without-code-wizards.md)

- [코드 마법사를 사용하는 경우](../mfc/type-safe-access-to-controls-with-code-wizards.md)

## <a name="see-also"></a>참고 항목

[대화 상자](../mfc/dialog-boxes.md)
