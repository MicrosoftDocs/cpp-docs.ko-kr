---
description: Is_error_condition_enum 클래스에 대해 자세히 알아보세요.
title: is_error_condition_enum 클래스
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 3fd4f95e06ebee66a1f4d7d0e7de039d26b9f1fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323730"
---
# <a name="is_error_condition_enum-class"></a>is_error_condition_enum 클래스

[error_condition](../standard-library/error-condition-class.md) 열거형을 테스트하는 형식 조건자를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <_Enum>
    class is_error_condition_enum;
```

## <a name="remarks"></a>설명

이 [형식 조건자](../standard-library/type-traits.md)의 인스턴스는 `_Enum` 형식이 `error_condition` 형식의 개체에 저장하는 데 적합한 열거형 값이면 true입니다.

사용자 정의 형식의 경우 이 형식에 특수화를 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

[<type_traits>](../standard-library/type-traits.md)
