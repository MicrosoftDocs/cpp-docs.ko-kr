---
description: '자세한 정보: _com_error:: HelpFile'
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: e45785913a8a5a1909f702bce672727171e0baef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295928"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Microsoft 전용**

`IErrorInfo::GetHelpFile`함수를 호출 합니다.

## <a name="syntax"></a>구문

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Return Value

`IErrorInfo::GetHelpFile`개체 내에 기록 된 개체에 대 한 결과를 반환 합니다 `IErrorInfo` `_com_error` . 결과 BSTR은 `_bstr_t` 개체에 캡슐화됩니다. `IErrorInfo`가 기록 되지 않으면 빈을 반환 `_bstr_t` 합니다.

## <a name="remarks"></a>설명

메서드를 호출 하는 동안 발생 하는 모든 오류 `IErrorInfo::GetHelpFile` 는 무시 됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
