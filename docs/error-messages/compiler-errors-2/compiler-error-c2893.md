---
description: '자세한 정보: 컴파일러 오류 C2893'
title: 컴파일러 오류 C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: 42e31327096a539feeb691c698b52f57ecb615a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278261"
---
# <a name="compiler-error-c2893"></a>컴파일러 오류 C2893

' Template name ' 함수 템플릿을 특수화 하지 못했습니다.

컴파일러가 함수 템플릿을 특수화 하지 못했습니다. 이 오류의 원인은 여러 가지가 있을 수 있습니다.

일반적으로 C2893 오류를 해결 하는 방법은 함수의 시그니처를 검토 하 고 모든 형식을 인스턴스화할 수 있는지 확인 하는 것입니다.

## <a name="example"></a>예제

C2893 `f` 는의 템플릿 매개 변수가로 `T` 추론 `std::map<int,int>` 되었지만 `std::map<int,int>` (를 사용 하 `data_type` `T::data_type` 여 인스턴스화할 수 없음 `T = std::map<int,int>` ) 멤버를 포함 하지 않기 때문에 발생 합니다. 다음 샘플에서는 C2893를 생성 합니다.

```cpp
// C2893.cpp
// compile with: /c /EHsc
#include<map>
using namespace std;
class MyClass {};

template<class T>
inline typename T::data_type
// try the following line instead
// inline typename  T::mapped_type
f(T const& p1, MyClass const& p2);

template<class T>
void bar(T const& p1) {
    MyClass r;
    f(p1,r);   // C2893
}

int main() {
   map<int,int> m;
   bar(m);
}
```
