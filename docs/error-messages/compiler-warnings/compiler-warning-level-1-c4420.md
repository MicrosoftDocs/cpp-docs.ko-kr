---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4420'
title: 컴파일러 경고(수준 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 2a92d7296bf5c38655182e5c0dd2c200d0ccf42d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311073"
---
# <a name="compiler-warning-level-1-c4420"></a>컴파일러 경고(수준 1) C4420

' operator ': 연산자를 사용할 수 없습니다. 대신 ' operator '를 사용 합니다. 런타임 검사가 손상 될 수 있습니다.

이 경고는 [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector new/delete 검사)를 사용 하 고 벡터 폼을 찾을 수 없는 경우에 생성 됩니다. 이 경우 벡터가 아닌 형식이 사용 됩니다.

/RTCv가 올바르게 작동 하려면 [](../../cpp/new-operator-cpp.md) / 벡터 구문이 사용 된 경우 컴파일러에서 항상 새[delete](../../cpp/delete-operator-cpp.md) 의 vector 형식을 호출 해야 합니다.
