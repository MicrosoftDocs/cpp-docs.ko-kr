---
description: pragmaMicrosoft C/c + +의 setlocale 지시문에 대해 자세히 알아보세요.
title: setlocale pragma
ms.date: 01/22/2021
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragma, setlocale
- setlocale pragma
no-loc:
- pragma
ms.openlocfilehash: 936aa1c2eb26798438b48e61ec28007a12080f28
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713209"
---
# <a name="setlocale-no-locpragma"></a>`setlocale` pragma

와이드 문자 상수와 문자열 리터럴을 변환할 때 사용할 *로캘*, 국가, 지역 및 언어를 정의 합니다.

## <a name="syntax"></a>구문

> **`#pragma setlocale( "`** [ *로캘-문자열* ] **`" )`**

## <a name="remarks"></a>설명

멀티 바이트 문자를 와이드 문자로 변환 하는 알고리즘은 로캘에 따라 다를 수 있으며 실행 파일이 실행 되는 다른 로캘에서 컴파일이 발생할 수 있습니다 .이는 pragma 컴파일 타임에 대상 로캘을 지정 하는 방법을 제공 합니다. 와이드 문자 문자열은 올바른 형식으로 저장 됩니다.

기본 *로캘 문자열* 은에 의해 지정 된 빈 문자열입니다 `#pragma setlocale( "" )` .

**`"C"`** 로캘은 문자열의 각 문자를 값으로에 매핑합니다 **`wchar_t`** . 에 유효한 다른 값 `setlocale` 은 [언어 문자열](../c-runtime-library/language-strings.md) 목록에 있는 항목입니다. 예를 들어 다음과 같이 지정할 수 있습니다.

```cpp
#pragma setlocale("dutch")
```

언어 문자열을 지정 하는 기능은 컴퓨터의 코드 페이지 및 언어 ID 지원에 따라 달라 집니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
