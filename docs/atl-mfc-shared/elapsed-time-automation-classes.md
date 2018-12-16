---
title: '경과 시간: 자동화 클래스'
ms.date: 11/04/2016
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
ms.openlocfilehash: fbd01a4e7268456af342293d77ef74d372d2e639
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583913"
---
# <a name="elapsed-time-automation-classes"></a>경과 시간: 자동화 클래스

이 절차에서는 두 `CTime` 객체 간의 차이를 계산하고 `CTimeSpan` 결과를 얻는 방법을 보여 준다.

## <a name="to-calculate-elapsed-time"></a>경과된 시간을 계산하는 방법

1. `COleDateTime` 개체를 2개 생성합니다.

1. `COleDateTime` 개체 중 하나를 현재 시간으로 설정합니다.

1. 시간이 많이 걸리는 작업을 수행합니다.

1. 다른 `OleDateTime` 개체를 현재 시간으로 설정합니다.

1. 두 시간 사이의 차이를 얻습니다.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>참고 항목

[날짜 및 시간: 자동화 지원](../atl-mfc-shared/date-and-time-automation-support.md)
