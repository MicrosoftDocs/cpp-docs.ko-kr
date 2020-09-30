---
title: __argc, __argv, __wargv
description: Microsoft C 런타임 라이브러리 전역 상수, 및에 대해 설명 합니다 __argc __argv __wargv .
ms.date: 11/04/2016
api_name:
- __wargv
- __argv
- __argc
api_location:
- msvcrt120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
no-loc:
- __argc
- __argv
- __wargv
- main
- wmain
ms.openlocfilehash: 02c130be0d2dcb8e48d2bb5c75438c94003fc9dd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507592"
---
# <a name="no-loc__argc-no-loc__argv-no-loc__wargv"></a>__argc, __argv, __wargv

`__argc` 전역 변수는 프로그램에 전달된 명령줄 인수의 수입니다. `__argv`는 프로그램 인수가 포함된 싱글바이트 문자 또는 멀티바이트 문자열의 배열에 대한 포인터이고 `__wargv`는 프로그램 인수가 포함된 와이드 문자열의 배열에 대한 포인터입니다. 이러한 전역 변수는 `main` 또는 `wmain`에 인수를 제공합니다.

## <a name="syntax"></a>구문

```C
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>설명

`main` 함수를 사용하는 프로그램에서 `__argc` 및 `__argv`는 프로그램 시작에 사용되는 명령줄을 사용하여 프로그램 시작 시 초기화됩니다. 해당 명령줄이 개별 인수로 구문 분석되고 와일드카드가 확장됩니다. 인수의 수가 `__argc`에 할당되고 인수 문자열이 힙에서 할당되며 인수 배열에 대한 포인터가 `__argv`에 할당됩니다. 와이드 문자 및 `wmain` 함수를 사용하도록 컴파일된 프로그램에서 인수는 구문 분석되고 와일드카드는 와이드 문자열로 확장되며 인수 문자열의 배열에 대한 포인터는 `__wargv`에 할당됩니다.

이식 가능한 코드의 경우 `main`에 전달된 인수를 사용하여 프로그램에서 명령줄 인수를 가져오는 것이 좋습니다.

### <a name="generic-text-routine-mappings"></a>일반 텍스트 루틴 매핑

|Tchar.h 루틴|_UNICODE가 정의되지 않음|_UNICODE 정의됨|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>요구 사항

|전역 변수|필수 헤더|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C + +)|

`__argc`, `__argv` 및 `__wargv`는 Microsoft 확장입니다. 호환성에 대한 내용은 [호환성](../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[전역 변수](../c-runtime-library/global-variables.md)\
[main 함수 및 명령줄 인수 (c + +)](../cpp/main-function-command-line-args.md)\
[wmain대신 사용main](../cpp/main-function-command-line-args.md)
