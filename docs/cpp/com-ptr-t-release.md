---
description: '자세한 정보: _com_ptr_t:: Release'
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: a1b81295ab249b1826ea6d373f782d91765df3b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344720"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Microsoft 전용**

 `IUnknown` 캡슐화 된 인터페이스 포인터에서의 릴리스 멤버 함수를 호출 합니다.

## <a name="syntax"></a>구문

```cpp
void Release( );
```

## <a name="remarks"></a>설명

`IUnknown::Release`캡슐화 된 인터페이스 포인터에 대해를 호출 하 여 `E_POINTER` 이 인터페이스 포인터가 NULL 인 경우 오류를 발생 시킵니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_ptr_t 클래스](../cpp/com-ptr-t-class.md)
