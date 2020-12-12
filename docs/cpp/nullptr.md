---
description: '자세한 정보: nullptr'
title: nullptr
ms.date: 07/22/2020
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 8d7eb3a578addc14b85c53c50ab81c6e5592d541
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146154"
---
# <a name="nullptr"></a>nullptr

**`nullptr`** 키워드는 `std::nullptr_t` 원시 포인터 형식으로 변환할 수 있는 형식의 null 포인터 상수를 지정 합니다.  헤더를 포함 하지 않고 키워드를 사용할 수 있지만, **`nullptr`** 코드에서 형식을 사용 하는 `std::nullptr_t` 경우 헤더를 포함 하 여 정의 해야 합니다 `<cstddef>` .

> [!NOTE]
> **`nullptr`** 키워드는 관리 코드 응용 프로그램에 대 한 c + +/cli 에서도 정의 되며 ISO 표준 c + + 키워드와는 호환 되지 않습니다. 관리 코드를 대상으로 하는 컴파일러 옵션을 사용 하 여 코드를 컴파일할 수 있는 경우 [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) `__nullptr` 컴파일러에서 네이티브 c + + 해석을 사용 하도록 보장 해야 하는 코드 줄에서를 사용 합니다. 자세한 내용은 [ `nullptr` (c + +/cli 및 c + +/cx)](../extensions/nullptr-cpp-component-extensions.md)를 참조 하세요.

## <a name="remarks"></a>설명

`NULL`또는 0 ()을 `0` null 포인터 상수로 사용 하지 마십시오. **`nullptr`** 는 오용에 취약 하지 않으며 대부분의 상황에서 효과적으로 작동 합니다.  예를 들어 `func(std::pair<const char *, double>)`가 주어진 경우 `func(std::make_pair(NULL, 3.14))`를 호출하면 컴파일러 오류가 발생합니다.  매크로는 `NULL` 로 확장 `0` 되므로 호출에서을 반환 하 고 `std::make_pair(0, 3.14)` `std::pair<int, double>` `std::pair<const char *, double>` 의 매개 변수 형식으로 변환할 수 없습니다 `func` .  `func(std::make_pair(nullptr, 3.14))`는 `std::make_pair(nullptr, 3.14)`로 변환될 수 있는 `std::pair<std::nullptr_t, double>`를 반환하기 때문에 `std::pair<const char *, double>`를 호출하면 성공적으로 컴파일됩니다.

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)<br/>
[`nullptr` (C + +/CLI 및 c + +/CX)](../extensions/nullptr-cpp-component-extensions.md)
