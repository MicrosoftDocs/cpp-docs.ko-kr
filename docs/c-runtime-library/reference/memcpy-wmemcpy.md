---
description: Memcpy, wmemcpy에 대해 자세히 알아보세요.
title: memcpy, wmemcpy
ms.date: 1/14/2021
api_name:
- memcpy
- wmemcpy
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: 49b08877f63bf0d331dcc40e2885b375fe6d1ee7
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243140"
---
# <a name="memcpy-wmemcpy"></a>`memcpy`, `wmemcpy`

버퍼 간에 바이트를 복사합니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [ `memcpy_s` 을 `wmemcpy_s` ](memcpy-s-wmemcpy-s.md)참조 하십시오.

## <a name="syntax"></a>구문

```C
void *memcpy(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemcpy(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>매개 변수

*`dest`*\
새 버퍼입니다.

*`src`*\
복사할 버퍼입니다.

*`count`*\
복사할 문자 수입니다.

## <a name="return-value"></a>반환 값

의 값 *`dest`* 입니다.

## <a name="remarks"></a>설명

**`memcpy`***`count`* 에서로 바이트 *`src`* 를 복사 하 *`dest`* 고 **`wmemcpy`** *`count`* 와이드 문자 (2 바이트)를 복사 합니다. 소스와 대상이 겹치는 경우의 동작이 **`memcpy`** 정의 되지 않습니다. **`memmove`** 겹치는 영역을 처리 하는 데 사용 합니다.

> [!IMPORTANT]
> 대상 버퍼의 크기가 소스 버퍼의 크기보다 크거나 같아야 합니다. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

> [!IMPORTANT]
> 의 부적절 한 사용에 대 한 많은 버퍼 오버런 및 잠재적인 보안 익스플로잇이 추적 되었으므로 **`memcpy`** 이 함수는 SDL (보안 개발 수명 주기)에 의해 "금지" 된 기능 사이에 나열 됩니다.  일부 VC + + 라이브러리 클래스는 계속 사용 됨을 확인할 수 있습니다 **`memcpy`** .  또한 VC + + 컴파일러 최적화 프로그램에서에 대 한 호출을 내보내는 경우도 있습니다 **`memcpy`** .  Visual C++ 제품은 SDL 프로세스에 따라 개발되었으므로 이처럼 금지된 함수의 사용이 철저하게 평가되었습니다.  라이브러리에서 이러한 함수를 사용하는 경우에는 이러한 호출을 통해 버퍼 오버런이 허용되지 않도록 호출을 면밀하게 검사했습니다.  컴파일러의 경우 특정 코드 패턴이의 패턴과 동일한 것으로 인식 되어 **`memcpy`** 함수 호출로 대체 되는 경우도 있습니다.  이러한 경우를 사용 하는 것은 **`memcpy`** 원래 지침 보다 안전 하지 않으며, 성능 조정 함수에 대 한 호출에만 최적화 되어 있습니다. **`memcpy`**  "Safe" CRT 함수를 사용 하는 것은 안전 하지 않습니다. 즉, 안전 하지 않기 때문에 "금지 된" 기능을 사용 하는 것은 위험을 보장 하지 않습니다 (안전을 보장 하기 위해 더 높은 검사가 필요 함).
>
> **`memcpy`** VC + + 컴파일러 및 라이브러리의 사용이 신중 하 게 협동할 때문에 이러한 호출은 SDL과 호환 되는 코드 내에서 허용 됩니다.  **`memcpy`** 응용 프로그램 소스 코드에 도입 된 호출은 보안 전문가가 해당 사용을 검토 한 경우에만 SDL과 호환 됩니다.

**`memcpy`** **`wmemcpy`** **`_CRT_SECURE_DEPRECATE_MEMORY`** 아래 예제와 같이 함수가 더 이상 사용 되지 않도록 하려면 포함 문 앞에 상수가 정의 되어 있는 경우에만 및 함수가 사용 되지 않습니다.

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

또는

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`memcpy`**|`<memory.h>` 또는 `<string.h>`|
|**`wmemcpy`**|`<wchar.h>`|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예

을 [`memmove`](memmove-wmemmove.md) 사용 하는 방법에 대 한 샘플은를 참조 하세요 **`memcpy`** .

## <a name="see-also"></a>참고 항목

[버퍼 조작](../../c-runtime-library/buffer-manipulation.md)\
[`_memccpy`](memccpy.md)\
[`memchr`, `wmemchr`](memchr-wmemchr.md)\
[`memcmp`, `wmemcmp`](memcmp-wmemcmp.md)\
[`memmove`, `wmemmove`](memmove-wmemmove.md)\
[`memset`, `wmemset`](memset-wmemset.md)\
[`strcpy_s`, `wcscpy_s`, `_mbscpy_s`](strcpy-s-wcscpy-s-mbscpy-s.md)\
[`strncpy_s`, `_strncpy_s_l`, `wcsncpy_s`, `_wcsncpy_s_l`, `_mbsncpy_s`, `_mbsncpy_s_l`](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)\
