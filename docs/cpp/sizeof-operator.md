---
title: sizeof 연산자
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: bc1165cf1df3933575013906d1b24673467f0b36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178719"
---
# <a name="sizeof-operator"></a>sizeof 연산자

**Char**형식의 크기를 기준으로 해당 피연산자의 크기를 생성 합니다.

> [!NOTE]
>  `sizeof ...` 연산자에 대 한 자세한 내용은 [줄임표 및 Variadic 템플릿](../cpp/ellipses-and-variadic-templates.md)을 참조 하세요.

## <a name="syntax"></a>구문

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>주의

**Sizeof** 연산자의 결과는 `size_t`형식이 며, 포함 파일 \<stddef >에 정의 된 정수 계열 형식입니다. 이 연산자를 사용하면 프로그램에서 컴퓨터 종속 데이터 크기를 지정하지 않아도 됩니다.

**Sizeof** 의 피연산자는 다음 중 하나일 수 있습니다.

- 형식 이름. 형식 이름으로 **sizeof** 를 사용 하려면 이름을 괄호로 묶어야 합니다.

- 식입니다. 식과 함께 사용 하는 경우에는 괄호를 사용 하거나 사용 하지 않고 **sizeof** 를 지정할 수 있습니다. 식은 계산되지 않습니다.

**Sizeof** 연산자가 **char**형식의 개체에 적용 되 면 1이 생성 됩니다. **Sizeof** 연산자가 배열에 적용 되 면 배열 식별자가 나타내는 포인터의 크기가 아니라 해당 배열의 총 바이트 수가 생성 됩니다. 배열 식별자가 나타내는 포인터의 크기를 가져오려면 **sizeof**를 사용 하는 함수에 매개 변수로 전달 합니다. 예를 들면 다음과 같습니다.

## <a name="example"></a>예제

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>샘플 출력

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

**Sizeof** 연산자가 **클래스**, **구조체**또는 **공용 구조체** 형식에 적용 되는 경우 결과는 해당 형식의 개체에 있는 바이트 수와 단어 경계의 멤버를 맞추기 위해 추가 된 안쪽 여백을 포함 합니다. 결과는 개별 멤버의 스토리지 요구 사항을 추가하여 계산된 크기와 일치하지 않을 수도 있습니다. [/Zp](../build/reference/zp-struct-member-alignment.md) 컴파일러 옵션과 [pack](../preprocessor/pack.md) pragma는 멤버의 맞춤 경계에 영향을 줍니다.

**Sizeof** 연산자는 빈 클래스의 경우에도 0을 생성 하지 않습니다.

**Sizeof** 연산자는 다음 피연산자와 함께 사용할 수 없습니다.

- 함수 그러나 **sizeof** 는 함수에 대 한 포인터에 적용 될 수 있습니다.

- 비트 필드

- 정의되지 않은 클래스

- **Void**형식입니다.

- 동적으로 할당된 배열

- 외부 배열

- 불완전한 형식

- 괄호로 묶인 불완전한 형식의 이름

**Sizeof** 연산자가 참조에 적용 되는 경우에는 **sizeof** 가 개체 자체에 적용 된 것과 결과가 같습니다.

크기 배열 배열이 구조체의 마지막 요소인 경우 **sizeof** 연산자는 배열이 없는 구조체의 크기를 반환 합니다.

**Sizeof** 연산자는 다음 형식의 식을 사용 하 여 배열의 요소 수를 계산 하는 데 주로 사용 됩니다.

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>참고 항목

[단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)<br/>
[키워드](../cpp/keywords-cpp.md)
