---
description: '자세한 정보: 예외 처리 루틴'
title: 예외 처리 루틴
ms.date: 11/04/2016
f1_keywords:
- c.exceptions
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
ms.openlocfilehash: d241c3ef7f32a96f08d4ad499887963fda031967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331096"
---
# <a name="exception-handling-routines"></a>예외 처리 루틴

C++ 예외 처리 함수를 사용하여 프로그램 실행 중에 예기치 않은 이벤트에서 복구할 수 있습니다.

## <a name="exception-handling-functions"></a>예외 처리 함수

|함수|기능|
|--------------|---------|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Win32 예외(C 구조적 예외)를 C++ 형식 예외로 처리|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|**terminate** 에서 호출하는 사용자 고유 종료 루틴을 설치합니다.|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|**unexpected** 에서 호출하는 사용자 고유 종료 함수를 설치합니다.|
|[끝나야](../c-runtime-library/reference/terminate-crt.md)|예외가 throw된 후에 특정 상황에서 자동으로 호출됩니다. **terminate** 함수는 **set_terminate** 를 사용하여 **abort** 또는 지정한 함수를 호출합니다.|
|[없는](../c-runtime-library/reference/unexpected-crt.md)|**set_unexpected** 를 사용하여 **terminate** 또는 지정한 함수를 호출합니다. **unexpected** 함수는 현재 Microsoft C++ 예외 처리 구현에서 사용되지 않습니다.|

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
