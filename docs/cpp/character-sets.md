---
description: '자세한 정보: 토큰 및 문자 집합'
title: 토큰 및 문자 집합
ms.date: 12/10/2019
helpviewer_keywords:
- Tokens (C++)
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: b5a6868f5e4c01772758acaa0e44459e72b16a84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308473"
---
# <a name="tokens-and-character-sets"></a>토큰 및 문자 집합

C + + 프로그램의 텍스트는 토큰과 *공백으로* 구성 됩니다. 토큰은 컴파일러에 의미 있는 C++ 프로그램의 최소 요소입니다. C + + 파서는 다음과 같은 종류의 토큰을 인식 합니다.

- [C++ 키워드](../cpp/keywords-cpp.md)
- [식별자](../cpp/identifiers-cpp.md)
- [숫자, 부울 및 포인터 리터럴](../cpp/numeric-boolean-and-pointer-literals-cpp.md)
- [문자열 및 문자 리터럴](../cpp/string-and-character-literals-cpp.md)
- [사용자 정의 리터럴](../cpp/user-defined-literals-cpp.md)
- [연산자](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
- [문장 부호](../cpp/punctuators-cpp.md)

토큰은 일반적으로 *공백* 으로 구분 되며, 하나 이상이 될 수 있습니다.

- 공백
- 가로 또는 세로 탭
- 새로운 줄
- 양식 피드
- 의견

## <a name="basic-source-character-set"></a>기본 소스 문자 집합

C + + 표준에서는 소스 파일에서 사용할 수 있는 *기본 소스 문자 집합* 을 지정 합니다. 이 집합 외부에 문자를 나타내려면 *유니버설 문자 이름* 을 사용하여 추가 문자를 지정할 수 있습니다. MSVC 구현은 추가 문자를 허용 합니다. *기본 소스 문자 집합* 은 소스 파일에서 사용할 수 있는 96 문자로 구성 됩니다. 이 집합에는 공백 문자, 가로 탭, 세로 탭, 폼 피드 및 줄 바꿈 제어 문자가 포함되며 다음 그래픽 문자 집합도 포함됩니다.

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Microsoft 전용**

MSVC에는 `$` 문자를 기본 소스 문자 집합의 멤버로 포함 합니다. 또한 MSVC를 사용 하면 파일 인코딩에 따라 소스 파일에서 추가 문자 집합을 사용할 수 있습니다. 기본적으로 Visual Studio는 기본 코드 페이지를 사용하여 소스 파일을 저장합니다. 로캘 관련 코드 페이지 또는 유니코드 코드 페이지를 사용 하 여 소스 파일을 저장 하면 MSVC를 사용 하 여 기본 소스 문자 집합에서 명시적으로 허용 되지 않는 제어 코드를 제외 하 고 소스 코드에서 해당 코드 페이지의 모든 문자를 사용할 수 있습니다. 예를 들어 일본어 코드 페이지를 사용하여 파일을 저장하는 경우 주석, 식별자 또는 문자열 리터럴에 일본어 문자를 배치할 수 있습니다. MSVC는 유효한 멀티 바이트 문자 또는 유니코드 코드 포인트로 변환할 수 없는 문자 시퀀스를 허용 하지 않습니다. 컴파일러 옵션에 따라 허용되는 일부 문자가 식별자에 나타나지 않을 수 있습니다. 자세한 내용은 [식별자](../cpp/identifiers-cpp.md)를 참조하세요.

**Microsoft 전용 종료**

### <a name="universal-character-names"></a>유니버설 문자 이름

C++ 프로그램에서는 기본 소스 문자 집합에 지정된 것보다 훨씬 더 많은 문자를 사용할 수 있으므로 *유니버설 문자 이름* 을 사용하여 이식 가능한 방법으로 이러한 문자를 지정할 수 있습니다. 유니버설 문자 이름은 유니코드 코드 포인트를 나타내는 문자 시퀀스로 구성되며,  두 가지 형식을 사용합니다. `\UNNNNNNNN` 을 사용하여 U+NNNNNNNN 형식의 유니코드 코드 포인터를 나타냅니다. 여기서 NNNNNNNN은 8자리 16진수 코드 포인트 번호입니다. 4자리 `\uNNNN` 을 사용하여 U+0000NNNN 형식의 유니코드 코드 포인트를 나타냅니다.

유니버설 문자 이름은 문자열 및 문자 리터럴과 식별자에서 사용할 수 있습니다. 유니버설 문자 이름은 0xD800-0xDFFF 범위에 있는 서로게이트 코드 포인트를 나타내는 데 사용할 수 없습니다. 대신 원하는 코드 포인트를 사용하면 컴파일러에서 필요한 서로게이트를 자동으로 생성합니다. 식별자에 사용할 수 있는 유니버설 문자 이름에는 추가 제한이 적용됩니다. 자세한 내용은 [Identifiers](../cpp/identifiers-cpp.md) 및 [String and Character Literals](../cpp/string-and-character-literals-cpp.md)을 참조하세요.

**Microsoft 전용**

Microsoft c + + 컴파일러는 유니버설 문자 이름 형식과 리터럴 형식의 문자를 서로 바꿔 처리 합니다. 예를 들어 유니버설 문자 이름 형식을 사용하여 식별자를 선언하고 리터럴 형식에서 사용할 수 있습니다.

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Windows 클립보드의 확장된 문자 형식은 애플리케이션 로캘 설정과 관련이 있습니다. 다른 애플리케이션에서 이러한 문자를 잘라내어 코드에 붙여 넣으면 예기치 않은 문자 인코딩이 발생할 수 있습니다. 그러면 표시되는 원인 없이 코드에서 구문 분석 오류가 발생할 수 있습니다. 따라서 확장된 문자를 붙여 넣기 전에 소스 파일 인코딩을 유니코드 코드 페이지로 설정하는 것이 좋습니다. 또한 IME 또는 문자표 앱을 사용하여 확장된 문자를 생성하는 것이 좋습니다.

**Microsoft 전용 종료**

### <a name="execution-character-sets"></a>실행 문자 집합

*실행 문자 집합* 은 컴파일된 프로그램에 나타날 수 있는 문자 및 문자열을 나타냅니다. 이러한 문자 집합은 소스 파일에서 허용 되는 모든 문자와 경고, 백스페이스, 캐리지 리턴 및 null 문자를 나타내는 제어 문자로 구성 됩니다. 실행 문자 집합에는 로캘별 표현이 있습니다.
