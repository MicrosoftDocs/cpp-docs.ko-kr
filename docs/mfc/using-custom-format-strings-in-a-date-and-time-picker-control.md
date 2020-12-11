---
description: '자세히 알아보기: 날짜 및 시간 선택 컨트롤에서 사용자 지정 서식 문자열 사용'
title: 날짜 및 시간 선택 컨트롤에서 사용자 지정 서식 문자열 사용
ms.date: 11/04/2016
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
ms.openlocfilehash: 91add199ffd852a107588617d47a2fd51136596d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154554"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>날짜 및 시간 선택 컨트롤에서 사용자 지정 서식 문자열 사용

기본적으로 날짜 및 시간 선택 컨트롤은 현재 날짜 또는 시간을 표시 하기 위한 세 가지 형식 형식 (고유 스타일에 해당 하는 형식)을 제공 합니다.

- **DTS_LONGDATEFORMAT** 날짜를 긴 형식으로 표시 하 고 "수요일, 1 월 3 일 2000"와 같은 출력을 생성 합니다.

- **DTS_SHORTDATEFORMAT** "1/3/00"과 같은 출력을 생성 하는 간단한 형식으로 날짜를 표시 합니다.

- **DTS_TIMEFORMAT** "5:31:42 PM"과 같은 출력을 생성 하는 긴 형식으로 시간을 표시 합니다.

그러나 사용자 지정 서식 문자열을 사용 하 여 날짜 또는 시간의 모양을 사용자 지정할 수 있습니다. 이 사용자 지정 문자열은 기존 형식 문자, 비 서식 문자 또는 둘의 조합으로 구성 됩니다. 사용자 지정 문자열이 작성 되 면 사용자 지정 문자열을 전달 하는 [CDateTimeCtrl:: SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) 을 호출 합니다. 그러면 날짜 및 시간 선택 컨트롤에서 사용자 지정 서식 문자열을 사용 하 여 현재 값을 표시 합니다.

다음 예제 코드 (여기서 *m_dtPicker* 는 `CDateTimeCtrl` 개체)는 가능한 한 가지 솔루션을 보여 줍니다.

[!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]

사용자 지정 형식 문자열 외에도 날짜 및 시간 선택 컨트롤은 [콜백 필드도](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)지원 합니다.

## <a name="see-also"></a>참고 항목

[CDateTimeCtrl 사용](../mfc/using-cdatetimectrl.md)<br/>
[컨트롤](../mfc/controls-mfc.md)
