---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: d0092cf107159f4c84b431f5eeae130df64dc835
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507457"
---
# <a name="struct-c"></a>struct (C++)

키워드는 구조체 형식 **`struct`** 및/또는 구조체 형식의 변수를 정의 합니다.

## <a name="syntax"></a>구문

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>매개 변수

*템플릿-사양*<br/>
선택적 템플릿 지정입니다. 자세한 내용은 [템플릿 사양](templates-cpp.md)을 참조 하세요.

*struct*<br/>
**`struct`** 키워드입니다.

*ms decl-사양*<br/>
선택적 스토리지 클래스 지정입니다. 자세한 내용은 [__declspec](../cpp/declspec.md) 키워드를 참조 하세요.

*태그가*<br/>
구조체에 지정된 형식 이름입니다. 태그는 구조체의 범위 내에서 예약어가 됩니다. 태그는 선택 사항입니다. 생략할 경우 익명 구조체가 정의됩니다. 자세한 내용은 [익명 클래스 형식](../cpp/anonymous-class-types.md)을 참조 하세요.

*base-list*<br/>
이 구조체가 해당 멤버를 파생할 클래스 또는 구조체의 선택적 목록입니다. 자세한 내용은 [기본 클래스](../cpp/base-classes.md) 를 참조 하세요. 각 기본 클래스 또는 구조체 이름 앞에는 액세스 지정자 ([public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md)) 및 [virtual](../cpp/virtual-cpp.md) 키워드가 올 수 있습니다. 자세한 내용은 [클래스 멤버에 대 한 액세스 제어](member-access-control-cpp.md) 의 멤버 액세스 테이블을 참조 하세요.

*멤버 목록*<br/>
구조체 멤버 목록입니다. 자세한 내용은 [클래스 멤버 개요](../cpp/class-member-overview.md) 를 참조 하세요. 여기서는를 대신 사용 한다는 점만 다릅니다 **`struct`** **`class`** .

*declarators*<br/>
구조체의 이름을 지정 하는 선언 자 목록입니다. 선언자 목록은 구조체 형식의 하나 이상의 인스턴스를 선언합니다. 구조체의 모든 데이터 멤버가 인 경우 선언 자는 이니셜라이저 목록을 포함할 수 있습니다 **`public`** . 이니셜라이저 목록은 기본적으로 데이터 멤버가 이기 때문에 구조에서 일반적 **`public`** 입니다.  자세한 내용은 [선언 자 개요](./declarations-and-definitions-cpp.md) 를 참조 하세요.

## <a name="remarks"></a>설명

구조체 형식은 사용자 정의 복합 형식입니다. 이 형식은 다른 형식을 가질 수 있는 필드 또는 멤버로 구성됩니다.

C + +에서 구조체는 클래스와 동일 합니다. 단, 해당 멤버는 **`public`** 기본적으로입니다.

C + +/CLI의 관리 되는 클래스 및 구조체에 대 한 자세한 내용은 [클래스 및 구조체](../extensions/classes-and-structs-cpp-component-extensions.md)를 참조 하세요.

## <a name="using-a-structure"></a>구조체 사용

C에서는 키워드를 명시적으로 사용 하 여 구조체를 선언 해야 합니다 **`struct`** . C + +에서는 **`struct`** 형식을 정의한 후 키워드를 사용할 필요가 없습니다.

닫는 중괄호와 세미콜론 사이에 쉼표로 구분된 변수 이름을 하나 이상 넣어 구조체 형식이 정의될 때 변수를 선언하는 옵션이 있습니다.

구조체 변수를 초기화할 수 있습니다. 각 변수의 초기화는 중괄호로 묶어야 합니다.

관련 내용은 [클래스](../cpp/class-cpp.md), [공용 구조체](../cpp/unions.md)및 [열거형](../cpp/enumerations-cpp.md)을 참조 하세요.

## <a name="example"></a>예제

```cpp
#include <iostream>
using namespace std;

struct PERSON {   // Declare PERSON struct type
    int age;   // Declare member types
    long ss;
    float weight;
    char name[25];
} family_member;   // Define object of type PERSON

struct CELL {   // Declare CELL bit field
    unsigned short character  : 8;  // 00000000 ????????
    unsigned short foreground : 3;  // 00000??? 00000000
    unsigned short intensity  : 1;  // 0000?000 00000000
    unsigned short background : 3;  // 0???0000 00000000
    unsigned short blink      : 1;  // ?0000000 00000000
} screen[25][80];       // Array of bit fields

int main() {
    struct PERSON sister;   // C style structure declaration
    PERSON brother;   // C++ style structure declaration
    sister.age = 13;   // assign values to members
    brother.age = 7;
    cout << "sister.age = " << sister.age << '\n';
    cout << "brother.age = " << brother.age << '\n';

    CELL my_cell;
    my_cell.character = 1;
    cout << "my_cell.character = " << my_cell.character;
}
// Output:
// sister.age = 13
// brother.age = 7
// my_cell.character = 1
```
