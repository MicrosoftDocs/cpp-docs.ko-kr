---
description: '자세한 정보: 식별자 (c + +)'
title: 식별자(C++)
ms.date: 05/07/2019
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers [C++]
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
ms.openlocfilehash: 24798675940761eb7a2b8cbdeb6d63592bb4d05a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114015"
---
# <a name="identifiers-c"></a>식별자(C++)

식별자는 다음 중 하나를 나타내는 데 사용되는 문자 시퀀스입니다.

- 개체 또는 변수 이름

- 클래스, 구조체 또는 공용 구조체 이름

- 열거 형식 이름

- 클래스, 구조체, 공용 구조체 또는 열거의 멤버

- 함수 또는 클래스 멤버 함수

- typedef 이름

- 레이블 이름

- 매크로 이름

- 매크로 매개 변수

다음 문자는 식별자의 모든 문자로 허용됩니다.

```
_ a b c d e f g h i j k l m
n o p q r s t u v w x y z
A B C D E F G H I J K L M
N O P Q R S T U V W X Y Z
```

특정 범위의 유니버설 문자 이름도 식별자에서 허용됩니다.  식별자의 유니버설 문자 이름은 제어 문자나 기본 소스 문자 집합의 문자를 지정할 수 없습니다. 자세한 내용은 [Character Sets](../cpp/character-sets.md)을 참조하세요. 이러한 유니코드 코드 포인트 숫자 범위는 식별자의 모든 문자에 대해 유니버설 문자 이름으로 허용됩니다.

- 00A8, 00AA, 00AD, 00AF, 00B2-00B5, 00B7-00BA, 00BC-00BE, 00C0-00D6, 00D8-00F6, 00F8-00FF, 0100-02FF, 0370-167F, 1681-180D, 180F-1DBF, 1E00-1FFF, 200B-200D, 202A-202E, 203F-2040, 2054, 2060-206F, 2070-20CF, 2100-218F, 2460-24FF, 2776-2793, 2C00-2DFF, 2E80-2FFF, 3004-3007, 3021-302F, 3031-303F, 3040-D7FF, F900-FD3D, FD40-FDCF, FDF0-FE1F, FE30-FE44, FE47-FFFD, 10000-1FFFD, 20000-2FFFD, 30000-3FFFD, 40000-4FFFD, 50000-5FFFD, 60000-6FFFD, 70000-7FFFD, 80000-8FFFD, 90000-9FFFD, A0000-AFFFD, B0000-BFFFD, C0000-CFFFD, D0000-DFFFD, E0000-EFFFD

다음 문자는 식별자의 첫 번째 문자를 제외한 모든 문자로 허용됩니다.

```
0 1 2 3 4 5 6 7 8 9
```

이러한 유니코드 코드 포인트 숫자 범위는 식별자의 첫 번째 문자를 제외한 모든 문자에 대해 유니버설 문자 이름으로도 허용됩니다.

- 0300-036F, 1DC0-1DFF, 20D0-20FF, FE20-FE2F

**Microsoft 전용**

Microsoft C++ 식별자의 처음 2048 문자만 의미가 있습니다. 사용자 정의 형식의 이름은 컴파일러에서 "데코레이팅"되어 형식 정보를 유지합니다. 형식 정보를 포함하는 결과 이름은 2048자를 초과할 수 없습니다. 자세한 내용은 [데코레이팅된 이름](../build/reference/decorated-names.md) 을 참조 하세요. 데코레이팅된 식별자의 길이에 영향을 줄 수 있는 요소는 다음과 같습니다.

- 식별자가 사용자 정의 형식의 개체 또는 사용자 정의 형식에서 파생된 형식을 나타내는지 여부

- 식별자가 함수 또는 함수에서 파생된 형식을 나타내는지 여부

- 함수에 사용되는 인수의 수

달러 기호는 `$` Microsoft c + + 컴파일러 (MSVC)의 유효한 식별자 문자입니다. 또한 MSVC를 사용 하면 식별자에서 허용 되는 유니버설 문자 이름 범위로 표시 된 실제 문자를 사용할 수 있습니다. 이러한 문자를 사용하려면 해당 문자를 포함하는 파일 인코딩 코드 페이지를 사용하여 파일을 저장해야 합니다.  이 예에서는 확장 문자와 유니버설 문자 이름을 코드에서 서로 바꿔 사용할 수 있는 방법을 보여 줍니다.

```cpp
// extended_identifier.cpp
// In Visual Studio, use File, Advanced Save Options to set
// the file encoding to Unicode codepage 1200
struct テスト         // Japanese 'test'
{
    void トスト() {}  // Japanese 'toast'
};

int main() {
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form
    パン.トスト();        // compiler recognizes UCN or literal form
}
```

식별자에서 허용되는 문자의 범위는 C++/CLI 코드를 컴파일하는 경우보다 덜 제한적입니다. /clr을 사용하여 컴파일된 코드의 식별자는  [Standard ECMA-335: Common Language Infrastructure(CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm)를 준수해야 합니다.

**Microsoft 전용 종료**

식별자의 첫 번째 문자는 영문자(대문자 또는 소문자) 또는 밑줄( **_** )이어야 합니다. C++ 식별자가 대/소문자를 구분하기 때문에 `fileName` 은 `FileName`과 다릅니다.

식별자는 키워드와 정확히 동일한 철자와 대/소문자를 사용할 수 없습니다. 키워드가 포함된 식별자를 사용할 수 있습니다. 예를 `Pint` 들어는 키워드인가 포함 되어 있어도 유효한 식별자입니다 **`int`** .

식별자에 두 개의 연속 밑줄 문자 ( **__** )를 사용 하거나 단일 선행 밑줄 뒤에 대문자를 사용 하는 경우 모든 범위에서 c + + 구현을 위해 예약 됩니다. 현재 또는 나중에 예약되는 식별자와 충돌할 수 있기 때문에 파일 범위가 있는 이름에 소문자가 뒤에 오는 단일 선행 밑줄을 사용하지 않도록 해야 합니다.

## <a name="see-also"></a>참고 항목

[어휘 규칙](../cpp/lexical-conventions.md)
