---
title: nullptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3063a93361095a9d51152ce93f8522365513cf67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="nullptr"></a>nullptr
어떠한 원시 포인터 형식으로도 변환될 수 있는 `std::nullptr_t` 형식의 null 포인터 상수를 지정합니다.  헤더를 포함하지 않고 `nullptr` 키워드를 사용할 수 있지만, 코드에서 `std::nullptr_t` 형식을 사용하는 경우 `<cstddef>` 헤더를 포함하여 정의해야 합니다.  
  
> [!NOTE]
>  `nullptr` 키워드는 관리 코드 응용 프로그램을 위해 C++/CLI에서도 정의되며 ISO 표준 C++ 키워드와 상호 교환해서 사용할 수 없습니다. 사용 하 여 코드를 컴파일할 수 있는 경우는 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 관리 코드를 대상으로 컴파일러 옵션을 사용 하 여 `__nullptr` 컴파일러는 네이티브 c + + 해석을 사용을 보장 해야 하는 코드의 임의의 줄에서. 자세한 내용은 참조 [nullptr](../windows/nullptr-cpp-component-extensions.md)합니다.  
  
## <a name="remarks"></a>설명  
 `NULL` 또는 영(`0`)을 null 포인터 상수로 사용하지 마십시오. `nullptr`은 잘못 사용하는 경우 위험성이 더 적고 대부분의 상황에서 보다 효과적으로 작동합니다.  예를 들어 `func(std::pair<const char *, double>)`가 주어진 경우 `func(std::make_pair(NULL, 3.14))`를 호출하면 컴파일러 오류가 발생합니다.  NULL 매크로는 `0`으로 확장되므로 `std::make_pair(0, 3.14)` 호출은 func()의 `std::pair<int, double>` 매개 변수 형식으로 변환될 수 없는 `std::pair<const char *, double>`를 반환합니다.  `func(std::make_pair(nullptr, 3.14))`는 `std::make_pair(nullptr, 3.14)`로 변환될 수 있는 `std::pair<std::nullptr_t, double>`를 반환하기 때문에 `std::pair<const char *, double>`를 호출하면 성공적으로 컴파일됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [키워드](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)