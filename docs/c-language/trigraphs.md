---
description: '자세한 정보: 삼중자'
title: 삼중자
ms.date: 11/04/2016
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
ms.openlocfilehash: 70844472de698b581f33adea5dd6b6fa5cdfc8fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243070"
---
# <a name="trigraphs"></a>삼중자

C 소스 프로그램의 소스 문자 집합은 7비트 ASCII 문자 집합에 포함되지만 ISO 646-1983 고정 코드 집합의 상위 집합입니다. 삼중자 시퀀스를 사용하면 C 프로그램을 ISO(International Standards Organization) 고정 코드 집합만을 사용하여 쓸 수 있습니다. 삼중자는 컴파일러가 해당 문장 부호 문자로 대체하는 세 문자(두 개의 연속된 물음표로 시작)의 시퀀스입니다. 삼중자는 특정 문장 부호 문자에 대한 편리한 그래픽 표현을 포함하지 않는 문자 집합이 사용되는 C 소스 파일에서 사용할 수 있습니다.

C++17의 언어에서는 삼중자가 제거됩니다. 구현에서는 실제 원본 파일에서 *기본 원본 문자 집합* 으로의 구현이 정의된 매핑의 일부분으로 삼중자가 계속 지원될 수도 있지만, 표준에 따라 구현에서 삼중자를 지원하지 않는 것이 좋습니다. C++14까지는 삼중자가 C에서처럼 지원됩니다.

Visual C++에서는 삼중자 대체가 계속 지원되지만 기본적으로는 사용할 수 없습니다. 삼중자 대체를 사용하도록 설정하는 방법에 대한 자세한 내용은 [`/Zc:trigraphs`(삼중자 대체)](../build/reference/zc-trigraphs-trigraphs-substitution.md)를 참조하세요.

다음 표에서는 9개의 삼중자 시퀀스를 보여 줍니다. 첫 번째 열에서 문장 부호 문자의 소스 파일에 있는 모든 항목은 두 번째 열의 해당 문자로 바뀝니다.

### <a name="trigraph-sequences"></a>삼중자 시퀀스

| 삼중자 | 문장 부호 문자 |
|----------|-----------------------|
| `??=` | `#` |
| `??(` | `[` |
| `??/` | `\` |
| `??)` | `]` |
| `??'` | `^` |
| `??<` | `{` |
| `??!` | `|` |
| `??>` | `}` |
| `??-` | `~` |

삼중자는 항상 단일 소스 문자로 처리됩니다. 삼중자 변환은 문자열 리터럴 및 문자 상수에서 이스케이프 문자를 인식하기 전에 첫 번째 [변환 단계](../preprocessor/phases-of-translation.md)에서 발생합니다. 위의 표에 나와 있는 9개의 삼중자만 인식됩니다. 다른 모든 문자 시퀀스는 변환되지 않고 유지됩니다.

문자 이스케이프 시퀀스인 **`\?`** 는 삼중자와 비슷한 문자 시퀀스가 잘못 해석되는 것을 방지합니다. 이스케이프 시퀀스에 대한 자세한 내용은 [이스케이프 시퀀스](../c-language/escape-sequences.md)를 참조하세요. 예를 들어, `What??!` 문자열을 이 `printf` 문으로 출력하려고 하면

```C
printf( "What??!\n" );
```

`What|`라는 문자열이 출력됩니다. 이는 `??!`가 `|` 문자로 바뀌는 삼중자 시퀀스이기 때문입니다. 문자열을 올바르게 출력하려면 다음과 같이 문을 작성하십시오.

```C
printf( "What?\?!\n" );
```

이 `printf` 문에서 두 번째 물음표 앞에 있는 백슬래시 이스케이프 문자는 `??!`가 삼중자로 잘못 해석되지 않게 합니다.

## <a name="see-also"></a>참조

[`/Zc:trigraphs`(삼중자 대체)](../build/reference/zc-trigraphs-trigraphs-substitution.md)<br/>
[C 식별자](../c-language/c-identifiers.md)
