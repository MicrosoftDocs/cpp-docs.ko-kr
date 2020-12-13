---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4710'
title: 컴파일러 경고(수준 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: b10a2add132335db48c49ae69740d04f792f126e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330587"
---
# <a name="compiler-warning-level-4-c4710"></a>컴파일러 경고(수준 4) C4710

' function ': 함수가 인라인되지 있지 않습니다.

지정 된 함수가 인라인 확장을 위해 선택 되었지만 컴파일러가 인라이닝을 수행 하지 않았습니다.

인라인은 컴파일러의 판단에 의해 수행 됩니다. 키워드와 **`inline`** 같은 키워드는 **`register`** 컴파일러에 대 한 힌트로 사용 됩니다. 컴파일러는 추론을 사용 하 여 속도를 위해 컴파일할 때 코드의 속도를 높이 거 나 특정 함수를 인라인으로 지정 하 여 공간을 컴파일하는 동안 코드를 더 작게 만드는 지 여부를 확인 합니다. 컴파일러는 공간을 컴파일하는 경우 매우 작은 함수만 인라인 합니다.

경우에 따라 컴파일러는 기계적 이유로 특정 함수를 인라인 하지 않습니다. 컴파일러가 함수를 인라인 할 수 없는 이유 목록은 [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) 를 참조 하세요.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.
