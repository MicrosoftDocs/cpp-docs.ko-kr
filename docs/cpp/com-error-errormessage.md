---
description: '자세한 정보: _com_error:: ErrorMessage'
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: e7f91882d55e629744df5f26f7dcc64df1dddb22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296006"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Microsoft 전용**

개체에 저장 된 HRESULT에 대 한 문자열 메시지를 검색 합니다 `_com_error` .

## <a name="syntax"></a>구문

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Return Value

개체 내에 기록 된 HRESULT에 대 한 문자열 메시지를 반환 합니다 `_com_error` . HRESULT가 매핑된 16 비트 [Wcode](../cpp/com-error-wcode.md)이면 일반 메시지 " `IDispatch error #<wCode>` "가 반환 됩니다. 메시지가 발견되지 않으면 일반 메시지 "`Unknown error #<hresult>`"가 반환됩니다. 반환된 문자열은 _UNICODE 매크로의 상태에 따라 유니코드이거나 멀티바이트 문자열입니다.

## <a name="remarks"></a>설명

개체 내에 기록 된 HRESULT에 대 한 적절 한 시스템 메시지 텍스트를 검색 합니다 `_com_error` . Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 함수를 호출 하 여 시스템 메시지 텍스트를 가져옵니다. 반환된 문자열은 `FormatMessage` API에 의해 할당되고, `_com_error` 개체가 제거될 때 해제됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[_com_error 클래스](../cpp/com-error-class.md)
