---
description: '자세한 정보: 날짜 및 시간 선택 컨트롤에서 콜백 필드 사용'
title: 날짜 및 시간 선택 컨트롤에서 콜백 필드 사용
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 3ff0ae2af8e71a53cceff4d5d8df652f701b1ef1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202628"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>날짜 및 시간 선택 컨트롤에서 콜백 필드 사용

날짜 및 시간 선택 필드를 정의 하는 표준 형식 문자 외에도 사용자 지정 형식 문자열의 특정 부분을 콜백 필드로 지정 하 여 출력을 사용자 지정할 수 있습니다. 콜백 필드를 선언 하려면 서식 문자열의 본문에 "X" 문자 (ASCII 코드 88)를 하나 이상 포함 합니다. 예를 들어, 다음 문자열 "'은 ' yy '/' MM '/' dd ' (Day ' X ') '"를 발생 시킵니다. 날짜 및 시간 선택 컨트롤은 현재 값을 연도로 표시 하 고 그 다음에 월, 날짜 및 마지막으로 날짜를 표시 합니다.

> [!NOTE]
> 콜백 필드의 X 수가 표시 되는 문자 수와 일치 하지 않습니다.

"X" 문자를 반복 하 여 사용자 지정 문자열의 여러 콜백 필드를 구분할 수 있습니다. 따라서 형식 문자열 "XXddddMMMdd ', ' yyyXXX '에는 두 개의 고유한 콜백 필드인" XX "및" XXX "가 포함 됩니다.

> [!NOTE]
> 콜백 필드는 유효한 필드로 처리 되므로 응용 프로그램에서 DTN_WMKEYDOWN 알림 메시지를 처리할 수 있도록 준비 해야 합니다.

날짜 및 시간 선택 컨트롤에서 콜백 필드를 구현 하는 것은 다음 세 부분으로 구성 됩니다.

- 사용자 지정 서식 문자열 초기화

- DTN_FORMATQUERY 알림 처리

- DTN_FORMAT 알림 처리

## <a name="initializing-the-custom-format-string"></a>사용자 지정 서식 문자열 초기화

호출을 사용 하 여 사용자 지정 문자열을 초기화 `CDateTimeCtrl::SetFormat` 합니다. 자세한 내용은 [날짜 및 시간 선택 컨트롤에서 사용자 지정 서식 문자열 사용](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md)을 참조 하세요. 사용자 지정 형식 문자열을 설정 하는 일반적인 장소는 포함 하는 `OnInitDialog` 대화 상자 클래스 또는 포함 하는 `OnInitialUpdate` 뷰 클래스의 함수에 있습니다.

## <a name="handling-the-dtn_formatquery-notification"></a>DTN_FORMATQUERY 알림 처리

컨트롤이 형식 문자열을 구문 분석 하 고 콜백 필드를 발견 하면 응용 프로그램은 DTN_FORMAT 및 DTN_FORMATQUERY 알림 메시지를 보냅니다. 쿼리 중인 콜백 필드를 확인할 수 있도록 콜백 필드 문자열이 알림에 포함 됩니다.

DTN_FORMATQUERY 알림은 현재 콜백 필드에 표시 되는 문자열의 최대 허용 크기 (픽셀)를 검색 하기 위해 전송 됩니다.

이 값을 올바르게 계산 하려면 컨트롤의 표시 글꼴을 사용 하 여 필드를 대체할 문자열의 높이와 너비를 계산 해야 합니다. [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) Win32 함수를 호출 하 여 문자열의 실제 계산을 쉽게 수행할 수 있습니다. 크기를 확인 한 후에는 값을 다시 응용 프로그램에 전달 하 고 처리기 함수를 종료 합니다.

다음 예제는 콜백 문자열의 크기를 제공 하는 한 가지 방법입니다.

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

현재 콜백 필드의 크기가 계산 된 후에는 필드에 대 한 값을 제공 해야 합니다. 이는 DTN_FORMAT 알림에 대 한 처리기에서 수행 됩니다.

## <a name="handling-the-dtn_format-notification"></a>DTN_FORMAT 알림 처리

DTN_FORMAT 알림은 응용 프로그램에서 대체 되는 문자열을 요청 하는 데 사용 됩니다. 다음 예에서는 가능한 한 가지 방법을 보여 줍니다.

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
> **NMDATETIMEFORMAT** 구조체에 대 한 포인터는 알림 처리기의 첫 번째 매개 변수를 적절 한 형식으로 캐스팅 하 여 찾을 수 있습니다.

## <a name="see-also"></a>참고 항목

[CDateTimeCtrl 사용](../mfc/using-cdatetimectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
