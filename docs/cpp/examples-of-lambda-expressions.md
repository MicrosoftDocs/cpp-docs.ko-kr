---
title: 람다 식의 예 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c83802dcc7382040d3b9f40bd0bbc2fe13d076f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="examples-of-lambda-expressions"></a>람다 식의 예
이 문서에서는 프로그램에 람다 식을 사용하는 방법을 보여 줍니다. 람다 식의 개요를 참조 하십시오. [람다 식](../cpp/lambda-expressions-in-cpp.md)합니다. 람다 식의 구조에 대 한 자세한 내용은 참조 [람다 식 구문](../cpp/lambda-expression-syntax.md)합니다.  
  
##  <a name="declaringLambdaExpressions"></a> 람다 식 선언  
  
### <a name="example-1"></a>예제 1  
 람다 식을 입력 하기 때문에 지정할 수 있습니다는 `auto` 변수 또는 [함수](../standard-library/function-class.md) 다음과 같이 개체:  
  
### <a name="code"></a>코드  
  
```cpp  
// declaring_lambda_expressions1.cpp  
// compile with: /EHsc /W4  
#include <functional>  
#include <iostream>  
  
int main()  
{  
  
    using namespace std;  
  
    // Assign the lambda expression that adds two numbers to an auto variable.  
    auto f1 = [](int x, int y) { return x + y; };  
  
    cout << f1(2, 3) << endl;  
  
    // Assign the same lambda expression to a function object.  
    function<int(int, int)> f2 = [](int x, int y) { return x + y; };  
  
    cout << f2(3, 4) << endl;  
}  
```  
  
### <a name="output"></a>출력  
  
```Output  
5  
7  
```  
  
### <a name="remarks"></a>설명  
 자세한 내용은 참조 [자동](../cpp/auto-cpp.md), [클래스 함수](../standard-library/function-class.md), 및 [함수 호출](../cpp/function-call-cpp.md)합니다.  
  
 람다 식은 함수의 본문에서 대부분 선언되지만 변수를 초기화할 수 있는 어느 곳에서나 선언할 수 있습니다.  
  
### <a name="example-2"></a>예제 2  
 식을 호출할 때 대신 식을 선언할 때 Visual C++ 컴파일러는 캡처된 변수에 람다 식을 바인딩합니다. 다음 예제에서는 변수 지역 변수 `i`값과 참조로서 변수 `j`를 캡처하는 람다 식을 보여 줍니다. 람다 식은 `i`를 값으로 캡처하기 때문에 프로그램에서 `i` 이상을 다시 할당하면 식의 결과에 영향을 주지 않습니다. 그러나 람다 식을 `j`를 참조로 캡처하기 때문에 `j`를 다시 할당하면 식의 결과에 영향을 주지 않습니다.  
  
### <a name="code"></a>코드  
  
```cpp  
// declaring_lambda_expressions2.cpp  
// compile with: /EHsc /W4  
#include <functional>  
#include <iostream>  
  
int main()  
{  
   using namespace std;  
  
   int i = 3;  
   int j = 5;  
  
   // The following lambda expression captures i by value and  
   // j by reference.  
   function<int (void)> f = [i, &j] { return i + j; };  
  
   // Change the values of i and j.  
   i = 22;  
   j = 44;  
  
   // Call f and print its result.  
   cout << f() << endl;  
}  
```  
  
### <a name="output"></a>출력  
  
