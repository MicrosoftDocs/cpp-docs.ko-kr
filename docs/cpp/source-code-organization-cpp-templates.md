---
description: '자세한 정보: 소스 코드 조직 (c + + 템플릿)'
title: 소스 코드 조직(C++ 템플릿)
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: 72777c550cf36fd635432a8ce840af92f0a3f893
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113872"
---
# <a name="source-code-organization-c-templates"></a>소스 코드 조직(C++ 템플릿)

클래스 템플릿을 정의할 때 멤버 정의가 컴파일러에 필요할 경우 표시되도록 소스 코드를 구성해야 합니다. 포함 모델이나 명시적 인스턴스화 모델을 사용할 수 있습니다. 포함 모델에서 템플릿을 사용 하는 모든 파일에 멤버 정의를 포함 합니다. 이 방식은 가장 단순하며 템플릿에 구체적인 형식을 사용할 수 있다는 면에서 가장 유연합니다. 단점은 컴파일 시간이 늘어날 수 있는 것입니다. 프로젝트나 포함된 파일 자체가 큰 경우 상당한 영향을 미칠 수 있습니다. 명시적 인스턴스화 방식을 사용하면 템플릿 자체에서 구체적인 클래스 또는 클래스 멤버를 특정 형식에 맞게 인스턴스화합니다.  이 방식은 컴파일 시간을 단축할 수 있지만, 템플릿 구현자를 미리 사용하도록 설정한 클래스에만 사용할 수 있습니다. 일반적으로 컴파일 시간이 문제가 되는 경우를 제외하고는 포함 모델을 사용하는 것이 좋습니다.

## <a name="background"></a>배경

템플릿은 컴파일러에서 템플릿 또는 해당 멤버의 개체 코드를 생성하지 않는다는 점에서 일반 클래스와 다릅니다. 템플릿이 구체적인 형식으로 인스턴스화되기 전까지는 생성하는 항목이 없습니다. 컴파일러에서 `MyClass<int> mc;`과 같은 템플릿 인스턴스화가 발생하는 데 해당 시그니처가 있는 클래스가 아직 없으면 새 클래스를 생성합니다. 또한 사용되는 멤버 함수의 코드를 생성하려고 합니다. 이러한 정의가 컴파일되는 .cpp 파일에 직접 또는 간접적으로 #포함되지 않은 파일에 있는 경우 컴파일러에서 이러한 정의를 볼 수 없습니다.  컴파일러의 관점에서는 이 경우에도 함수가 다른 변환 단위에 정의될 수 있고, 그러면 링커에서 함수를 찾으므로 오류가 발생하지는 않습니다.  링커가 해당 코드를 찾지 못하면 *해결되지 않은 외부* 오류가 발생합니다.

## <a name="the-inclusion-model"></a>포함 모델

템플릿 정의를 변환 단위 전체에 표시하도록 설정하는 가장 일반적이고 간단한 방법은 헤더 파일 자체에 정의를 넣는 것입니다.  템플릿을 사용하는 모든 .cpp 파일에 헤더를 #포함하면 됩니다. 이것이 표준 라이브러리에서 사용되는 방식입니다.

```cpp
#ifndef MYARRAY
#define MYARRAY
#include <iostream>

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    // Full definitions:
    MyArray(){}
    void Print()
    {
        for (const auto v : arr)
        {
            std::cout << v << " , ";
        }
    }

    T& operator[](int i)
   {
       return arr[i];
   }
};
#endif
```

이 접근 방식을 사용 하는 경우 컴파일러는 전체 템플릿 정의에 대 한 액세스 권한을 가지 며 모든 형식에 대해 요청 시 템플릿을 인스턴스화할 수 있습니다. 이 방식은 간단하고 비교적으로 유지 관리하기 쉽습니다. 그러나 포함 모델은 컴파일 시간이 길다는 단점이 있습니다. 큰 프로그램에서, 특히 템플릿 헤더 자체에 다른 헤더가 #포함된 경우 이 단점이 상당할 수 있습니다. *`.cpp`* 헤더를 #includes 하는 모든 파일은 자체 함수 템플릿 및 모든 정의의 복사본을 가져옵니다. 링커에서 일반적으로 항목을 정렬할 수 있으므로 함수의 정의가 여럿이 되지는 않지만 이 작업을 하는 데 시간이 걸립니다. 작은 프로그램에서는 이런 추가 컴파일 시간이 길지 않을 수 있습니다.

## <a name="the-explicit-instantiation-model"></a>명시적 인스턴스화 모델

프로젝트에 대 한 포함 모델을 사용할 수 없는 경우 템플릿 인스턴스화에 사용할 형식 집합을 알고 있는 경우 템플릿 코드를 *`.h`* 및 파일로 분리 하 *`.cpp`* 고, *`.cpp`* 파일에서 템플릿을 명시적으로 인스턴스화할 수 있습니다. 이렇게 하면 컴파일러에서 사용자 인스턴스를 발견할 때 표시할 개체 코드가 생성됩니다.

키워드 템플릿 다음에 인스턴스화할 엔터티의 시그니처를 사용하여 명시적 인스턴스화를 작성합니다. 이 엔터티는 형식 또는 멤버일 수 있습니다. 형식을 명시적으로 인스턴스화하는 경우 모든 멤버가 인스턴스화됩니다.

```cpp
template MyArray<double, 5>;
```

```cpp
//MyArray.h
#ifndef MYARRAY
#define MYARRAY

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    MyArray();
    void Print();
    T& operator[](int i);
};
#endif

//MyArray.cpp
#include <iostream>
#include "MyArray.h"

using namespace std;

template<typename T, size_t N>
MyArray<T,N>::MyArray(){}

template<typename T, size_t N>
void MyArray<T,N>::Print()
{
    for (const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

앞의 예에서 명시적 인스턴스는 .cpp 파일의 맨 아래에 있습니다. 는 `MyArray` 또는 형식에만 사용할 수 있습니다 **`double`** `String` .

> [!NOTE]
> C + + 11에서 **`export`** 키워드는 템플릿 정의의 컨텍스트에서 사용 되지 않습니다. 대부분의 컴파일러에서 이 키워드를 지원하지 않았으므로 실제로 영향은 거의 없습니다.
