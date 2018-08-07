---
title: 형식 변환 및 형식 안전성 (최신 c + +) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ccdbc71679a197e0464b4ec42dba948754c4c5c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462266"
---
# <a name="type-conversions-and-type-safety-modern-c"></a>형식 변환 및 형식 안전성(최신 C++)
이 문서에서는 공용 형식 변환 문제를 식별하고 C++ 코드에서 이 문제를 방지하는 방법에 대해 설명합니다.  
  
 C++ 프로그램을 작성하는 경우 형식 안전이 확인되어야 합니다. 즉 모든 변수, 함수 인수 및 함수 반환 값에서 적합한 종류의 데이터를 저장하고 다른 형식의 값을 포함하는 작업이 "합리적"이며 데이터 손실, 비트 패턴의 잘못된 해석 또는 메모리 손상이 발생하지 않음을 의미합니다. 명시적 또는 암시적으로 값을 한 형식에서 다른 형식으로 변환하지 않는 프로그램은 정의에 따라 형식이 안전합니다. 그러나 안전하지 않은 변환인 경우에도 형식 변환이 필요한 경우가 있습니다. 부동의 결과 저장 해야 하는 예를 들어 형식의 변수에 작업을 가리키고 **int**, 부호 없는 값을 전달 해야 할 수 있습니다 **int** 로그인을 사용 하는 함수를  **int**합니다. 두 예제는 데이터 손실 또는 값의 다시 해석이 발생할 수 있으므로 안전하지 않은 변환을 보여 줍니다.  
  
 컴파일러에서 안전하지 않은 변환을 발견하는 경우 오류 또는 경고가 발생합니다. 오류는 컴파일을 중지합니다. 경고는 컴파일을 계속하지만 코드에서 가능한 오류를 나타냅니다. 그러나 프로그램이 경고 없이 컴파일되는 경우에도 암시적 형식 변환이 발생하고 잘못된 결과가 발생하는 코드가 포함될 수 있습니다. 코드에서 형식 오류는 명시적 변환 또는 캐스트에서 나타날 수도 있습니다.  
  
## <a name="implicit-type-conversions"></a>암시적 형식 변환  
 컴파일러는 기본 제공 사용 없습니다 명시적 캐스트를 사용할 수 있는 식에 다른 기본 제공 형식의 피연산자를 *표준 변환* 형식이 일치 되도록 피연산자 중 하나를 변환 합니다. 컴파일러는 하나가 성공할 때까지 잘 정의된 시퀀스의 변환을 시도합니다. 선택한 변환이 승격인 경우에는 컴파일러에서 경고가 발생되지 않습니다. 변환이 축소인 경우 컴파일러에서 가능한 데이터 손실에 대한 경고가 발생됩니다. 실제 데이터 손실이 발생하는지 여부는 관련된 실제 값에 따라 다르지만 이 경고를 오류로 처리하는 것이 좋습니다. 사용자 정의 형식이 포함된 경우 컴파일러에서는 클래스 정의에서 지정한 변환을 사용하려고 합니다. 허용되는 변환을 찾을 수 없는 경우 컴파일러에서 오류가 발생되고 프로그램이 컴파일되지 않습니다. 표준 변환을 제어 하는 규칙에 대 한 자세한 내용은 참조 하세요. [표준 변환](../cpp/standard-conversions.md)합니다. 사용자 정의 변환에 대 한 자세한 내용은 참조 하세요. [사용자 정의 변환 (C + + /cli CLI)](../dotnet/user-defined-conversions-cpp-cli.md)합니다.  
  
### <a name="widening-conversions-promotion"></a>확대 변환(승격)  
 확대 변환에서 작은 변수의 값은 데이터의 손실 없이 큰 변수에 할당됩니다. 확대 변환은 항상 안전하므로 컴파일러에서 확대 변환이 자동으로 수행되고 경고가 발생하지 않습니다. 다음 변환은 확대 변환입니다.  
  
|시작|대상|  
|----------|--------|  
|부호 있는 정수 또는 부호 없는 정수 형식이 제외한 **long long** 또는 **__int64**|**double**|  
|**bool** 또는 **char**|다른 기본 제공 형식|  
|**짧은** 또는 **wchar_t**|**int**하십시오 **긴**, **long long**|  
|**int**, **long**|**long long**|  
|**float**|**double**|  
  
### <a name="narrowing-conversions-coercion"></a>축소 변환(강제 변환)  
 컴파일러에서 암시적으로 축소 변환을 수행하지만 잠재적인 데이터 손실에 대한 경고가 나타납니다. 이러한 경고를 매우 심각하게 고려하십시오. 큰 변수의 값은 항상 작은 변수에 맞으므로 데이터 손실이 발생하지 않을 것이라고 가정하는 경우 컴파일러에서 더 이상 경고가 발생하지 않도록 명시적 캐스트를 추가합니다. 변환이 안전한지 확실하지 않은 경우에는 코드에 런타임 검사를 추가하여 프로그램에서 잘못된 결과가 발생하지 않도록 가능한 데이터 손실을 처리합니다. 
  
 부동 소수점 형식에서 정수 계열 형식으로의 모든 변환은 부동 소수점 값의 소수 부분이 삭제 및 손실되므로 축소 변환입니다.  
  
 다음 코드 예제에서는 일부 암시적 축소 변환 및 이에 대해 컴파일러에서 발생하는 경고를 보여 줍니다.  
  
