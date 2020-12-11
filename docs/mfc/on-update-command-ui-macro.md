---
description: '자세한 정보: 매크로 ON_UPDATE_COMMAND_UI'
title: ON_UPDATE_COMMAND_UI 매크로
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 394ee2679e84c09223f61d485fac3e628dec7145
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112169"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI 매크로

사용자 인터페이스 개체를 명령 대상 개체의 명령 업데이트 처리기에 연결 하려면 **클래스 뷰** 을 열고 처리기가 추가 될 클래스를 마우스 오른쪽 단추로 클릭 한 다음 **클래스 마법사** 를 선택 합니다. 왼쪽 목록에서 사용자 인터페이스 개체 ID를 찾은 다음 오른쪽 창에서 **UPDATE_COMMAND_UI** 을 선택 하 고 **처리기 추가** 를 클릭 합니다. 그러면 클래스에 처리기 함수가 만들어지고 메시지 맵에 적절 한 항목이 추가 됩니다. 자세한 내용은 [함수에 메시지 매핑](reference/mapping-messages-to-functions.md) 을 참조 하세요. **메시지** 창에서 처리할 추가 메시지를 지정할 수 있습니다.

예를 들어 프로그램의 편집 메뉴에서 모두 지우기 명령을 업데이트 하려면 **클래스 마법사** 를 사용 하 여 선택한 클래스에 메시지 맵 항목을 추가 하 고, 클래스 선언에서 호출 된 명령 업데이트 처리기에 대 한 함수 선언과 클래스 `OnUpdateEditClearAll` 의 구현 파일에 빈 함수 템플릿을 추가 합니다. 함수 프로토타입은 다음과 같습니다.

[!code-cpp[NVC_MFCDocView#2](codesnippet/cpp/on-update-command-ui-macro_1.h)]

모든 처리기와 마찬가지로 함수 선언에는 **afx_msg** 키워드가 표시 됩니다. 모든 업데이트 처리기와 마찬가지로 하나의 인수를 사용 하 여 개체에 대 한 포인터를 가져옵니다 `CCmdUI` .

## <a name="see-also"></a>참고 항목

[방법: User-Interface 개체 업데이트](how-to-update-user-interface-objects.md)
