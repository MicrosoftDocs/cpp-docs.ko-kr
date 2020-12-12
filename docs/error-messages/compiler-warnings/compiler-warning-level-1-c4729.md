---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4729'
title: 컴파일러 경고(수준 1) C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: de4da8a56f4b8c6788b972a154e8670c14c07d68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272216"
---
# <a name="compiler-warning-level-1-c4729"></a>컴파일러 경고(수준 1) C4729

선형 그래프 기반 경고에 사용하기에는 함수가 너무 큽니다.

이 경고는 함수가 너무 커서 경고를 생성하는 상황을 안정적으로 검사하여 컴파일할 수 없는 경우에 생성됩니다. 이 경고는 [/Od](../../build/reference/od-disable-debug.md) 컴파일러 옵션을 사용한 경우에만 생성됩니다.

이 경고를 해결하려면 함수를 좀더 작은 함수로 나눕니다.
