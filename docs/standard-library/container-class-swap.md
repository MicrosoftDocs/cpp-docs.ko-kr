---
description: '자세히 알아보기: Container Class:: swap'
title: Container Class::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: a38dd6d14ada3ad50927060ccec1542ebf2fd4ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233359"
---
# <a name="container-classswap"></a>Container Class::swap

> [!NOTE]
> 이 항목은 c + + 표준 라이브러리에서 사용 되는 컨테이너의 작동 하지 않는 예제로 Microsoft c + + 설명서에 있습니다. 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../standard-library/stl-containers.md)를 참조하세요.

**\* 이** 와 해당 인수 간에 제어 되는 시퀀스를 바꿉니다.

## <a name="syntax"></a>구문

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>설명

**\* 이 경우 get \_ 할당자 = =** _right_**.get_allocator** 는 일정 한 시간에 교환 합니다. 그렇지 않으면 두 개의 제어되는 시퀀스에 있는 요소 수에 비례하여 많은 요소 할당 및 생성자 호출을 수행합니다.

## <a name="see-also"></a>참고 항목

[Sample Container 클래스](../standard-library/sample-container-class.md)
