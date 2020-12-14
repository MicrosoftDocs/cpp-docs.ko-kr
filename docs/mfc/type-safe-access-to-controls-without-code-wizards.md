---
description: '자세히 알아보기: 코드 마법사를 사용 하지 않고 컨트롤에 대 한 액세스 Type-Safe'
title: 코드 마법사를 사용하지 않고 컨트롤에 대한 형식이 안전한 액세스 수행
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
ms.openlocfilehash: 1e59353a17f0d841cd69fa64f792dcc7cdbfa6ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263779"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>코드 마법사를 사용하지 않고 컨트롤에 대한 형식이 안전한 액세스 수행

컨트롤에 대 한 형식이 안전한 액세스를 만드는 첫 번째 방법은 다음 예제와 같이 인라인 멤버 함수를 사용 하 여 `CWnd` 클래스 `GetDlgItem` 멤버 함수의 반환 형식을 적절 한 c + + 컨트롤 형식으로 캐스팅 하는 것입니다.

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

그러면 다음과 유사한 코드를 사용 하 여 형식이 안전한 방식으로 컨트롤에 액세스 하는 데이 멤버 함수를 사용할 수 있습니다.

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>참고 항목

[대화 상자의 컨트롤에 대 한 형식이 안전한 액세스](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[코드 마법사를 사용 하 여 컨트롤에 대 한 형식이 안전한 액세스](../mfc/type-safe-access-to-controls-with-code-wizards.md)
