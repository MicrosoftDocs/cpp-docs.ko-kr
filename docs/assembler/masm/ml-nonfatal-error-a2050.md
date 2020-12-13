---
description: '자세한 정보: ML 심각 하지 않은 오류 A2050'
title: ML 심각하지 않은 오류 A2050
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 9ae38353d3c2e2a2e25e3e5c4a87e3b3b6888781
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129001"
---
# <a name="ml-nonfatal-error-a2050"></a>ML 심각하지 않은 오류 A2050

**실수 또는 BCD 숫자가 허용 되지 않습니다.**

부동 소수점 (실수) 숫자 또는 BCD (binary 코딩 된 10 진수) 상수가 데이터 이니셜라이저가 아닌 다른 방식으로 사용 되었습니다.

다음 중 하나가 발생 했습니다.

- 식에 실수 또는 BCD가 사용 되었습니다.

- 실수를 사용 하 여 [DWORD](dword.md), [qword(64](qword.md)또는 [1tb](tbyte.md)이외의 지시어를 초기화 했습니다.

- BCD를 사용 하 여 이외의 지시문을 초기화 했습니다 `TBYTE` .

## <a name="see-also"></a>참고 항목

[ML 오류 메시지](ml-error-messages.md)
