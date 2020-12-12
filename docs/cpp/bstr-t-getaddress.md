---
description: '자세한 정보: _bstr_t:: GetAddress'
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: afb877a6f1b4cfcfb6fe08b36168af745d733b85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229316"
---
# <a name="_bstr_tgetaddress"></a>_bstr_t::GetAddress

**Microsoft 전용**

기존 문자열을 해제하고 새로 할당된 문자열의 주소를 반환합니다.

## <a name="syntax"></a>구문

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Return Value

`BSTR`로 래핑되는 `_bstr_t`에 대한 포인터입니다.

## <a name="remarks"></a>설명

**Getaddress** `_bstr_t` 는를 공유 하는 모든 개체에 영향을 줍니다 `BSTR` . 두 개 이상의 `_bstr_t` 은 `BSTR` 복사 생성자와 **operator =** 를 사용 하 여를 공유할 수 있습니다.

## <a name="example"></a>예제

**Getaddress** 를 사용 하는 예제는 [_Bstr_t:: Assign](../cpp/bstr-t-assign.md) 을 참조 하십시오.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_bstr_t 클래스](../cpp/bstr-t-class.md)
