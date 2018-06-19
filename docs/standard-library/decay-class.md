---
title: decay 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::decay
dev_langs:
- C++
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0451b8565a4d021181d79d15437637e1b2f3b27
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841800"
---
# <a name="decay-class"></a>decay 클래스

값으로 전달되는 형식을 생성합니다. 형식을 비참조, 비상수, 비휘발성으로 만들거나 함수 또는 배열 형식에서 형식에 대한 포인터를 만듭니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>매개 변수

`T` 수정할 형식입니다.

## <a name="remarks"></a>설명

decay 템플릿을 사용하여 형식이 값을 통해 인수로 전달된 것처럼 결과 형식을 생성합니다. 템플릿 클래스 멤버 typedef `type`은 다음 단계에서 정의되는 수정된 형식을 포함합니다.

- `U` 형식은 `remove_reference<T>::type`으로 정의되어 있습니다.

- `is_array<U>::value`가 true이면 수정된 형식 `type`이 `remove_extent<U>::type *`입니다.

- 그렇지 않은 경우, `is_function<U>::value`가 true이면 수정된 형식 `type`은 `add_pointer<U>::type`입니다.

- 그렇지 않은 경우, 수정된 형식 `type`은 `remove_cv<U>::type`입니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<type_traits>](../standard-library/type-traits.md)<br/>
