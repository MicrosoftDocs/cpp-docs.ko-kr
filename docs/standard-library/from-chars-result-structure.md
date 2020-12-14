---
description: '다음에 대 한 자세한 정보: from_chars_result 구조체'
title: from_chars_result 구조체
ms.date: 7/23/2020
f1_keywords:
- std::from_chars_result
helpviewer_keywords:
- from_chars_result class
- from_chars_result structure
ms.openlocfilehash: 894a687a4395e22538b384675af5b4ce57731f78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232280"
---
# <a name="from_chars_result-struct"></a>from_chars_result 구조체

## <a name="syntax"></a>Syntax

```cpp
struct from_chars_result {
    const char* ptr;
    errc ec;
};
```

|멤버|설명|
|--|--|
|`ptr`| `ec`가와 같으면 `errc{}` 변환이 성공 하 고 `ptr` 인식할 수 없는 숫자의 일부가 아닌 첫 번째 문자를 가리킵니다. |
|`ec` | 변환 오류 코드입니다. 특정 오류 코드는를 참조 하십시오 [`errc`](system-error-enums.md#errc) .|

### <a name="remarks"></a>설명

예를 들어 `"1729cats"` , 10 진수 정수로 구문 분석은 성공 하 고는 `ptr` `'c'` 첫 번째 숫자가 아닌를 가리키고는의 끝 부분에 해당 하는를 가리킵니다 `"1729"` .

숫자 패턴에 일치 하는 문자가 없는 경우 `from_chars_result.ptr` 는를 가리키며 `first` `from_chars_result.ec` 은 `errc::invalid_argument` 입니다.

일부 문자만 숫자 패턴과 일치 하는 경우는 `from_chars_result.ptr` 패턴이 일치 하지 않는 첫 번째 문자를 가리키거나 `last` 모든 문자가 일치 하는 경우 매개 변수의 값을 갖습니다.

구문 분석 된 값이 수행할 변환의 형식에 맞지 않는 경우 `from_chars_result.ec` 는 `errc::result_out_of_range` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<charconv>

**네임스페이스:** std

**컴파일러 옵션:** /ostd: c + + 17 이상이 필요 합니다.

## <a name="see-also"></a>참고 항목

[from_chars](charconv-functions.md#from_chars)
