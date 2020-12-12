---
description: '자세한 정보: char, wchar_t, char16_t, char32_t'
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: f8bab56bf8a2cebe8409c9dc4ceecf931ec83260
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278794"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char, wchar_t, char16_t, char32_t

, 및 형식은 영숫자 문자 뿐만 아니라 영숫자가 아닌 문자 **`char`** **`wchar_t`** **`char16_t`** **`char32_t`** 모양 및 인쇄 되지 않는 문자를 나타내는 기본 제공 형식입니다.

## <a name="syntax"></a>구문

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>설명

**`char`** 형식은 C 및 c + +의 원래 문자 형식 이었습니다. 형식은 **`unsigned char`** c + +에서 기본 제공 형식이 아닌 *바이트* 를 나타내는 데 사용 되는 경우가 많습니다. **`char`** 형식은 ASCII 문자 집합 또는 ISO-8859 문자 집합의 문자를 저장 하는 데 사용할 수 있으며, shift-jis 또는 유니코드 문자 집합의 utf-8 인코딩과 같은 멀티 바이트 문자의 개별 바이트를 저장 하는 데 사용할 수 있습니다. 형식의 문자열 **`char`** 은 멀티 바이트 문자를 인코딩하는 데 사용 되는 경우에도 *좁은* 문자열 이라고 합니다. Microsoft 컴파일러에서 **`char`** 는 8 비트 형식입니다.

**`wchar_t`** 형식은 구현 시 정의 된 와이드 문자 형식입니다. Microsoft 컴파일러에서 Windows 운영 체제의 네이티브 문자 형식인 u t f-UTF-16LE로 인코딩된 유니코드를 저장 하는 데 사용 되는 16 비트 와이드 문자를 나타냅니다. C #의 와이드 문자 버전은 **`wchar_t`** 네이티브 WINDOWS API의 와이드 문자 버전과 마찬가지로 및 해당 포인터와 배열 형식을 매개 변수 및 반환 값으로 사용 합니다.

**`char16_t`** 및 **`char32_t`** 형식은 각각 16 비트 및 32 비트 와이드 문자를 나타냅니다. U t f-16으로 인코딩된 유니코드는 형식에 저장 될 수 있으며 **`char16_t`** u t f-32로 인코딩된 유니코드는 형식으로 저장 될 수 있습니다 **`char32_t`** . 이러한 형식 및의 문자열 **`wchar_t`** 은 모두 *와이드* 문자열 이라고 하며, 용어는 주로 형식의 문자열을 의미 합니다 **`wchar_t`** .

C + + 표준 라이브러리에서 `basic_string` 형식은 좁은 문자열과 와이드 문자열 모두에 대해 특수화 되어 있습니다. 문자가 형식이 면, 문자가 형식이 면, 문자가 형식이 면, 문자의 형식이 인 경우를 사용 `std::string` **`char`** `std::u16string` **`char16_t`** `std::u32string` **`char32_t`** `std::wstring` **`wchar_t`** 합니다. 및를 비롯 하 여 텍스트를 나타내는 다른 형식은 `std::stringstream` `std::cout` 좁은 문자열과 와이드 문자열에 대 한 특수화를 가집니다.
