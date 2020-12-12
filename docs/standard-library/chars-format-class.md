---
description: '다음에 대 한 자세한 정보: 열거형 chars_format'
title: chars_format 열거형
ms.date: 08/03/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: af458f96e3e9dbe4db9d1adab1c529403cefcaa6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325183"
---
# <a name="chars_format-enum"></a>chars_format 열거형

라이브러리와 함께 사용 되어 [\<charconv>](charconv.md) 기본 숫자 변환에 대 한 부동 소수점 형식을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum class chars_format {
    scientific = unspecified,
    fixed = unspecified,
    hex = unspecified,
    general = fixed | scientific
};
```

### <a name="members"></a>멤버

|요소|설명|
|-|-|
| `scientific` | 에서 `from_chars()` 지 수를 예측 하 고 구문 분석 합니다. `printf()` `'e'` 과 같은 과학적 표기법의 형식을 지정 하는 서식 지정자와 비슷합니다 `"1.729e+01"` . |
| `fixed` | `from_chars()`는 지 수를 예측 하거나 구문 분석 하지 않습니다. `printf()`과 같이 부동 소수점 형식을 지정 하는 서식 지정자와 비슷합니다 `'f'` `"17.29"` .|
| `hex` | `from_chars()`는 숫자를 16 진수 형식으로 간주 하지만 앞에는 표시 되지 않습니다 `0x` . |
| `general` | `from_chars()`에서 지수가 허용 되지만 필요 하지는 않습니다. 의 경우 `to_chars()` `printf()` `'g'` 과학적 표기법 또는 고정을 전환 하는 형식 지정자와 비슷합니다. 합리적인 출력을 생성할 수 있도록 지수가 무엇 인지 고려 합니다. 예: `1e-5` 의 결과 `"1e-05"` 는 이지만이 `1e-4` 발생 `"0.001"` 합니다. `1e5` 에서 결과 `100000` 를 반환 `1e6` `1e+06` 합니다. `1e0``1`을 생성 합니다.|

## <a name="remarks"></a>설명

[From_chars](charconv-functions.md#from_chars) 함수의 경우이 열거형은 필요한 입력의 종류를 설명 합니다.
[To_chars](charconv-functions.md#to_chars) 함수의 경우 내보낼 출력의 종류를 설명 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<charconv>

**네임스페이스:** std

/std: c + + 17 이상이 필요 합니다.

## <a name="see-also"></a>참고 항목

[\<charconv>](../standard-library/charconv.md)  
[printf () 서식 지정자](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)
