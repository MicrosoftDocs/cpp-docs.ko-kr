---
description: '다음에 대 한 자세한 정보: __security_init_cookie'
title: __security_init_cookie
ms.date: 11/04/2016
api_name:
- __security_init_cookie
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: 48051eb34e7fe9fe1e32e41849072f71d6665d94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288947"
---
# <a name="__security_init_cookie"></a>__security_init_cookie

전역 보안 쿠키를 초기화합니다.

## <a name="syntax"></a>구문

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>설명

전역 보안 쿠키는 [/GS(버퍼 보안 검사)](../../build/reference/gs-buffer-security-check.md)를 사용하여 컴파일된 코드와 예외 처리를 사용하는 코드에서 버퍼 오버런을 방지하는 데 사용됩니다. 오버런 방지 함수로 진입 시 쿠키가 스택에 배치되며 해당 함수 종료 시 스택의 값을 전역 쿠키와 비교합니다. 쿠키의 값이 서로 다르면 버퍼 오버런이 발생한 것이며 프로그램이 즉시 종료됩니다.

일반적으로 **__security_init_cookie** 는 CRT가 초기화 될 때 호출 됩니다. CRT 초기화를 무시 하는 경우 (예: [/entry](../../build/reference/entry-entry-point-symbol.md) 를 사용 하 여 진입점을 지정 하는 경우) **__security_init_cookie** 직접 호출 해야 합니다. **__Security_init_cookie** 를 호출 하지 않으면 전역 보안 쿠키가 기본값으로 설정 되며 버퍼 오버런 방지가 손상 됩니다. 공격자는이 기본 쿠키 값을 악용 하 여 버퍼 오버런 검사를 수행할 수 있으므로 사용자 고유의 진입점을 정의할 때 항상 **__security_init_cookie** 를 호출 하는 것이 좋습니다.

**__Security_init_cookie** 에 대 한 호출은 오버런 방지 함수를 입력 하기 전에 수행 해야 합니다. 그렇지 않으면 의사 버퍼 오버런이 검색 됩니다. 자세한 내용은 [C 런타임 오류 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)를 참조하세요.

## <a name="example"></a>예제

[C 런타임 오류 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)의 예제를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie** 는 표준 C 런타임 라이브러리에 대 한 Microsoft 확장입니다. 호환성에 대한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[Microsoft 보안 대응 센터](https://www.microsoft.com/msrc?rtc=1)
