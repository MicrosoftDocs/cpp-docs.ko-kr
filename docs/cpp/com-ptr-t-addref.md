---
description: '자세한 정보: _com_ptr_t:: AddRef'
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 0979245662a94596307b1a63af918d0ce67c7b6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295694"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Microsoft 전용**

`AddRef` `IUnknown` 캡슐화 된 인터페이스 포인터에 대 한의 멤버 함수를 호출 합니다.

## <a name="syntax"></a>구문

```cpp
void AddRef( );
```

## <a name="remarks"></a>설명

`IUnknown::AddRef`캡슐화 된 인터페이스 포인터에 대해를 호출 하 여 `E_POINTER` 포인터가 NULL 인 경우 오류를 발생 시킵니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_ptr_t 클래스](../cpp/com-ptr-t-class.md)
