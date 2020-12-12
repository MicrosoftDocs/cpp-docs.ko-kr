---
description: '자세한 정보: _com_ptr_t:: Attach'
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 5b27a4bd6572f2f1429766328c01f377672ee11d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295655"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft 전용**

이 스마트 포인터 형식의 원시 인터페이스 포인터를 캡슐화합니다.

## <a name="syntax"></a>구문

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>매개 변수

*pInterface*<br/>
원시 인터페이스 포인터입니다.

*fAddRef*<br/>
인 경우 **`true`** `AddRef` 가 호출 됩니다. 인 경우 **`false`** 개체는를 `_com_ptr_t` 호출 하지 않고 원시 인터페이스 포인터의 소유권을 갖습니다 `AddRef` .

## <a name="remarks"></a>설명

- **연결 (**  *pinterface*  **)** `AddRef` 가 호출 되지 않습니다. 인터페이스 소유권이 이 `_com_ptr_t` 개체에 전달됩니다. `Release` 이전에 캡슐화 된 포인터에 대 한 참조 횟수를 감소 하기 위해가 호출 됩니다.

- **Attach (**  *pinterface* **,**  *fAddRef*  **)** *FAddRef* 가 이면 **`true`** `AddRef` 캡슐화 된 인터페이스 포인터의 참조 횟수를 증가 시키기 위해가 호출 됩니다. *FAddRef* 가 이면 **`false`** 이 개체는를 `_com_ptr_t` 호출 하지 않고 원시 인터페이스 포인터의 소유권을 갖습니다 `AddRef` . `Release` 이전에 캡슐화 된 포인터에 대 한 참조 횟수를 감소 하기 위해가 호출 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_ptr_t 클래스](../cpp/com-ptr-t-class.md)
