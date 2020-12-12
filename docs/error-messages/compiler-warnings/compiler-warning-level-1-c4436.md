---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4436'
title: 컴파일러 경고(수준 1) C4436
ms.date: 11/04/2016
f1_keywords:
- C4436
helpviewer_keywords:
- C4436
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: 78d6ab1d6b80c06448b6dfdd8401cb9fd2d76b02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212599"
---
# <a name="compiler-warning-level-1-c4436"></a>컴파일러 경고(수준 1) C4436

생성자 또는 소멸자에서 가상 기본 'class1'에서 'class2'로의 dynamic_cast는 부분적으로 생성된 개체와 함께 실패할 수 있습니다.        /vd2를 사용해서 컴파일하거나 해당 #pragma vtordisp(2)에 'class2'를 정의하십시오.

컴파일러가 **`dynamic_cast`** 다음과 같은 특성을 가진 작업을 발견 했습니다.

- 캐스트는 기본 클래스 포인터에서 파생된 클래스 포인터의 방향으로 수행됩니다.

- 파생된 클래스는 기본 클래스를 상속합니다.

- 파생된 클래스에는 가상 기본에 대한 `vtordisp` 필드가 포함되지 않습니다.

- 파생된 클래스 또는 파생 클래스에서 추가로 상속되는 일부 다른 클래스의 생성자 또는 소멸자에서 클래스가 발견되었습니다.

경고는가 **`dynamic_cast`** 부분적으로 생성 된 개체에서 작동 하는 경우 제대로 수행 되지 않을 수 있음을 나타냅니다.  이 경우는 파생된 생성자/소멸자가 추가로 파생된 일부 개체의 하위 개체에서 작동하는 경우에 발생합니다.  경고에 지정된 파생된 클래스가 더 이상 파생되지 않을 경우 경고를 무시해도 됩니다.

## <a name="example"></a>예제

다음 샘플은 C4436을 생성하고 누락된 `vtordisp` 필드로부터 발생하는 코드 생성 문제를 보여줍니다.

```cpp
// C4436.cpp
// To see the warning and runtime assert, compile with: /W1
// To eliminate the warning and assert, compile with: /W1 /vd2
//       or compile with: /W1 /DFIX
#include <cassert>

struct A
{
public:
    virtual ~A() {}
};

#if defined(FIX)
#pragma vtordisp(push, 2)
#endif
struct B : virtual A
{
    B()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4436
        assert(this == b);              // assert unless compiled with /vd2
    }
};
#if defined(FIX)
#pragma vtordisp(pop)
#endif

struct C : B
{
    int i;
};

int main()
{
    C c;
}
```

## <a name="see-also"></a>참고 항목

[dynamic_cast 연산자](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[컴파일러 경고 (수준 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)
