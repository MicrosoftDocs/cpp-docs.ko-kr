---
description: '자세한 정보: &lt; charconv&gt;'
title: '&lt;charconv&gt;'
ms.date: 07/22/2020
f1_keywords:
- <charconv>
helpviewer_keywords:
- charconv header
ms.openlocfilehash: 9faab40d2b601317e9dd739053c31000da5ea18b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325210"
---
# <a name="ltcharconvgt"></a>&lt;charconv&gt;

문자 시퀀스를 정수 또는 부동 소수점 값으로 빠르게 변환 하 고 그 밖의 다른 방법으로 변환 합니다.
이 라이브러리를 사용 하는 한 가지 방법은 JSON 및 텍스트 파일에서 부동 소수점 값을 쓰고 라운드트립 하는 것입니다.

변환 함수는 성능을 위해 조정 되며 최단 왕복 동작을 지원 합니다. 최단 왕복 동작 이란 숫자를 문자로 변환 하는 경우 해당 문자를 다시 부동 소수점으로 변환 하는 경우 원래 숫자를 복구할 수 있도록 충분 한 소수 자릿수가 기록 됨을 의미 합니다. 다른 CRT 또는 STL 함수는이 기능을 제공 하지 않습니다.

라이브러리 사용의 이점 중 일부는 `<charconv>` 다음과 같습니다.

- 숫자 값을 나타내는 문자 시퀀스는 null로 종료할 필요가 없습니다. 마찬가지로 숫자가 문자로 변환 되는 경우 결과는 null로 종료 되지 않습니다.
- 변환 함수는 메모리를 할당 하지 않습니다. 모든 경우에서 버퍼를 소유 합니다.
- 변환 함수는를 throw 하지 않습니다. 오류 정보를 포함 하는 구조체를 반환 합니다.
- 변환은 런타임 반올림 모드를 구분 하지 않습니다.
- 변환은 로캘이 인식 되지 않습니다. 쉼표를 사용 하는 로캘의 경우 항상 '. '로 '. '로 소수점을 인쇄 하 고 구문 분석 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<charconv>

**네임스페이스:** std

/std: c + + 17 이상이 필요 합니다.

## <a name="members"></a>멤버

### <a name="types"></a>유형

| 형식 | 설명 |
|-|:-|
| [chars_format](chars-format-class.md) | 과학적, hex 등의 형식 지정 형식을 지정 합니다. |
| [from_chars_result](from-chars-result-structure.md) | 변환 결과를 포함 합니다 `from_chars` . |
| [to_chars_result](to-chars-result-structure.md) | 변환 결과를 포함 합니다 `to_chars` . |

### <a name="functions"></a>Functions

| 함수 | 설명 |
|-|:-|
| [from_chars](charconv-functions.md#from_chars) | 문자를 정수, 부동 소수점 또는 double로 변환 합니다. |
| [to_chars](charconv-functions.md#to_chars)| Integer, float 또는 double을 chars로 변환 합니다. |

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](cpp-standard-library-header-files.md)
