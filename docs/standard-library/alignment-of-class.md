---
description: Alignment_of 클래스에 대해 자세히 알아보세요.
title: alignment_of 클래스
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 7e1eeafb259b71f24cb272c079cdb485bb8e1b4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163654"
---
# <a name="alignment_of-class"></a>alignment_of 클래스

지정된 형식의 맞춤을 가져옵니다. 이 구조체는의 측면에서 구현 됩니다 [`alignof`](../cpp/alignment-cpp-declarations.md) . **`alignof`** 맞춤 값을 쿼리해야 하는 경우 직접를 사용 합니다. `alignment_of`태그 디스패치를 수행 하는 경우와 같이 정수 계열 상수가 필요한 경우를 사용 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>매개 변수

*Ty*\
형식이 쿼리입니다.

## <a name="remarks"></a>설명

형식 쿼리는 *Ty* 형식의 맞춤 값을 보유 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<type_traits>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[`<type_traits>`](type-traits.md)\
[`aligned_storage` 클래스](aligned-storage-class.md)
