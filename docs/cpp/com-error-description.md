---
description: _Com_error::D e)에 대해 자세히 알아보세요.
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: 6404d16361abe81d9e234a6b63039a7476d91ef1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332551"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Microsoft 전용**

`IErrorInfo::GetDescription`함수를 호출 합니다.

## <a name="syntax"></a>구문

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Return Value

`IErrorInfo::GetDescription`개체 내에 기록 된 개체에 대 한 결과를 반환 합니다 `IErrorInfo` `_com_error` . 결과 `BSTR`은 `_bstr_t` 개체에 캡슐화됩니다. `IErrorInfo`가 기록 되지 않으면 빈을 반환 `_bstr_t` 합니다.

## <a name="remarks"></a>설명

함수를 호출 `IErrorInfo::GetDescription` 하 고 `IErrorInfo` 개체 내에 기록 된을 검색 `_com_error` 합니다. 메서드를 호출 하는 동안 발생 하는 모든 오류 `IErrorInfo::GetDescription` 는 무시 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
