---
description: Allocator_fixed_size 클래스에 대해 자세히 알아보세요.
title: allocator_fixed_size 클래스
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_fixed_size
- allocators/stdext::allocator_fixed_size
- stdext::allocators::allocator_fixed_size
helpviewer_keywords:
- stdext::allocators [C++], allocator_fixed_size
- stdext::allocator_fixed_size
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
ms.openlocfilehash: b4b3452a611734dd2731bdb9c43e4bf7a7ce6744
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163602"
---
# <a name="allocator_fixed_size-class"></a>allocator_fixed_size 클래스

[Max_fixed_size](max-fixed-size-class.md)에서 길이가 관리 되는 [cache_freelist](cache-freelist-class.md) 형식의 캐시를 사용 하 여 *형식 형식의 개체* 에 대 한 저장소 할당 및 해제를 관리 하는 개체에 대해 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>매개 변수

*입력할*\
할당자에 의해 할당된 요소 형식입니다.

## <a name="remarks"></a>설명

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl) 매크로는 다음 문에서이 클래스를 *name* 매개 변수로 전달 합니다.`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>요구 사항

**헤더:**\<allocators>

**네임스페이스:** stdext

## <a name="see-also"></a>참고 항목

[\<allocators>](allocators-header.md)
