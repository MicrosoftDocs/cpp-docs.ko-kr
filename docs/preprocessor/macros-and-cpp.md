---
description: '에 대 한 자세한 정보: 매크로 및 c + +'
title: 매크로 및 C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 2ec4db1e36bf18c23567c8c513bdc5e15ec613a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333427"
---
# <a name="macros-and-c"></a>매크로 및 C++

C + +는 ANSI C 전처리기에서 제공 되는 기능을 기능이 아닙니다 하는 새로운 기능을 제공 합니다. 이 새로운 기능으로 형식이 더욱 안전해지고 효과적으로 언어를 예측할 수 있습니다.

- C + +에서로 선언 된 개체 **`const`** 는 상수 식에서 사용할 수 있습니다. 프로그램에서 형식 및 값 정보를 포함 하는 상수를 선언할 수 있습니다. 디버거를 사용 하 여 기호로 볼 수 있는 열거형을 선언할 수 있습니다. 전처리기 지시문을 사용 하 여 상수를 정의 하는 경우에는 `#define` 형식이 안전 하지 않고 정확 하지 않습니다. **`const`** 프로그램에 해당 주소를 사용 하는 식이 포함 되어 있지 않으면 개체에 대해 저장소가 할당 되지 않습니다.

- C ++ 인라인 함수 기능은 함수 형식 매크로를 대신합니다. 인라인 함수를 사용하면 매크로에 비해 다음과 같은 이점이 있습니다.

  - 형식 안전성. 인라인 함수는 일반 함수와 똑같은 함수 검사를 받습니다. 매크로는 형식이 안전 하지 않습니다.

  - 의도하지 않은 결과가 생기는 인수를 올바르게 처리. 인라인 함수는 함수 본문을 입력 하기 전에 인수로 제공 된 식을 계산 합니다. 따라서 부작용이 있는 식은 안전 하지 않을 수 있습니다.

인라인 함수에 대 한 자세한 내용은 [inline, __inline, \_ _forceinline](../cpp/inline-functions-cpp.md)을 참조 하세요.

이전 버전과의 호환성을 위해 ANSI C 및 이전의 C++ 사양에 있는 모든 전처리기 기능이 Microsoft C++에 대해 유지됩니다.

## <a name="see-also"></a>참고 항목

[미리 정의 된 매크로](../preprocessor/predefined-macros.md)\
[매크로(C/C++)](../preprocessor/macros-c-cpp.md)
