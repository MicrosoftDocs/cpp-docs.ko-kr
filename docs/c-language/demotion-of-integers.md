---
description: '자세한 정보: 정수 강등'
title: 정수 강등
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: d80adff34223d8aa785fa6ffa079a54af198a309
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186820"
---
# <a name="demotion-of-integers"></a>정수 강등

**ANSI 3.2.1.2** 정수를 더 짧은 부호 있는 정수로 변환한 결과 또는 값을 표현할 수 없는 경우 부호 없는 정수를 같은 길이의 부호 있는 정수로 변환한 결과

**`long`** 정수가 **`short`** 로 캐스팅되거나 **`short`** 가 **`char`** 로 캐스팅되는 경우에는 최하위 바이트가 유지됩니다.

예를 들어, 다음 줄은

```
short x = (short)0x12345678L;
```

0x5678 값을 `x`에 할당하고 다음 줄은

```
char y = (char)0x1234;
```

0x34 값을 `y`에 할당합니다.

**`signed`** 변수가 **`unsigned`** 로 변환되거나 그 반대의 경우 비트 패턴이 동일하게 유지됩니다. 예를 들어, -2(0xFE)를 **`unsigned`** 값으로 캐스팅하면 254(0xFE)가 생성됩니다.

## <a name="see-also"></a>참조

[정수](../c-language/integers.md)
