---
description: '자세한 정보: _bstr_t:: GetBSTR'
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: ced985bb5123d86ff119279fc49a2b4d181ba8b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229303"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Microsoft 전용**

`BSTR`에 의해 래핑되는 `_bstr_t`의 시작 부분을 가리킵니다.

## <a name="syntax"></a>구문

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Return Value

`BSTR`에 의해 래핑되는 `_bstr_t`의 시작 부분입니다.

## <a name="remarks"></a>설명

**Getbstr** `_bstr_t` 은를 공유 하는 모든 개체에 영향을 줍니다 `BSTR` . 두 개 이상의 `_bstr_t` 은 `BSTR` 복사 생성자와 **operator =** 를 사용 하 여를 공유할 수 있습니다.

## <a name="example"></a>예제

**Getbstr** 를 사용 하는 예제는 [_Bstr_t:: Assign](../cpp/bstr-t-assign.md) 을 참조 하십시오.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_bstr_t 클래스](../cpp/bstr-t-class.md)
