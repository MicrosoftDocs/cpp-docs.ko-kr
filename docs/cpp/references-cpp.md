---
description: '자세한 정보: 참조 (c + +)'
title: 참조 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
ms.openlocfilehash: 1f49e089d8992a32f30e1a384d5f0c36fa327c0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250051"
---
# <a name="references-c"></a>참조 (C++)

참조는 포인터와 마찬가지로, 메모리의 다른 위치에 있는 개체의 주소를 저장합니다. 하지만 포인터와는 달리, 참조는 초기화되고 나면 다른 개체를 참조하도록 설정하거나 null로 설정할 수 없습니다. 참조에는 두 가지 종류가 있습니다. lvalue 참조는 명명 된 변수를 참조 하 고 rvalue 참조는 [임시 개체](../cpp/temporary-objects.md)를 참조 합니다. & 연산자는 lvalue 참조를 나타내며 && 연산자는 rvalue 참조 또는 컨텍스트에 따라 일반 참조 (rvalue 또는 lvalue)를 나타냅니다.

참조를 선언할 수 있는 구문은 다음과 같습니다.

> \[*저장소 클래스 지정자*] \[ *cv 한정자*] *형식-지정자* \[ *ms-modifier*] *선언 자* \[ **=** *식*]**;**

참조를 지정하는 임의의 유효한 선언자를 사용할 수 있습니다. 참조가 함수 또는 배열 형식에 대한 참조가 아닌 한 다음 단순화된 구문이 적용됩니다.

> \[*저장소 클래스 지정자*] \[ *cv 한정자*] *형식 지정자* \[ **&** 또는 **&&** ] \[ *cv-한정자*] *식별자* \[ **=** *식*]**;**

참조를 선언하는 시퀀스는 다음과 같습니다.

1. 선언 지정자:

   - 선택적 스토리지 클래스 지정자.

   - 선택적 **`const`** 및/또는 **`volatile`** 한정자입니다.

   - 형식 지정자: 형식의 이름

1. 선언자:

   - 선택적 Microsoft 전용 한정자. 자세한 내용은 [Microsoft 전용 한정자](../cpp/microsoft-specific-modifiers.md)를 참조 하세요.

   - **&** 연산자 또는 **&&** 연산자입니다.

   - 선택 사항 **`const`** 및/또는 **`volatile`** 한정자.

   - 식별자입니다.

1. 선택적 이니셜라이저입니다.

배열 및 함수에 대 한 포인터의 더 복잡 한 선언 자 형식은 배열 및 함수에 대 한 참조에도 적용 됩니다. 자세한 내용은 [포인터](../cpp/pointers-cpp.md)를 참조 하세요.

여러 선언자와 이니셜라이저가 단일 선언 지정자 뒤에 쉼표로 구분된 목록으로 나타날 수 있습니다. 예를 들어:

```cpp
int &i;
int &i, &j;
```

참조, 포인터 및 개체를 함께 선언할 수 있습니다.

```cpp
int &ref, *ptr, k;
```

참조는 개체의 주소를 보유하지만 구문적으로 개체처럼 동작합니다.

다음 프로그램에서 개체 이름인 `s`와 개체에 대한 참조인 `SRef`를 프로그램에서 동일하게 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// references.cpp
#include <stdio.h>
struct S {
   short i;
};

int main() {
   S  s;   // Declare the object.
   S& SRef = s;   // Declare the reference.
   s.i = 3;

   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);

   SRef.i = 4;
   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);
}
```

```Output
3
3
4
4
```

## <a name="see-also"></a>참고 항목

[참조 형식 함수 인수](../cpp/reference-type-function-arguments.md)<br/>
[참조 형식 함수 반환](../cpp/reference-type-function-returns.md)<br/>
[포인터에 대 한 참조](../cpp/references-to-pointers.md)
