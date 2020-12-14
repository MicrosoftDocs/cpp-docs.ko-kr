---
description: '자세한 정보: 표준 Windows 메시지 처리기'
title: 표준 Windows 메시지에 대한 처리기
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: 161e4d85e702972ee178e2fe82aa2371f0560068
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248933"
---
# <a name="handlers-for-standard-windows-messages"></a>표준 Windows 메시지에 대한 처리기

표준 Windows 메시지에 대 한 기본 처리기 (**WM_**)는 클래스에서 미리 정의 되어 있습니다 `CWnd` . 이 클래스 라이브러리는 메시지 이름을 기반으로 이러한 처리기의 이름을 지정합니다. 예를 들어 **WM_PAINT** 메시지에 대 한 처리기는에서 `CWnd` 다음과 같이 선언 됩니다.

`afx_msg void OnPaint();`

**Afx_msg** 키워드는 **`virtual`** 다른 멤버 함수의 처리기를 구분 하 여 c + + 키워드의 효과를 제안 합니다 `CWnd` . 하지만 이러한 함수는 실제로 가상이 아니며, 대신 메시지 맵을 통해 구현됩니다. 메시지 맵은 C++ 언어의 확장이 아닌 표준 전처리기 매크로에만 의존합니다. 전처리 후 **afx_msg** 키워드가 공백으로 확인 됩니다.

기본 클래스에 정의된 처리기를 재정의하려면 단순히 파생된 클래스의 동일 프로토타입으로 함수를 정의하고 처리기에 대한 메시지-맵 항목을 만듭니다. 처리기는 클래스의 기본 클래스에서 동일한 이름의 모든 처리기를 "재정의"합니다.

이부 경우에는 기본 클래스 및 Windows가 해당 메시지에 대해 작업을 수행할 수 있도록 처리기가 기본 클래스에서 재정의된 처리기를 호출해야 합니다. 재정의에서 기본 클래스 처리기를 호출 하는 위치는 상황에 따라 달라집니다. 경우에 따라 기본 클래스 처리기를 먼저 호출하거나, 마지막으로 호출해야 합니다. 메시지를 직접 처리하지 않도록 선택한 일부 경우에는 기본 클래스 처리기를 조건에 따라 호출합니다. 또한 기본 클래스 처리기를 호출한 후, 기본 클래스 처리기에서 반환된 값 또는 상태에 따라 고유 처리기 코드를 조건에 따라 실행해야 할 수도 있습니다.

> [!CAUTION]
> 인수를 기본 클래스 처리기에 전달하려는 경우에는 처리기에 전달된 인수를 수정하는 것이 안전하지 않습니다. 예를 들어 처리기의 *nChar* 인수를 수정할 수 있습니다 `OnChar` (예: 대문자로 변환). 이 동작은 상당히 모호 하지만이를 수행 해야 하는 경우에는 `CWnd` 멤버 함수를 대신 사용 `SendMessage` 합니다.

[클래스 마법사](reference/mfc-class-wizard.md) 가 지정 된 메시지에 대 한 처리기 함수의 기초를 작성할 때 지정 된 메시지를 재정의 하는 적절 한 방법을 결정 하는 방법 ( `OnCreate` 예: **WM_CREATE** 에 대 한 처리기)은 권장 되는 재정의 된 멤버 함수의 형식으로 스케치 합니다. 다음 예제에서는 처리기가 먼저 기본 클래스 처리기를 호출 하 고-1을 반환 하지 않는 조건 에서만 진행 하도록 권장 합니다.

[!code-cpp[NVC_MFCMessageHandling#3](codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

일반적으로 이러한 처리기의 이름은 접두사 "On"으로 시작합니다. 이러한 처리기 중 일부는 인수를 사용하지 않으며, 다른 일부는 인수를 사용합니다. 또한 일부에는 이외의 반환 형식이 있습니다 **`void`** . 모든 **WM_** 메시지의 기본 처리기는 *MFC 참조* 에서 `CWnd` 이름이 "On"으로 시작 하는 클래스의 멤버 함수로 설명 되어 있습니다. 의 멤버 함수 선언에는 `CWnd` **afx_msg** 접두사가 붙습니다.

## <a name="see-also"></a>참고 항목

[메시지 처리기 함수 선언](declaring-message-handler-functions.md)
