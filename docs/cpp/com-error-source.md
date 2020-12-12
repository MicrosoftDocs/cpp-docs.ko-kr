---
description: '자세한 정보: _com_error:: Source'
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 3b6cf35420454e8285d3d8b4deee3df8fe8771e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295772"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Microsoft 전용**

`IErrorInfo::GetSource`함수를 호출 합니다.

## <a name="syntax"></a>구문

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Return Value

`IErrorInfo::GetSource`개체 내에 기록 된 개체에 대 한 결과를 반환 합니다 `IErrorInfo` `_com_error` . 결과 `BSTR`은 `_bstr_t` 개체에 캡슐화됩니다. `IErrorInfo`가 기록 되지 않으면 빈을 반환 `_bstr_t` 합니다.

## <a name="remarks"></a>설명

메서드를 호출 하는 동안 발생 하는 모든 오류 `IErrorInfo::GetSource` 는 무시 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
