---
description: '자세한 정보: 정수를 부동 소수점 값으로 캐스팅'
title: 정수를 부동 소수점 값으로 캐스팅
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: 2a1a3ce5bf7aac98148c70eb62cdb3c377ca54f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214020"
---
# <a name="casting-integers-to-floating-point-values"></a>정수를 부동 소수점 값으로 캐스팅

**ANSI 3.2.1.3** 정수가 원래의 값을 정확하게 나타낼 수 없는 부동 소수점 숫자로 변환될 경우 잘라내기 방향입니다.

정수가 값을 정확히 나타낼 수 없는 부동 소수점 값으로 캐스팅되면 알맞은 근사값으로 값이 반올림되거나 반내림됩니다.

예를 들어, **`unsigned long`** (전체 자릿수가 32비트)을 **`float`** (가수의 전체 자릿수가 23비트)로 캐스팅하면 가장 근사한 256의 배수로 반올림됩니다. **`long`** 값 4,294,966,913 ~ 4,294,967,167은 모두 **`float`** 값 4,294,967,040으로 반올림됩니다.

## <a name="see-also"></a>참조

[부동 소수점의 수학](../c-language/floating-point-math.md)
