---
description: '자세한 정보: _com_ptr_t:: QueryInterface'
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 6c6ff19227c920aade762af295942d8058a17ad3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295343"
---
# <a name="_com_ptr_tqueryinterface"></a>_com_ptr_t::QueryInterface

**Microsoft 전용**

 `IUnknown` 캡슐화 된 인터페이스 포인터에서의 QueryInterface 멤버 함수를 호출 합니다.

## <a name="syntax"></a>구문

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>매개 변수

*iid*<br/>
`IID` 인터페이스 포인터의입니다.

*®*<br/>
원시 인터페이스 포인터입니다.

## <a name="remarks"></a>설명

지정 된을 `IUnknown::QueryInterface` 사용 하 여 캡슐화 된 인터페이스 포인터에서를 호출 `IID` 하 고 결과 원시 인터페이스 포인터를 *p* 로 반환 합니다. 이 루틴은 성공 또는 실패를 나타내는 HRESULT를 반환 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_ptr_t 클래스](../cpp/com-ptr-t-class.md)
