---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4276'
title: 컴파일러 경고(수준 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: 14b13b2eb1e13d28f2b208e52ef71e1c729fe5e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311788"
---
# <a name="compiler-warning-level-1-c4276"></a>컴파일러 경고(수준 1) C4276

' function ': 프로토타입을 제공 하지 않았습니다. 매개 변수를 가정 하지 않습니다.

함수 주소를 [__stdcall](../../cpp/stdcall.md) 호출 규칙으로 사용 하는 경우 컴파일러에서 함수의 데코레이팅된 이름을 만들 수 있도록 프로토타입을 제공 해야 합니다. *함수* 에 프로토타입이 없으므로 컴파일러는 데코레이팅된 이름을 만들 때 함수에 매개 변수가 없는 것으로 가정 합니다.
