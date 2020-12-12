---
description: '자세한 정보: void (c + +)'
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: e49dfa03e289cdbace50a24cf6854d25c51b3426
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213353"
---
# <a name="void-c"></a>void (C++)

함수 반환 형식으로 사용 하는 경우 **`void`** 키워드는 함수가 값을 반환 하지 않도록 지정 합니다. 함수 매개 변수 목록에 사용 되는 경우 **`void`** 함수에서 매개 변수를 사용 하지 않도록 지정 합니다. 포인터 선언에 사용 될 때 **`void`** 포인터가 "universal" 임을 지정 합니다.

포인터 형식이 void _ 인 경우 **\* 포인터는 _ `const` 또는 키워드로 *선언 되지 않은 모든 변수를 가리킬 수 있습니다*** **`volatile`** . **Void \** _ 포인터는 다른 형식으로 캐스팅 된 경우에만 역참조 될 수 있습니다. _*Void \**_ 포인터는 다른 형식의 데이터 포인터로 변환 될 수 있습니다.

_ *`void`* * 포인터는 함수를 가리킬 수 있지만 c + +의 클래스 멤버가 될 수 없습니다.

형식의 변수는 선언할 수 없습니다 **`void`** .

## <a name="example"></a>예제

```cpp
// void.cpp
void vobject;   // C2182
void *pv;   // okay
int *pint; int i;
int main() {
   pv = &i;
   // Cast optional in C required in C++
   pint = (int *)pv;
}
```

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)<br/>
[기본 제공 형식](../cpp/fundamental-types-cpp.md)
