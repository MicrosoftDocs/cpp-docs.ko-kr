---
title: 컴파일러 경고 (수준 4) C4437 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748ba39d9c22a4071307b8df075eab233f3cfbb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4437"></a>컴파일러 경고(수준 4) C4437
가상 기본 'class1'에서 'class2' 사이의 dynamic_cast 일부 컨텍스트에서 실패할 컴파일/v d 2 하거나 적용 'class2' #pragma vtordisp(2)로 정의할 수 없습니다.  
  
 기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.  
  
 컴파일러에서 다음과 같은 특성의 `dynamic_cast` 작업이 발견되었습니다.  
  
-   캐스트는 기본 클래스 포인터에서 파생된 클래스 포인터의 방향으로 수행됩니다.  
  
-   파생된 클래스는 기본 클래스를 상속합니다.  
  
-   파생된 클래스에는 가상 기본에 대한 `vtordisp` 필드가 포함되지 않습니다.  
  
-   캐스팅 생성자 또는 파생된 된 클래스의 소멸자에 없는 또는 추가 하는 일부 클래스 (그렇지 컴파일러 경고 C4436 발생 하는) 파생된 클래스에서 상속 합니다.  
  
 이 경고는 나타냅니다는 `dynamic_cast` 부분적으로 생성 된 개체에서 작동 하는 경우 올바르게 성능이 떨어질 수 있습니다.  이 상황은 생성자 또는 경고에 지정 하는 파생된 클래스를 상속 하는 클래스의 소멸자에서 바깥쪽 함수를 호출할 때 발생 합니다.  경고에 지정 하는 파생된 클래스를 더 이상 파생 된를 또는 바깥쪽 함수의 개체 생성 이나 소멸 중 호출 하지 않으면 경고를 무시할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 샘플 C4437를 생성 하 고 누락 된에서 발생 하는 코드 생성 문제를 보여 줍니다. `vtordisp` 필드입니다.  
  
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
 [dynamic_cast 연산자](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [컴파일러 경고(수준 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)