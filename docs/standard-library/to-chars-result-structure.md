---
description: '다음에 대 한 자세한 정보: to_chars_result 구조체'
title: to_chars_result 구조체
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars_result
helpviewer_keywords:
- to_chars_result class
- to_chars_result structure
ms.openlocfilehash: fb043ba928f086549aea326419ec3a2d673723ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167190"
---
# <a name="to_chars_result-struct"></a>to_chars_result 구조체

## <a name="syntax"></a>구문

```cpp
struct to_chars_result {
    char* ptr;
    errc ec;
};
```

## <a name="members"></a>멤버

|멤버|설명|
|--|--|
|`ptr`| `ec`가와 같으면 `errc{}` 변환이 성공적으로 수행 되 고,는 문자를 기반으로 하는 문자를 벗어난 `ptr` 끝 포인터입니다. 그렇지 않으면 `ptr` 매개 변수의 값이이 `to_chars()` `last` 고, \[ first, last 등 범위의 내용이 지정 되지 않습니다.|
|`ec` | 변환 오류 코드입니다. 특정 오류 코드는를 참조 하십시오 [`errc`](system-error-enums.md#errc) .|

## <a name="requirements"></a>요구 사항

**헤더:**\<charconv>

**네임스페이스:** std

**컴파일러 옵션:** /ostd: c + + 17 이상이 필요 합니다.

## <a name="see-also"></a>참고 항목

[to_chars](charconv-functions.md#to_chars)
