---
description: '자세한 정보: 캐스팅 연산자'
title: 캐스팅 연산자
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: 6ab19f1b30958f4d78a97be76c15373ed9c9b620
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308551"
---
# <a name="casting-operators"></a>캐스팅 연산자

캐스트 연산자에는 C++ 언어 전용 연산자가 몇 가지 있습니다. 이 연산자는 예전 스타일의 C 언어 캐스트에 있는 일부 모호함과 위험성을 제거하는 데 목적이 있습니다. 그 종류는 다음과 같습니다.

- [dynamic_cast](../cpp/dynamic-cast-operator.md) 다형 형식을 변환 하는 데 사용 됩니다.

- [static_cast](../cpp/static-cast-operator.md) 비 다형 형식을 변환 하는 데 사용 됩니다.

- [const_cast](../cpp/const-cast-operator.md) , 및 특성을 제거 하는 데 사용 **`const`** **`volatile`** **`__unaligned`** 됩니다.

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md) 비트의 간단한 다시 해석을 위해 사용 됩니다.

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) C + +/CLI에서 안정형 MSIL을 생성 하는 데 사용 됩니다.

**`const_cast`** **`reinterpret_cast`** 이러한 연산자는 이전 스타일 캐스트와 동일한 위험을 제공 하므로 및를 마지막 수단으로 사용 합니다. 하지만 이 두 캐스트는 이전 스타일 캐스트를 완전히 바꾸기 위해 여전히 필요합니다.

## <a name="see-also"></a>참고 항목

[캐스팅](../cpp/casting.md)
