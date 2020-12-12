---
description: '자세한 정보: Lvalues 및 Rvalue (c + +)'
title: '값 범주: Lvalues 및 Rvalue (c + +)'
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: b92ddc3aad62f1eaf7af6a6bc113c1a0fdd70769
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299243"
---
# <a name="lvalues-and-rvalues-c"></a>Lvalue 및 Rvalue (C++)

모든 c + + 식에는 형식이 있으며 *값 범주* 에 속합니다. 값 범주는 식 평가 중에 임시 개체를 만들고 복사 하 고 이동할 때 컴파일러가 따라야 하는 규칙의 기본입니다.

C + + 17 표준은 식 값 범주를 다음과 같이 정의 합니다.

- 고 *값* 은 해당 평가에서 개체, 비트 필드 또는 함수의 id를 결정 하는 식입니다.
- *Prvalue* 는 해당 평가가 개체 또는 비트 필드를 초기화 하거나, 표시 되는 컨텍스트에 지정 된 대로 연산자의 피연산자 값을 계산 하는 식입니다.
- *Xvalue 값* 은 리소스를 다시 사용할 수 있는 개체 또는 비트 필드 (일반적으로 수명이 종료 되는 곳에 있기 때문)를 나타내는 고 값입니다. 예제: rvalue 참조 (8.3.2)를 포함 하는 특정 종류의 식은 반환 형식이 rvalue 참조 이거나 rvalue 참조 형식으로 캐스팅 되는 함수에 대 한 호출과 같이 xvalues을 생성 합니다.
- *Lvalue* 는 xvalue 값가 아닌 잘못 된 값입니다.
- *Rvalue* 는 prvalue 또는 xvalue 값입니다.

다음 다이어그램에서는 범주 간의 관계를 보여 줍니다.

![C + + 식 값 범주](media/value_categories.png "C + + 식 값 범주")

Lvalue에는 프로그램에서 액세스할 수 있는 주소가 있습니다. Lvalue 식의 예로는 변수 **`const`** , 배열 요소, lvalue 참조, 비트 필드, 공용 구조체 및 클래스 멤버를 반환 하는 함수 호출을 포함 한 변수 이름이 있습니다.

Prvalue 식에는 프로그램에서 액세스할 수 있는 주소가 없습니다. Prvalue 식의 예로는 리터럴, 참조 하지 않는 형식을 반환 하는 함수 호출, 식 평가 중에 생성 되었지만 컴파일러 에서만 액세스할 수 있는 임시 개체 등이 있습니다.

Xvalue 값 식에는 프로그램에서 더 이상 액세스할 수 없지만 식에 대 한 액세스를 제공 하는 rvalue 참조를 초기화 하는 데 사용할 수 있는 주소가 있습니다. 예제에는 rvalue 참조를 반환 하는 함수 호출 및 배열이 나 개체가 rvalue 참조 인 멤버 식에 대 한 배열 첨자, 멤버 및 포인터가 포함 됩니다.

## <a name="example"></a>예제

다음 예제에서는 lvalue 및 rvalue에 대한 여러 가지 올바른 사용과 올바르지 않은 사용의 예를 보여 줍니다.

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;

    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> 이 항목의 예제는 연산자가 오버로드되지 않을 때 올바른 사용과 올바르지 않은 사용의 예를 보여 줍니다. 연산자를 오버로드하여 `j * 4`와 같은 식을 lvalue로 만들 수 있습니다.

*Lvalue* 및 *rvalue* 용어는 개체 참조를 참조 하는 경우에 자주 사용 됩니다. 참조에 대 한 자세한 내용은 [Lvalue 참조 선언 자: &](../cpp/lvalue-reference-declarator-amp.md) 및 [Rvalue 참조 선언 자:  &&](../cpp/rvalue-reference-declarator-amp-amp.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[기본 개념](../cpp/basic-concepts-cpp.md)<br/>
[Lvalue 참조 선언자: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Rvalue 참조 선언자: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
