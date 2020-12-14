---
description: '자세한 정보: final 지정자'
title: final 지정자
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: 5fd6ee3c23a455c4316593cc089c26c34477709d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242615"
---
# <a name="final-specifier"></a>final 지정자

**Final** 키워드를 사용 하 여 파생 클래스에서 재정의할 수 없는 가상 함수를 지정할 수 있습니다. 상속할 수 없는 클래스를 지정하기 위해 해당 키워드를 사용할 수도 있습니다.

## <a name="syntax"></a>구문

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>설명

**final** 은 컨텍스트를 구분 하며 함수 선언 또는 클래스 이름 다음에 사용 되는 경우에만 특별 한 의미가 있습니다. 그렇지 않으면 예약 된 키워드가 아닙니다.

**Final** 이 클래스 선언에 사용 되는 경우 `base-classes` 는 선언의 선택적 부분입니다.

## <a name="example"></a>예제

다음 예에서는 **final** 키워드를 사용 하 여 가상 함수를 재정의할 수 없도록 지정 합니다.

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

멤버 함수를 재정의할 수 있도록 지정 하는 방법에 대 한 자세한 내용은 [Override 지정자](../cpp/override-specifier.md)를 참조 하세요.

다음 예제에서는 **final** 키워드를 사용 하 여 클래스를 상속할 수 없도록 지정 합니다.

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)<br/>
[override 지정자](../cpp/override-specifier.md)
