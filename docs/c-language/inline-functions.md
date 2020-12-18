---
description: '자세한 정보: 인라인 함수'
title: 인라인 함수
ms.date: 10/16/2017
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
ms.openlocfilehash: 616e85f2ac298420b3de174551ea2f6f879f24f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137556"
---
# <a name="inline-functions"></a>인라인 함수

**Microsoft 전용**

**`__inline`** 키워드는 컴파일러가 모든 함수 호출 건에 대해 함수 정의 내에서 코드를 대체하라고 말합니다. 하지만 코드 대체는 컴파일러의 판단하에서만 발생합니다. 예를 들어, 컴파일러는 해당 주소를 가져온 경우나 인라인에 비해 너무 클 경우에는 함수를 인라인하지 않습니다.

인라이닝의 후보로 간주되는 함수의 경우 새 스타일 함수 정의를 사용해야 합니다.

이 양식을 사용하여 인라인 함수를 지정합니다.

> **`__inline`** *type*<sub>opt</sub> *function-definition*

인라인 함수를 사용하면 보다 빨리 코드를 생성할 수 있고 동등한 함수 호출이 생성하는 코드보다 더 작은 코드를 생성하는 경우도 있습니다. 그 이유는 다음과 같습니다.

- 함수 호출을 실행하는 데 필요한 시간을 저장합니다.

- 3줄 이하의 작은 인라인 함수는 컴파일러 인수가 인수 및 반환 값을 처리하는 코드를 생성하지 않으므로 해당 함수 호출보다 적은 코드를 만듭니다.

- 인라인으로 생성된 함수에서는 컴파일러가 프로시저 간 최적화를 수행하지 않기 때문에 일반 함수에 사용할 수 없는 코드 최적화가 진행됩니다.

**`__inline`** 을 사용하는 함수는 인라인 어셈블러 코드와 혼동해서는 안 됩니다. 자세한 내용은 [인라인 어셈블러](../c-language/inline-assembler-c.md)를 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md)
