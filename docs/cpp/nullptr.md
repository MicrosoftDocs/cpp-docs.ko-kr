---
title: nullptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06586d7d4374ec1763e43a1eaf3235c37dc72cd1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077947"
---
# <a name="nullptr"></a>nullptr

어떠한 원시 포인터 형식으로도 변환될 수 있는 `std::nullptr_t` 형식의 null 포인터 상수를 지정합니다.  키워드를 사용할 수 있지만 **nullptr** 코드 형식을 사용 하는 경우 모든 헤더를 포함 하지 않고 `std::nullptr_t`, 헤더를 포함 하 여 정의 해야 합니다 `<cstddef>`합니다.

> [!NOTE]
>  합니다 **nullptr** 키워드는 C +에 정의 되어 + CLI에 대 한 관리 코드 응용 프로그램 되며 ISO 표준 c + + 키워드를 사용 하 여 서로 바꿔 사용할 수 없습니다. 코드를 사용 하 여 컴파일될 수 있습니다 하는 경우는 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 관리 되는 코드를 대상으로 하는 컴파일러 옵션을 사용 하 여 `__nullptr` 컴파일러는 네이티브 c + + 해석을 사용 되도록 해야 하는 코드 줄에서. 자세한 내용은 [nullptr](../windows/nullptr-cpp-component-extensions.md)합니다.

## <a name="remarks"></a>설명

NULL 또는 0을 사용 하지 마십시오 (`0`) null 포인터 상수로; **nullptr** 오용에 덜 취약 하므로 이며 대부분의 상황에서 잘 작동 합니다.  예를 들어 `func(std::pair<const char *, double>)`가 주어진 경우 `func(std::make_pair(NULL, 3.14))`를 호출하면 컴파일러 오류가 발생합니다.  NULL 매크로는 `0`으로 확장되므로 `std::make_pair(0, 3.14)` 호출은 func()의 `std::pair<int, double>` 매개 변수 형식으로 변환될 수 없는 `std::pair<const char *, double>`를 반환합니다.  `func(std::make_pair(nullptr, 3.14))`는 `std::make_pair(nullptr, 3.14)`로 변환될 수 있는 `std::pair<std::nullptr_t, double>`를 반환하기 때문에 `std::pair<const char *, double>`를 호출하면 성공적으로 컴파일됩니다.

## <a name="see-also"></a>참고자료

[키워드](../cpp/keywords-cpp.md)<br/>
[nullptr](../windows/nullptr-cpp-component-extensions.md)