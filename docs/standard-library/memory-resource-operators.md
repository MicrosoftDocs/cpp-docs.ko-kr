---
description: '&lt;Memory_resource 연산자에 대 한 자세한 정보 &gt;'
title: '&lt;memory_resource &gt; 연산자'
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::operator!=
- memory_resource/std::operator==
helpviewer_keywords:
- std::operator!= (memory_resource)
- std::operator== (memory_resource)
ms.openlocfilehash: 28c1dee4e2f022cdba14b7f71e7b9a2e40bc1162
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183843"
---
# <a name="ltmemory_resourcegt-operators"></a>&lt;memory_resource &gt; 연산자

## <a name="operator"></a><a name="op_neq"></a> 연산자! =

연산자의 좌 변에 있는 memory_resource 개체가 우변에 있는 memory_resource 개체와 같지 않은 지 테스트 합니다.

```cpp
template <class T1, class T2>
    bool operator!=(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```

## <a name="operator"></a><a name="op_eq_eq"></a> 연산자 = =

연산자의 좌 변에 있는 memory_resource 개체가 우변에 있는 memory_resource 개체와 같은지 테스트 합니다.

```cpp
template <class T1, class T2>
    bool operator==(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```
