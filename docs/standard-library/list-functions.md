---
description: '자세한 정보: &lt; 함수 목록 &gt; 표시'
title: '&lt;&gt;함수 나열 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 6a94fcc916db08a510a968b66b0a0dc0cfa9b8e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284709"
---
# <a name="ltlistgt-functions"></a>&lt;목록 &gt; 함수

## <a name="swap"></a><a name="swap"></a> 스왑을

두 목록의 요소를 교환합니다.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>매개 변수

*비어*\
`list` 형식의 개체입니다.

*오른쪽*\
`list` 형식의 개체입니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 `left.swap(right)`를 실행합니다.
