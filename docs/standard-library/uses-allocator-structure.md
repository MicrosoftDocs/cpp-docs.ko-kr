---
description: '다음에 대 한 자세한 정보: uses_allocator 구조체'
title: uses_allocator 구조체
ms.date: 11/04/2016
f1_keywords:
- future/std::uses_allocator
ms.assetid: c418f002-62e9-4806-b70c-41c663cae583
ms.openlocfilehash: 3ece99d12443af2ec28b52e2a0dae72d8af4cc91
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153618"
---
# <a name="uses_allocator-structure"></a>uses_allocator 구조체

항상 true인 특수화입니다.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty, class Alloc>
struct uses_allocator<promise<Ty>, Alloc> : true_type;
template <class Ty, class Alloc>
struct uses_allocator<packaged_task<Ty>, Alloc> : true_type;
```

## <a name="requirements"></a>요구 사항

**헤더:**\<future>

**네임스페이스:** std

## <a name="specializations"></a>특수화

### <a name="tuple"></a><a name="tuple"></a> \<tuple>

```cpp
template <class... Types, class Alloc>
struct uses_allocator<tuple<Types...>, Alloc>;
```

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
