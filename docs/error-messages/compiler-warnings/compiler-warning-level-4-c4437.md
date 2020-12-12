---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4437'
title: 컴파일러 경고(수준 4) C4437
ms.date: 11/04/2016
f1_keywords:
- C4437
helpviewer_keywords:
- C4437
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 6ea94a972c08dfa6752c5c165a9c547419b03334
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251429"
---
# <a name="compiler-warning-level-4-c4437"></a>컴파일러 경고(수준 4) C4437

가상 기본 ' class1 '에서 ' class2 ' (으)로의 dynamic_cast은 (는)/vd2로 컴파일하거나 vtordisp (2) #pragma가 적용 된 ' class2 '를 정의 하는 일부 컨텍스트에서 실패할 수 있습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

컴파일러가 **`dynamic_cast`** 다음과 같은 특성을 가진 작업을 발견 했습니다.

- 캐스트는 기본 클래스 포인터에서 파생된 클래스 포인터의 방향으로 수행됩니다.

- 파생된 클래스는 기본 클래스를 상속합니다.

- 파생된 클래스에는 가상 기본에 대한 `vtordisp` 필드가 포함되지 않습니다.

- 파생 클래스의 생성자 또는 소멸자에 캐스팅이 없거나 파생 클래스에서 추가로 상속 되는 일부 클래스가 있습니다 (그렇지 않은 경우 컴파일러 경고 C4436가 실행 됨).

경고는가 **`dynamic_cast`** 부분적으로 생성 된 개체에서 작동 하는 경우 제대로 수행 되지 않을 수 있음을 나타냅니다.  이 상황은 경고에 명명 된 파생 클래스를 상속 하는 클래스의 소멸자 또는 생성자에서 바깥쪽 함수를 호출할 때 발생 합니다.  경고에 지정 된 파생 클래스가 더 이상 파생 되지 않거나 개체 생성 또는 소멸 중에 바깥쪽 함수를 호출 하지 않는 경우 경고를 무시할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4437를 생성 하 고 누락 된 필드에서 발생 하는 코드 생성 문제를 보여 줍니다 `vtordisp` .

```cpp
// C4437.cpp
// To see the warning and runtime assert, compile with: /W4
// To eliminate the warning and assert, compile with: /W4 /vd2
//       or compile with: /W4 /DFIX
#pragma warning(default : 4437)
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
        func();
    }

    void func()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4437
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
[컴파일러 경고 (수준 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)