```Output  
47  
```  
  
 [[이 문서의 내용](#top)]  
  
##  <a name="callingLambdaExpressions"></a> 람다 식 호출  
 다음 코드 조각과 같이 람다 식을 즉시 호출할 수 있습니다. 두 번째 조각은 람다를 인수로 알고리즘에 전달 하 c + + 표준 라이브러리와 같은 방법을 보여 줍니다 `find_if`합니다.  
  
### <a name="example-1"></a>예제 1  
 이 예제에서는 두 정수의 합을 반환하고 식 인수를 사용하여 인수 `5` 및 `4`로 식을 즉시 호출하는 람다 식을 선언합니다.  
  
### <a name="code"></a>코드  
  
```cpp  
// calling_lambda_expressions1.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main()  
{  
   using namespace std;  
   int n = [] (int x, int y) { return x + y; }(5, 4);  
   cout << n << endl;  
}  
```  
  
### <a name="output"></a>출력  
  
```Output  
9  
```  
  
### <a name="example-2"></a>예제 2  
 이 예제에서는 람다 식을 `find_if` 함수에 대한 인수로 전달합니다. 람다 식은 매개 변수가 짝수이면 `true`를 반환합니다.  
  
### <a name="code"></a>코드  
  
```cpp  
// calling_lambda_expressions2.cpp  
// compile with: /EHsc /W4  
#include <list>  
#include <algorithm>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    // Create a list of integers with a few initial elements.  
    list<int> numbers;  
    numbers.push_back(13);  
    numbers.push_back(17);  
    numbers.push_back(42);  
    numbers.push_back(46);  
    numbers.push_back(99);  
  
    // Use the find_if function and a lambda expression to find the   
    // first even number in the list.  
    const list<int>::const_iterator result =   
        find_if(numbers.begin(), numbers.end(),[](int n) { return (n % 2) == 0; });  
  
    // Print the result.  
    if (result != numbers.end()) {  
        cout << "The first even number in the list is " << *result << "." << endl;  
    } else {  
        cout << "The list contains no even numbers." << endl;  
    }  
}  
```  
  
### <a name="output"></a>출력  
  
```Output  
The first even number in the list is 42.  
```  
  
### <a name="remarks"></a>설명  
 에 대 한 자세한 내용은 `find_if` 함수, 참조 [find_if](../standard-library/algorithm-functions.md#find_if)합니다. 공용 알고리즘을 수행 하는 c + + 표준 라이브러리 함수에 대 한 자세한 내용은 참조 [ \<알고리즘 >](../standard-library/algorithm.md)합니다.  
  
 [[이 문서의 내용](#top)]  
  
##  <a name="nestingLambdaExpressions"></a> 람다 식 중첩  
  
### <a name="example"></a>예제  
 이 예제와 같이 람다 식을 다른 람다 식 안에 중첩할 수 있습니다. 안쪽 람다 식은 인수를 2를 곱한 후 결과를 반환합니다. 바깥쪽 람다 식은 안쪽 람다 식의 인수와 함께 호출하고 결과에 3을 더합니다.  
  
### <a name="code"></a>코드  
  
```cpp  
// nesting_lambda_expressions.cpp  
// compile with: /EHsc /W4  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    // The following lambda expression contains a nested lambda  
    // expression.  
    int timestwoplusthree = [](int x) { return [](int y) { return y * 2; }(x) + 3; }(5);  
  
    // Print the result.  
    cout << timestwoplusthree << endl;  
}  
  
```  
  
### <a name="output"></a>출력  
  
```Output  
13  
```  
  
### <a name="remarks"></a>설명  
 이 예제에서 `[](int y) { return y * 2; }`는 중첩된 람다 식입니다.  
  
 [[이 문서의 내용](#top)]  
  
##  <a name="higherOrderLambdaExpressions"></a> 고차 람다 함수  
  
### <a name="example"></a>예제  
 많은 프로그래밍 언어의 개념을 지원 한 *고차 함수입니다.* 고차 함수는 람다 식으로, 다른 람다 식을 인수로 취하거나 람다 식을 반환합니다. 사용할 수는 [함수](../standard-library/function-class.md) 클래스를 사용 하는 동작 하는 c + + 람다 식 고차 함수와 같이 합니다. 다음 예제에서는 `function` 개체를 반환하는 람다 식과 인수로서 `function` 개체를 취하는 람다 식을 보여 줍니다.  
  
### <a name="code"></a>코드  
  
```cpp  
// higher_order_lambda_expression.cpp  
// compile with: /EHsc /W4  
#include <iostream>  
#include <functional>  
  
int main()  
{  
    using namespace std;  
  
    // The following code declares a lambda expression that returns   
    // another lambda expression that adds two numbers.   
    // The returned lambda expression captures parameter x by value.  
    auto addtwointegers = [](int x) -> function<int(int)> {   
        return [=](int y) { return x + y; };   
    };  
  
    // The following code declares a lambda expression that takes another  
    // lambda expression as its argument.  
    // The lambda expression applies the argument z to the function f  
    // and multiplies by 2.  
    auto higherorder = [](const function<int(int)>& f, int z) {   
        return f(z) * 2;   
    };  
  
    // Call the lambda expression that is bound to higherorder.   
    auto answer = higherorder(addtwointegers(7), 8);  
  
    // Print the result, which is (7+8)*2.  
    cout << answer << endl;  
}  
  
```  
  
### <a name="output"></a>출력  
  
```Output  
30  
```  
  
 [[이 문서의 내용](#top)]  
  
##  <a name="methodLambdaExpressions"></a> 함수에서 람다 식 사용  
  
### <a name="example"></a>예제  
 함수의 본문에서 람다 식을 사용할 수 있습니다. 람다 식은 바깥쪽 함수에서 액세스할 수 있는 모든 함수 또는 데이터 멤버에 액세스할 수 있습니다. `this` 포인터를 명시적으로나 암시적으로 캡처하여 바깥쪽 클래스의 데이터 멤버 및 함수에 대한 액세스를 제공할 수 있습니다.  
**Visual Studio 2017 버전 15.3 이상** (사용할 수 있는 [/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 캡처 `this` 값별로 (`[*this]`) 경우 람다는 비동기 또는 병렬 작업에서 코드 수 있습니다 원래 개체 범위를 벗어난 후 실행 합니다.
  
 다음과 같이 함수에서 명시적으로 `this` 포인터를 사용할 수 있습니다.  
  
```cpp  

// capture "this" by reference
void ApplyScale(const vector<int>& v) const  
{  
   for_each(v.begin(), v.end(),   
      [this](int n) { cout << n * _scale << endl; });  
}  

// capture "this" by value (Visual Studio 2017 version 15.3 and later)
void ApplyScale2(const vector<int>& v) const  
{  
   for_each(v.begin(), v.end(),   
      [*this](int n) { cout << n * _scale << endl; });  
}  

```  
  
 `this` 포인터를 암시적으로 캡처할 수도 있습니다.  
  
```  
void ApplyScale(const vector<int>& v) const  
{  
   for_each(v.begin(), v.end(),   
      [=](int n) { cout << n * _scale << endl; });  
}  
```  
  
 다음 예제에서는 소수 자릿수 값을 캡슐화하는 `Scale` 클래스를 보여 줍니다.  
  
```cpp  
// function_lambda_expression.cpp  
// compile with: /EHsc /W4  
#include <algorithm>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
class Scale  
{  
public:  
    // The constructor.  
    explicit Scale(int scale) : _scale(scale) {}  
  
    // Prints the product of each element in a vector object   
    // and the scale value to the console.  
    void ApplyScale(const vector<int>& v) const  
    {  
        for_each(v.begin(), v.end(), [=](int n) { cout << n * _scale << endl; });  
    }  
  
private:  
    int _scale;  
};  
  
int main()  
{  
    vector<int> values;  
    values.push_back(1);  
    values.push_back(2);  
    values.push_back(3);  
    values.push_back(4);  
  
    // Create a Scale object that scales elements by 3 and apply  
    // it to the vector object. Does not modify the vector.  
    Scale s(3);  
    s.ApplyScale(values);  
}  
  
```  
  
### <a name="output"></a>출력  
  
```Output  
3  
6  
9  
12  
  
```  
  
### <a name="remarks"></a>설명  
 `ApplyScale` 함수는 람다 식을 사용하여 `vector` 개체에서 스케일 값 및 각 요소의 곱을 인쇄합니다. 람다 식은 포인터를 `this` 멤버에 액세스할 수 있도록 암시적으로 `_scale`를 캡처합니다.  
  
 [[이 문서의 내용](#top)]  
  
##  <a name="templateLambdaExpressions"></a> 템플릿이 있는 람다 식 사용  
  
### <a name="example"></a>예제  
 람다 식이 형식화되기 때문에 C++ 템플릿과 함께 사용할 수 있습니다. 다음 예제에서는 `negate_all` 및 `print_all` 함수를 보여 줍니다. `negate_all` 함수는 단항 `operator-`를 `vector` 개체의 각 요소에 적용합니다. `print_all` 함수는 `vector` 개체의 각 요소를 콘솔에 인쇄합니다.  
  
### <a name="code"></a>코드  
  
```cpp  
// template_lambda_expression.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
// Negates each element in the vector object. Assumes signed data type.  
template <typename T>  
void negate_all(vector<T>& v)  
{  
    for_each(v.begin(), v.end(), [](T& n) { n = -n; });  
}  
  
// Prints to the console each element in the vector object.  
template <typename T>  
void print_all(const vector<T>& v)  
{  
    for_each(v.begin(), v.end(), [](const T& n) { cout << n << endl; });  
}  
  
int main()  
{  
    // Create a vector of signed integers with a few elements.  
    vector<int> v;  
    v.push_back(34);  
    v.push_back(-43);  
    v.push_back(56);  
  
    print_all(v);  
    negate_all(v);  
    cout << "After negate_all():" << endl;  
    print_all(v);  
}  
  
```  
  
### <a name="output"></a>출력  
  
```Output  
34  
-43  
56  
After negate_all():  
-34  
43  
-56  
  
```  
  
### <a name="remarks"></a>설명  
 C + + 템플릿에 대 한 자세한 내용은 참조 하십시오. [템플릿](../cpp/templates-cpp.md)합니다.  
  
 [[이 문서의 내용](#top)]  
  
##  <a name="ehLambdaExpressions"></a> 예외 처리  
  
### <a name="example"></a>예제  
 람다 수식의 본문은 SEH(구조적 예외 처리)와 C++ 예외 처리에 대한 규칙을 따릅니다. 람다 식의 본문에는 양각된 예외를 처리하거나 예외 처리를 포함하는 범위를 지연시킬 수 있습니다. 다음 예제에서는 `for_each` 함수와 람다 식을 사용하여 하나의 `vector` 개체에 다른 개체의 값을 채웁니다. 사용 하 여 한 `try` / `catch` 첫 번째 벡터에 대 한 잘못 된 액세스를 처리 하는 블록입니다.  
  
### <a name="code"></a>코드  
  
```cpp  
// eh_lambda_expression.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <algorithm>  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    // Create a vector that contains 3 elements.  
    vector<int> elements(3);  
  
    // Create another vector that contains index values.  
    vector<int> indices(3);  
    indices[0] = 0;  
    indices[1] = -1; // This is not a valid subscript. It will trigger an exception.  
    indices[2] = 2;  
  
    // Use the values from the vector of index values to   
    // fill the elements vector. This example uses a   
    // try/catch block to handle invalid access to the   
    // elements vector.  
    try  
    {  
        for_each(indices.begin(), indices.end(), [&](int index) {   
            elements.at(index) = index;   
        });  
    }  
    catch (const out_of_range& e)  
    {  
        cerr << "Caught '" << e.what() << "'." << endl;  
    };  
}  
```  
  
### <a name="output"></a>출력  
  
```Output  
Caught 'invalid vector<T> subscript'.  
```  
  
### <a name="remarks"></a>설명  
 예외 처리에 대 한 자세한 내용은 참조 [예외 처리](../cpp/exception-handling-in-visual-cpp.md)합니다.  
  
 [[이 문서의 내용](#top)]  
  
##  <a name="managedLambdaExpressions"></a> 관리 되는 형식으로 람다 식 사용 (C + + /cli CLI)  
  
### <a name="example"></a>예제  
 람다 식의 캡처 절에는 관리되는 형식의 변수가 포함될 수 없습니다. 그러나 관리되는 형식이 포함된 인수를 람다 식의 매개 변수 목록으로 전달할 수 있습니다. 다음 예제에서는 관리되지 않는 지역 변수 `ch`를 캡처하는 람다 식을 포함하고 매개 변수로서 <xref:System.String?displayProperty=fullName> 개체를 가져옵니다.  
  
### <a name="code"></a>코드  
  
```cpp  
// managed_lambda_expression.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
    char ch = '!'; // a local unmanaged variable  
  
    // The following lambda expression captures local variables  
    // by value and takes a managed String object as its parameter.  
    [=](String ^s) {   
        Console::WriteLine(s + Convert::ToChar(ch));   
    }("Hello");  
}  
  
```  
  
### <a name="output"></a>출력  
  
```Output  
Hello!  
```  
  
### <a name="remarks"></a>설명  
 STL/CLR 라이브러리에서 람다 식을 사용할 수도 있습니다. 자세한 내용은 참조 [STL/CLR 라이브러리 참조](../dotnet/stl-clr-library-reference.md)합니다.  
  
> [!IMPORTANT]
>  람다는 `ref class`, `ref struct`, `value class` 또는 `value struct` 등의 이러한 공용 언어 런타임(CLR)의 관리되는 엔터티에서 지원되지 않습니다.  
  
 [[이 문서의 내용](#top)]  
  
## <a name="see-also"></a>참고 항목  
 [람다 식](../cpp/lambda-expressions-in-cpp.md)   
 [람다 식 구문](../cpp/lambda-expression-syntax.md)   
 [자동](../cpp/auto-cpp.md)   
 [function 클래스](../standard-library/function-class.md)   
 [find_if](../standard-library/algorithm-functions.md#find_if)   
 [\<알고리즘 >](../standard-library/algorithm.md)   
 [함수 호출](../cpp/function-call-cpp.md)   
 [서식 파일](../cpp/templates-cpp.md)   
 [예외 처리](../cpp/exception-handling-in-visual-cpp.md)   
 [STL/CLR 라이브러리 참조](../dotnet/stl-clr-library-reference.md)