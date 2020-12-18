---
description: '자세한 정보: 멀티바이트 및 와이드 문자'
title: 멀티바이트 및 와이드 문자
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
ms.openlocfilehash: 48063824b66df42d41b51ca491b0eec5f7679274
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243395"
---
# <a name="multibyte-and-wide-characters"></a>멀티바이트 및 와이드 문자

멀티바이트 문자는 하나 이상의 바이트의 시퀀스로 구성된 문자입니다. 각 바이트 시퀀스는 확장된 문자 집합에서 단일 문자를 나타냅니다. 멀티바이트 문자는 한자와 같은 문자 집합에 사용됩니다.

와이드 문자는 항상 16비트 크기의 다국어 문자 코드입니다. 문자 상수 형식은 **`char`** 이며 와이드 문자 형식은 **`wchar_t`** 입니다. 와이드 문자의 크기는 항상 고정되어 있으므로 와이드 문자를 사용하면 국제 공용 문자 집합으로 단순하게 프로그래밍할 수 있습니다.

와이드 문자열 리터럴, `L"hello"`는 **`wchar_t`** 형식의 6개의 정수 배열이 됩니다.

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

유니코드 사양은 와이드 문자에 대한 사양입니다. 멀티바이트 및 와이드 문자 간 변환을 위한 런타임 라이브러리 루틴에는 `mbstowcs`, `mbtowc`, `wcstombs` 및 `wctomb`가 있습니다.

## <a name="see-also"></a>참조

[C 식별자](../c-language/c-identifiers.md)
