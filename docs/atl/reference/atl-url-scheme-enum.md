---
description: '다음에 대 한 자세한 정보: ATL_URL_SCHEME'
title: ATL_URL_SCHEME 열거형
ms.date: 11/04/2016
helpviewer_keywords:
- ATLUTIL/ATL::ATL_URL_SCHEME
ms.assetid: f4131046-8ba0-4ec1-8209-84203f05d20e
ms.openlocfilehash: 72c149345a0e1edd41bfc9b32d1e94ab6477d488
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165136"
---
# <a name="atl_url_scheme"></a>ATL_URL_SCHEME

이 열거형의 멤버는 [말아](curl-class.md)가 이해 하는 체계에 대 한 상수를 제공 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum ATL_URL_SCHEME{
   ATL_URL_SCHEME_UNKNOWN = -1,
   ATL_URL_SCHEME_FTP     = 0,
   ATL_URL_SCHEME_GOPHER  = 1,
   ATL_URL_SCHEME_HTTP    = 2,
   ATL_URL_SCHEME_HTTPS   = 3,
   ATL_URL_SCHEME_FILE    = 4,
   ATL_URL_SCHEME_NEWS    = 5,
   ATL_URL_SCHEME_MAILTO  = 6,
   ATL_URL_SCHEME_SOCKS   = 7
};
```

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="see-also"></a>참고 항목

[개념](../active-template-library-atl-concepts.md)<br/>
[말아 넘기기:: SetScheme](curl-class.md#setscheme)<br/>
[말아 넘기기:: GetScheme](curl-class.md#getscheme)
