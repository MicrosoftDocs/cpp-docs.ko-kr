---
description: '자세히 알아보기: 상속 (c + +)'
title: 상속(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: d3007b8e12d6ba695a8a3e6604270a65f1118bb2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113898"
---
# <a name="inheritance--c"></a>상속(C++)

이 단원에서는 파생 클래스를 사용하여 확장 가능한 프로그램을 생성하는 방법을 설명합니다.

## <a name="overview"></a>개요

새 클래스는 "상속" 이라는 메커니즘을 사용 하 여 기존 클래스에서 파생 될 수 있습니다 ( [단일 상속](../cpp/single-inheritance.md)으로 시작 되는 정보 참조). 파생에 사용되는 클래스를 특정 파생 클래스의 "기본 클래스"라고 합니다. 파생 클래스는 다음 구문을 사용하여 선언됩니다.

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

클래스에 대한 태그(이름) 뒤에 콜론과 기본 사양 목록이 나타납니다.  그렇게 명명된 기본 클래스는 이전에 선언되어 있어야 합니다.  기본 사양에는 키워드 또는의 하나에 해당 하는 액세스 지정 자가 포함 될 수 있습니다 **`public`** **`protected`** **`private`** .  이러한 액세스 지정자는 기본 클래스 이름 앞에 나타나고 해당 기본 클래스에만 적용됩니다.  이러한 지정자는 기본 클래스의 멤버를 사용할 수 있는 파생 클래스의 권한을 제어합니다.  기본 클래스 멤버 액세스에 대 한 자세한 내용은 [멤버 Access Control](../cpp/member-access-control-cpp.md) 를 참조 하세요.  액세스 지정자를 생략 하면 해당 기준에 대 한 액세스를 고려 **`private`** 합니다.  기본 사양에는 **`virtual`** 가상 상속을 나타내는 키워드가 포함 될 수 있습니다.  이 키워드는 액세스 지정자(있는 경우) 앞이나 뒤에 나타날 수 있습니다.  가상 상속을 사용하는 경우 기본 클래스를 가상 기본 클래스라고 합니다.

여러 기본 클래스를 쉼표로 구분하여 지정할 수 있습니다.  단일 기본 클래스를 지정 하는 경우 상속 모델은 [단일 상속](../cpp/single-inheritance.md)입니다. 둘 이상의 기본 클래스를 지정 하는 경우 상속 모델을 [다중 상속](../cpp/multiple-base-classes.md)이라고 합니다.

다음 항목이 포함됩니다.

- [단일 상속](../cpp/single-inheritance.md)

- [다중 기본 클래스](../cpp/multiple-base-classes.md)

- [가상 함수](../cpp/virtual-functions.md)

- [명시적 재정의](../cpp/explicit-overrides-cpp.md)

- [추상 클래스](../cpp/abstract-classes-cpp.md)

- [범위 규칙의 요약](../cpp/summary-of-scope-rules.md)

[__Super](../cpp/super.md) 및 [__interface](../cpp/interface.md) 키워드는이 섹션에 설명 되어 있습니다.

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)
