---
title: constexpr (c + +) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- constexpr_cpp
dev_langs:
- C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf1094be23074fe71e65a3077de51263f01a81c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-c"></a>constexpr(C++)
`constexpr` 키워드는 C++11에서 도입되고 C++14에서 향상되었습니다. 의미 *상수 식*합니다. `const`와 마찬가지로, 코드에서 값을 수정하려고 하면 컴파일러 오류가 발생하도록 변수에 적용할 수 있습니다. `const`와 달리, `constexpr`은 함수 및 클래스 생성자에도 적용할 수 있습니다. `constexpr`은 값 또는 반환 값이 상수이고 가능한 경우 컴파일 타임에 계산됨을 나타냅니다.  템플릿 인수 및 배열 선언과 같이 const 정수가 필요한 곳마다 `constexpr` 정수 계열 값을 사용할 수 있습니다. 고 런타임 대신 컴파일 타임에 값을 계산할 수 있는 때 더 빠르게 실행 하 고 더 적은 메모리를 사용 하 여 프로그램 지원할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `params`  
 리터럴 형식(아래 참조)이어야 하며 그 자체가 상수 식이어야 하는 하나 이상의 매개 변수입니다.  
  
## <a name="return-value"></a>반환 값  
 constexpr 변수 또는 함수는 아래와 같은 리터럴 형식 중 하나를 반환해야 합니다.  
  
## <a name="literal-types"></a>리터럴 형식  
 컴퓨팅 컴파일 타임 상수의 복잡성 및 컴파일 타임에 대한 잠재적 영향을 제한하기 위해 C++14 표준에서는 상수 식에 관련된 형식이 리터럴 형식으로 제한되어야 합니다. 리터럴 형식은 컴파일 타임에 해당 레이아웃이 결정될 수 있는 형식입니다. 다음은 리터럴 형식입니다.  
  
1.  void  
  
2.  스칼라 형식  
  
3.  참조  
  
4.  void, 스칼라 형식 또는 참조의 배열  
  
5.  trivial 소멸자 및 이동 또는 복사 생성자가 아닌 constexpr 생성자를 하나 이상 포함하는 클래스입니다. 또한 해당 비정적 데이터 멤버 및 기본 클래스가 모두 리터럴 형식이고 volatile이 아니어야 합니다.  
  
## <a name="constexpr-variables"></a>constexpr 변수  
 const 및 constexpr 변수 간의 주요 차이점은 const 변수의 초기화는 런타임까지 지연시킬 수 있는 반면 constexpr 변수는 컴파일 타임에 초기화해야 한다는 것입니다.  모든 constexpr 변수는 상수입니다.  

-  변수가 리터럴 형식이고 초기화된 경우 `constexpr`을 사용하여 변수를 선언할 수 있습니다. 생성자가 초기화를 수행하는 경우 생성자를 `constexpr`로 선언해야 합니다.  
  
-   참조하는 개체가 상수 식으로 초기화되고 초기화 중에 호출되는 암시적 변환도 모두 상수 식인 경우 참조를 constexpr로 선언할 수 있습니다.  
  
-   `constexpr` 변수 또는 함수의 모든 선언에 `constexpr` 지정자가 있어야 합니다.  
  
 
  
 
  
```cpp  
constexpr float x = 42.0;  
constexpr float y{108};  
constexpr float z = exp(5, 3);  
constexpr int i; // Error! Not initialized  
int j = 0;  
constexpr int k = j + 1; //Error! j not a constant expression  
```  
  
## <a name="constexpr-functions"></a>constexpr 함수  
 `constexpr` 함수는 사용하는 코드에 필요한 경우 컴파일 시 반환 값을 계산할 수 있는 함수입니다.  해당 인수가 `constexpr` 값이고, `constexpr` 변수 초기화나 비형식 템플릿 인수 제공 등을 위해 사용하는 코드에서 컴파일 타임에 반환 값을 요구하는 경우 컴파일 타임 상수를 생성합니다. `constexpr` 이외의 인수를 사용하여 호출하거나 컴파일 타임에 해당 값이 필요하지 않은 경우 일반 함수처럼 런타임에 값을 생성합니다.  이 이중 동작 덕분에 동일한 함수의 `constexpr` 버전과 `constexpr` 이외 버전을 작성하지 않아도 됩니다.  
 
 `constexpr` 함수 또는 생성자는 암시적으로 `inline`입니다. 
 
 Constexpr 함수에는 다음 규칙이 적용 됩니다.

