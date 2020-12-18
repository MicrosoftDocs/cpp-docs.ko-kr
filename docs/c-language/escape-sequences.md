---
description: '자세한 정보: 이스케이프 시퀀스'
title: 이스케이프 시퀀스
ms.date: 11/04/2016
helpviewer_keywords:
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "form feed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\n escape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
ms.openlocfilehash: 860c9b490a0d67f27da612f113cf6233f32b7188
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196544"
---
# <a name="escape-sequences"></a>이스케이프 시퀀스

백슬래시( **\\** ) 뒤에 한 문자나 숫자 조합이 오는 문자 조합을 "이스케이프 시퀀스"라고 합니다. 줄 바꿈 문자, 작은따옴표, 또는 문자 상수의 다른 특정 문자를 나타내려면 이스케이프 시퀀스를 사용해야 합니다. 이스케이프 시퀀스는 단일 문자로 간주되므로 문자 상수로 유효합니다.

이스케이프 시퀀스는 일반적으로 터미널과 프린터의 캐리지 리턴 및 탭 이동과 같은 동작을 지정하는 데 사용됩니다. 또한 인쇄할 수 없는 문자 및 큰따옴표( **"** )와 같이 일반적으로 특별한 의미를 가진 문자의 리터럴 표현을 제공하는 데 사용됩니다. 다음 표에서는 ANSI 이스케이프 시퀀스 및 나타내는 사항을 보여 줍니다.

앞에 백슬래시가 오는 물음표( **\\?** )는 문자 시퀀스가 삼중자로 잘못 해석되는 경우 리터럴 물음표를 지정합니다. 자세한 내용은 [삼중자](../c-language/trigraphs.md)를 참조하세요.

### <a name="escape-sequences"></a>이스케이프 시퀀스

|이스케이프 시퀀스|표현|
|---------------------|----------------|
|**\a**|벨(경고)|
|**\b**|백스페이스|
|**\f**|폼 피드|
|**\n**|줄 바꿈|
|**\r**|캐리지 리턴|
|**\t**|가로 탭|
|**\v**|세로 탭|
|**\\'**|작은따옴표|
|**\\"**|큰따옴표|
|**\\\\**|백슬래시|
|**\\?**|리터럴 물음표|
|**\\** *ooo*|8진수 표기법의 ASCII 문자|
|**\x** *hh*|16진수 표기법의 ASCII 문자|
|**\x** *hhhh*|이 이스케이프 시퀀스가 와이드 문자 상수 또는 유니코드 문자열 리터럴에 사용되는 경우 16진수 표기법의 유니코드 문자입니다.<br /><br /> 예를 들어 `WCHAR f = L'\x4e00'` 또는 `WCHAR b[] = L"The Chinese character for one is \x4e00"`로 이름을 지정할 수 있습니다.|

**Microsoft 전용**

표에 없는 문자 앞에 백슬래시가 오는 경우 컴파일러는 정의되지 않은 문자를 문자 자체로 처리합니다. 예를 들어 `\c`는 `c`로 처리됩니다.

**Microsoft 전용 종료**

이스케이프 시퀀스를 사용하여 디스플레이 디바이스에 비그래픽 제어 문자를 보낼 수 있습니다. 예를 들어 ESC 문자( **\033**)는 터미널 또는 프린터에 대한 제어 명령의 첫 문자로 자주 사용됩니다. 일부 이스케이프 시퀀스는 디바이스별로 적용됩니다. 예를 들어 세로 탭 및 용지 공급 이스케이프 시퀀스( **\v** 및 **\f**)는 화면 출력에는 영향을 주지 않고 해당 프린터 작업을 수행합니다.

백슬래시( **\\** )를 연속 문자로 사용할 수도 있습니다. 줄 바꿈 문자(Return 키 누름과 같음)가 백슬래시 바로 뒤에 오는 경우 컴파일러는 백슬래시와 줄 바꿈 문자를 무시하고 다음 줄을 앞 줄의 일부로 처리합니다. 한 줄보다 긴 전처리기 정의에 주로 유용합니다. 예를 들어:

```
#define assert(exp) \
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )
```

## <a name="see-also"></a>참조

[C 문자 상수](../c-language/c-character-constants.md)