```cpp  
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow  
wchar_t wch = 'A'; //OK  
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'  
              // to 'char', possible loss of data  
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from  
                           // 'int' to 'unsigned char'  
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to  
              // 'int', possible loss of data  
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to  
             // 'int', possible loss of data  
```  
  
### <a name="signed---unsigned-conversions"></a>부호 있는 - 부호 없는 변환  
 부호 있는 정수 계열 형식 및 해당 부호 없는 정수 계열 형식은 항상 크기가 동일하지만 값 변환에 대한 비트 패턴 해석 방법은 서로 다릅니다. 다음 코드 예제에서는 부호 있는 값과 부호 없는 값으로 동일한 비트 패턴을 해석할 때 발생하는 사항을 보여 줍니다. `num` 및 `num2`에 저장된 비트 패턴은 이전 그림에 표시되는 내용에서 변경되지 않습니다.  
  
```cpp  
using namespace std;  
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>  
short num2 = num;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
// Go the other way.  
num2 = -1;  
num = num2;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
```  
  
 값은 두 가지 지시 사항으로 다시 해석됩니다. 프로그램에서 값의 부호가 예상되는 결과와 반대인 홀수 결과를 생성하는 경우 부호 있는 정수 계열과 부호 없는 정수 계열 간의 암시적 변환을 찾습니다. 다음 예제에서는 식의 결과에 (0-1)에서 암시적으로 변환 됩니다 **int** 하 **부호 없는 int** 에 저장 되는 경우 `num`합니다. 이를 통해 비트 패턴이 다시 해석됩니다.  
  
```cpp  
unsigned int u3 = 0 - 1;  
cout << u3 << endl; // prints 4294967295  
```  
  
 컴파일러에서 부호 있는 정수 계열과 부호 없는 정수 계열 형식 간의 암시적 변환에 대한 경고가 발생하지 않습니다. 따라서 부호 있음에서 부호 없음으로의 변환을 완전히 방지하는 것이 좋습니다. 이러한 변환을 방지할 수 없는 경우에는 코드에 런타임 검사를 추가하여 변환되는 값이 0보다 크거나 같은지 및 부호 있는 형식의 최대값보다 작거나 같은지 확인합니다. 이 범위의 값은 다시 해석되지 않고 부호 있음에서 부호 없음으로 또는 부호 없음에서 부호 있음으로 전송됩니다.  
  
### <a name="pointer-conversions"></a>포인터 변환  
 많은 식에서 C 스타일 배열은 배열의 첫 번째 요소에 대한 포인터로 암시적으로 변환되고 상수 변환이 자동으로 발생할 수 있습니다. 이 방법이 편리하지만 잠재적으로 오류가 발생할 수도 있습니다. 예를 들어 다음 잘못 디자인된 코드 예제는 무의미한 것 같지만 Visual C++에서 컴파일되고 'p'의 결과를 생성합니다. 먼저 "Help" 문자열 상수 리터럴은 배열의 첫 번째 요소를 가리키는 `char*`로 변환되고 해당 포인터는 이제 마지막 요소 'p'를 가리키도록 세 가지 요소로 증가됩니다.  
  
```cpp  
char* s = "Help" + 3;  
```  
  
## <a name="explicit-conversions-casts"></a>명시적 변환(캐스트)  
 캐스트 작업을 사용하여 컴파일러가 한 형식의 값을 다른 형식으로 변환하도록 지시할 수 있습니다. 컴파일러에서는 두 가지 형식이 완전히 관련이 없는 일부 경우에 오류가 발생하지만 다른 경우에는 작업의 형식이 안전하지 않은 경우에도 오류가 발생하지 않습니다. 한 형식에서 다른 형식으로의 변환은 프로그램 오류의 잠재적 원인이므로 캐스트를 가능하면 사용하지 마십시오. 그러나 캐스트는 필요한 경우가 있으며 모든 캐스트가 똑같이 위험한 것은 아닙니다. 캐스트의 효과적인 사용 중 하나는 코드가 축소 변환을 수행하고 이러한 변환으로 프로그램에서 잘못된 결과가 생성되지 않는 경우입니다. 실제로 사용자가 해야 할 사항을 알고 있으므로 이에 대해 경고하지 않도록 컴파일러에 지시합니다. 다른 사용은 파생 클래스에 대한 포인터에서 기본 클래스에 대한 포인터로 캐스팅하는 것입니다. 캐스팅 하는 또 다른 용도 **상수**비 필요로 하는 함수에 전달할 변수 특성-**const** 인수. 대부분의 이러한 캐스팅 작업은 일부 위험이 내포됩니다.  
  
 C 스타일의 프로그래밍에서 동일한 C 스타일 캐스트 연산자는 모든 종류의 캐스트에 사용됩니다.  
  