- `constexpr` 함수는 리터럴 형식만 사용하고 반환해야 합니다. 

- `constexpr` 함수는 재귀적일 수 있습니다. 

- 않아야 [가상](../cpp/virtual-cpp.md)합니다. A 바깥쪽 클래스에 있는 경우 가상 기본 클래스 생성자를 constexpr로 정의할 수 없습니다.

- 본문은 `= default` 또는 `= delete`로 정의할 수 있습니다. 

- 본문에는 no 포함 될 수 있습니다 `goto` 문이나 try 블록입니다. 

- constexpr 이외 템플릿의 명시적 특수화를 `constexpr`로 선언할 수 있습니다.  
  
- `constexpr` 템플릿의 명시적 특수화는 `constexpr`이 아니어도 됩니다. 


<!--conformance note-->
Visual Studio 2017 이상 constexpr 함수에 다음 규칙이 적용 됩니다. 

- 수 포함 하는 경우 및 문과 범위 기반 for, while,을 포함 하 여 모든 반복 문을 전환 및 수행-동안
    
- 지역 변수 선언을 포함 될 수 있지만 변수 초기화는 리터럴 형식 이어야 하 고 정적 또는 스레드 로컬이 될 수 없습니다. 로컬로 선언 된 변수는 const 일 필요가 없습니다 하며 변경할 수 있습니다.

- Constexpr 비정적 멤버 함수는 암시적으로 const 일 필요가 없습니다.

  
```cpp  
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
```  
  
> [!TIP]
>  참고: Visual Studio 디버거에서 `constexpr` 함수 내에 중단점을 배치하여 컴파일 타임에 함수가 계산되는지 확인할 수 있습니다. 중단점을 적중할 경우 함수가 런타임에 호출되었습니다.  그렇지 않을 경우 함수가 컴파일 타임에 호출되었습니다.  
  
 
## <a name="example"></a>예  
 다음 예제에서는 `constexpr` 변수, 함수 및 사용자 정의 형식을 보여 줍니다. main()의 마지막 문에서 `constexpr` 멤버 함수 GetValue()는 컴파일 타임에 값을 몰라도 되기 때문에 런타임 호출입니다.  
  
```  
#include <iostream>  
  
using namespace std;  
  
// Pass by value   
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
  
// Pass by reference  
constexpr float exp2(const float& x, const int& n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp2(x * x, n / 2) :  
        exp2(x * x, (n - 1) / 2) * x;  
};  
  
// Compile time computation of array length  
template<typename T, int N>  
constexpr int length(const T(&ary)[N])   
{   
    return N;   
}   
  
// Recursive constexpr function  
constexpr int fac(int n)  
{   
    return n == 1 ? 1 : n*fac(n - 1);   
}  
  
// User-defined type  
class Foo  
{  
public:  
    constexpr explicit Foo(int i) : _i(i) {}  
    constexpr int GetValue()  
    {  
        return _i;  
    }  
private:  
    int _i;  
};  
  
int main()  
{  
    //foo is const:  
    constexpr Foo foo(5);   
    // foo = Foo(6); //Error!  
  
    //Compile time:  
    constexpr float x = exp(5, 3);   
    constexpr float y { exp(2, 5) };  
    constexpr int val = foo.GetValue();   
    constexpr int f5 = fac(5);  
    const int nums[] { 1, 2, 3, 4 };  
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };  
  
    //Run time:   
    cout << "The value of foo is " << foo.GetValue() << endl;   
  
}  
  
```  
  
## <a name="requirements"></a>요구 사항  
 Visual Studio 2015  
  
## <a name="see-also"></a>참고 항목  
 [선언 및 정의](../cpp/declarations-and-definitions-cpp.md)   
 [const](../cpp/const-cpp.md)