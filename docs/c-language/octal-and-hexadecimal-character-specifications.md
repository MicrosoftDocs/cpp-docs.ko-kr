---
description: '자세한 정보: 8진 및 16진 문자 사양'
title: 8진 및 16진 문자 사양
ms.date: 11/04/2016
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
ms.openlocfilehash: 91646244a30cb3ec5ad965914f1bee855fba05d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243278"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>8진 및 16진 문자 사양

**\\** <em>ooo</em> 시퀀스는 ASCII 문자 집합의 문자를 세 자리 8진수 문자 코드로 지정할 수 있음을 의미합니다. 8진수 정수의 숫자 값은 원하는 문자 또는 와이드 문자의 값을 지정합니다.

마찬가지로 **\x**<em>hhh</em> 시퀀스를 사용하면 ASCII 문자를 16진수 문자 코드로 지정할 수 있습니다. 예를 들어, ASCII 백스페이스 문자를 표준 C 이스케이프 시퀀스( **\b**)로 지정하거나 **\010**(8진수) 또는 **\x008**(16진수)로 코딩할 수 있습니다.

8진수 이스케이프 시퀀스에 0부터 7까지의 숫자만 사용할 수 있습니다. 8진수 이스케이프 시퀀스는 길이가 3자리 이내여야 하며 8진수가 아닌 첫 번째 문자로 끝납니다. 3자리 숫자를 모두 사용할 필요는 없지만 하나 이상 사용해야 합니다. 예를 들어, 8진수 표현은 ASCII 차트에 지정된 대로 ASCII 백스페이스 문자에 대해 **\10** 이고 문자 A에 대해 **\101** 입니다.

마찬가지로 16진수 이스케이프 시퀀스에 대해 하나 이상의 숫자를 사용해야 하지만 두 번째 숫자와 세 번째 숫자를 생략할 수 있습니다. 따라서 백스페이스 문자의 16진수 이스케이프 시퀀스를 **\x8**, **\x08** 또는 **\x008** 로 지정할 수 있습니다.

8진수 또는 16진수 이스케이프 시퀀스의 값은 문자 상수에 **`unsigned char`** 형식 및 와이드 문자 상수에 대한 **`wchar_t`** 형식의 표현할 수 있는 값 범위에 있어야 합니다. 와이드 문자 상수에 대한 자세한 내용은 [멀티바이트 및 와이드 문자](../c-language/multibyte-and-wide-characters.md)를 참조하세요.

8진수 이스케이프 상수와 달리 이스케이프 시퀀스의 16진수 개수에는 제한이 없습니다. 16진수 이스케이프 시퀀스는 16진수가 아닌 첫 번째 문자에서 종결됩니다. 16진수에는 **a** 부터 **f** 까지의 문자가 포함되므로 이스케이프 시퀀스가 올바른 숫자에서 종결되도록 주의해야 합니다. 혼동을 피하기 위해 8진수나 16진수 문자 정의를 매크로 정의에 배치할 수 있습니다.

```
#define Bell '\x07'
```

16진수 값의 경우 문자열을 나누어 올바른 값을 분명하게 표시할 수 있습니다.

```
"\xabc"    /* one character  */
"\xab" "c" /* two characters */
```

## <a name="see-also"></a>참조

[C 문자 상수](../c-language/c-character-constants.md)
