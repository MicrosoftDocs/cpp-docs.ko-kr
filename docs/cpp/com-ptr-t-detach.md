---
description: _Com_ptr_t::D etach에 대해 자세히 알아보세요.
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: ec2a18a04b8c32e373225235fd0d6f520e768af0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295512"
---
# <a name="_com_ptr_tdetach"></a>_com_ptr_t::Detach

**Microsoft 전용**

캡슐화된 인터페이스 포인터를 추출하고 반환합니다.

## <a name="syntax"></a>구문

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>설명

캡슐화된 인터페이스 포인터를 추출하여 반환한 다음 캡슐화된 포인터 저장소를 NULL로 지웁니다. 이 작업을 통해 인터페이스 포인터의 캡슐화를 제거합니다. `Release`반환 된 인터페이스 포인터에 대해를 호출 해야 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_ptr_t 클래스](../cpp/com-ptr-t-class.md)
