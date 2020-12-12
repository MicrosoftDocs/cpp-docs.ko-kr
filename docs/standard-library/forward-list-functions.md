---
description: '&lt;Forward_list 함수에 대해 자세히 알아보세요. &gt;'
title: '&lt;forward_list&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 3f827b777f2e6fa62dd78c7d737d5da84b50610c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324367"
---
# <a name="ltforward_listgt-functions"></a>&lt;forward_list&gt; 함수

## <a name="swap"></a><a name="swap"></a> 스왑을

두 정방향 목록의 요소를 교환합니다.

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
`forward_list` 형식의 개체입니다.

*오른쪽*\
`forward_list` 형식의 개체입니다.

### <a name="remarks"></a>설명

이 템플릿 함수는 `left.swap(right)`를 실행합니다.