```cpp  
(int) x; // old-style cast, old-style syntax  
int(x); // old-style cast, functional syntax  
```  
  
 C 스타일 캐스트 연산자는 호출 연산자 ()와 동일하므로 코드에서 눈에 띄지 않으며 간과하기 쉽습니다. 보기 또는 검색에 인식 하기 어렵고 및의 조합을 호출할 정도로 서로 이기 때문에 잘못 된 둘 **정적**를 **const**, 및 **reinterpret_cast**. 이전 스타일의 캐스트에서 실제로 수행하는 사항을 알아내는 것은 어려울 수 있으며 오류가 발생할 수 있습니다. 이러한 모든 이유로 캐스팅이 필요할 때 다음 C++ 캐스트 연산자 중 하나를 사용하는 것이 좋습니다. 해당 연산자는 경우에 따라 훨씬 더 형식 안정적이며 더욱 명시적인 프로그래밍 의도를 표시합니다.  
  
-   **static_cast**, 컴파일 시 검사 되는 캐스트에 대 한 시간만 합니다. **static_cast** 컴파일러가 완전히 호환 되지 않는 형식 간에 캐스팅 하려는 검색 하는 경우에 오류를 반환 합니다. 포인터에서 기본 클래스에 대한 포인터와 파생 클래스에 대한 포인터 간을 캐스팅하는 데 사용할 수도 있지만 이러한 변환이 런타임에서 안전한지 여부를 컴파일에서 항상 확인할 수 없습니다.  
  
    ```cpp  
    double d = 1.58947;  
    int i = d;  // warning C4244 possible loss of data  
    int j = static_cast<int>(d);       // No warning.  
    string s = static_cast<string>(d); // Error C2440:cannot convert from  
                                       // double to std:string  
  
    // No error but not necessarily safe.  
    Base* b = new Base();  
    Derived* d2 = static_cast<Derived*>(b);  
    ```  
  
     자세한 내용은 [static_cast](../cpp/static-cast-operator.md)합니다.  
  
-   **dynamic_cast**에 대 한 포인터에서 기본 포인터를 파생의 안전 하 고 런타임이 검사 된 캐스트 합니다. A **dynamic_cast** 보다 안전를 **static_cast** 다운 캐스트 있지만 런타임 검사는 일부 오버 헤드를 초래 합니다.  
  
    ```cpp  
    Base* b = new Base();  
  
    // Run-time check to determine whether b is actually a Derived*  
    Derived* d3 = dynamic_cast<Derived*>(b);  
  
    // If b was originally a Derived*, then d3 is a valid pointer.  
    if(d3)  
    {  
       // Safe to call Derived method.  
       cout << d3->DoSomethingMore() << endl;  
    }  
    else  
    {  
       // Run-time check failed.  
       cout << "d3 is null" << endl;  
    }  
  
    //Output: d3 is null;  
    ```  
  
     자세한 내용은 [dynamic_cast](../cpp/dynamic-cast-operator.md)합니다.  
  
-   **const_cast**캐스팅 하는 것에 대 한 합니다 **const**변수의 변수 또는 비 변환-**const** 변수를 **const**합니다. 캐스팅 하는 것 **상수**-이 연산자를 사용 하 여 ness는 방금으로 오류가 발생 하기 쉬운 C 스타일의 캐스트를 사용 하 여 제외 하 고 사용 하는 **const 캐스트** 실수로 캐스트를 수행 하려면 작은 가능성이 있습니다. 캐스팅 해야 할 경우가 합니다 **const**-변수의 예를 들어, 전달할 특성을 **const** 변수는 함수는 비-를**const** 매개 변수입니다. 다음 예제에서는 이 작업을 수행하는 방법을 보여 줍니다.  
  
    ```cpp  
    void Func(double& d) { ... }  
    void ConstCast()  
    {  
       const double pi = 3.14;  
       Func(const_cast<double&>(pi)); //No error.  
    }  
    ```  
  
     자세한 내용은 [const_cast](../cpp/const-cast-operator.md)합니다.  
  
-   **reinterpret_cast**같은 관련 없는 형식 간 캐스트에 대 한 **포인터** 하려면 **int**합니다.  
  
    > [!NOTE]
    >  이 캐스트 연산자는 다른 연산자만큼 자주 사용되지 않으며 다른 컴파일러로 이식되는 것을 보장하지 않습니다.  
  
     다음 예제에서는 어떻게 **reinterpret_cast** 에서 다른 **static_cast**합니다.  
  
    ```cpp  
    const char* str = "hello";  
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot  
                                  // convert from 'const char *' to 'int'  
    int j = (int)str; // C-style cast. Did the programmer really intend  
                      // to do this?  
    int k = reinterpret_cast<int>(str);// Programming intent is clear.  
                                       // However, it is not 64-bit safe.  
    ```  
  
     자세한 내용은 [reinterpret_cast 연산자](../cpp/reinterpret-cast-operator.md)합니다.  
  
## <a name="see-also"></a>참고자료  
 [C + + 형식 시스템](../cpp/cpp-type-system-modern-cpp.md)   
 [C + +의 진화](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C++ 언어 참조](../cpp/cpp-language-reference.md)   
 [C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)