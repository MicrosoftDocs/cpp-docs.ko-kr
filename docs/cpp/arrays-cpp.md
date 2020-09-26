---
title: 배열 (C++)
ms.date: 08/03/2020
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 6d002f2baa6657c13ffc603e74828ab60585d3a9
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352793"
---
# <a name="arrays-c"></a>배열 (C++)

배열은 인접 한 메모리 영역을 차지 하는 동일한 형식의 개체 시퀀스입니다. 기존의 C 스타일 배열은 많은 버그의 소스 이지만 특히 이전 코드 베이스에서는 여전히 일반적입니다. 최신 c + +에서는이 섹션에 설명 된 C 스타일 배열 대신 [std:: vector](../standard-library/vector-class.md) 또는 [std:: array](../standard-library/array-class-stl.md) 를 사용 하는 것이 좋습니다. 이러한 표준 라이브러리 형식은 모두 인접 한 메모리 블록으로 해당 요소를 저장 합니다. 그러나 이러한 형식은 훨씬 더 큰 형식 안전성을 제공 하며 시퀀스 내에서 유효한 위치를 가리키도록 보장 되는 반복기를 지원 합니다. 자세한 내용은 [컨테이너](../standard-library/stl-containers.md)를 참조 하세요.

## <a name="stack-declarations"></a>스택 선언

C + + 배열 선언에서 배열 크기는 다른 언어에서와 같이 형식 이름이 아닌 변수 이름 뒤에 지정 됩니다. 다음 예제에서는 스택에 할당 될 1000의 배열을 선언 합니다. 요소 수는 정수 리터럴로 제공 하거나 다른 식으로 상수 식으로 제공 해야 합니다. 컴파일러가 할당할 스택 공간의 크기를 알고 있어야 하기 때문입니다. 런타임에 계산 된 값을 사용할 수 없습니다. 배열의 각 요소에는 기본값 0이 할당 됩니다. 기본값을 할당 하지 않는 경우 각 요소는 해당 메모리 위치에 발생 하는 임의 값을 처음에 포함 합니다.

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

배열의 첫 번째 요소는 0 번째 요소입니다. 마지막 요소는 (*n*-1) 요소입니다. 여기서 *n* 은 배열에 포함 될 수 있는 요소의 수입니다. 선언에 있는 요소 수는 정수 계열 형식 이어야 하며 0 보다 커야 합니다. 프로그램에서 보다 큰 첨자 연산자에 값을 전달 하지 않도록 하는 것은 사용자의 책임입니다 `(size - 1)` .

크기가 0 인 배열은 배열이 또는에서 마지막 필드이 **`struct`** **`union`** 고 Microsoft 확장을 사용 하도록 설정 **`/Za`** 하거나 설정 하지 않은 경우에만 유효 **`/permissive-`** 합니다.

스택 기반 배열은 힙 기반 배열 보다 할당 및 액세스 속도가 더 빠릅니다. 그러나 스택 공간은 제한적입니다. 배열 요소의 수는 너무 커서 너무 많은 스택 메모리를 사용할 수 없습니다. 프로그램에 따라 너무 많이 달라 집니다. 프로 파일링 도구를 사용 하 여 배열이 너무 큰지 여부를 확인할 수 있습니다.

## <a name="heap-declarations"></a>힙 선언

스택에 할당 하기에는 너무 큰 배열이 필요 하거나 컴파일 시간에 해당 크기를 알 수 없는 배열이 필요할 수 있습니다. 식을 사용 하 여 힙에이 배열을 할당할 수 있습니다 [`new[]`](new-operator-cpp.md) . 연산자는 첫 번째 요소에 대 한 포인터를 반환 합니다. 첨자 연산자는 스택 기반 배열에서와 동일한 방식으로 포인터 변수에 대해 작동 합니다. [포인터 산술 연산을](../c-language/pointer-arithmetic.md) 사용 하 여 포인터를 배열의 임의 요소로 이동할 수도 있습니다. 다음을 확인 하는 것은 사용자의 책임입니다.

- 배열이 더 이상 필요 하지 않을 때 메모리를 삭제할 수 있도록 항상 원래 포인터 주소의 복사본을 보관 합니다.
- 배열 범위를 벗어난 포인터 주소는 증가 하거나 감소 하지 않습니다.

다음 예제에서는 런타임에 힙에서 배열을 정의 하는 방법을 보여 줍니다. 다음은 첨자 연산자를 사용 하 여 배열 요소에 액세스 하는 방법과 포인터 산술 연산을 사용 하는 방법을 보여 줍니다.

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>배열 초기화

루프, 한 번에 한 개의 요소 또는 단일 문에서 배열을 초기화할 수 있습니다. 다음 두 배열의 내용이 동일 합니다.

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>함수에 배열 전달

배열이 함수에 전달 되 면 스택 기반 배열 또는 힙 기반 배열 인지에 관계 없이 첫 번째 요소에 대 한 포인터로 전달 됩니다. 포인터에 추가 크기 또는 형식 정보가 포함 되어 있지 않습니다. 이 동작을 *포인터 감소*라고 합니다. 배열을 함수에 전달 하는 경우에는 항상 별도의 매개 변수에서 요소 수를 지정 해야 합니다. 이 동작은 배열이 함수에 전달 될 때 배열 요소가 복사 되지 않는다는 의미 이기도 합니다. 함수가 요소를 수정 하지 않도록 하려면 매개 변수를 요소에 대 한 포인터로 지정 합니다 **`const`** .

다음 예제에서는 배열 및 길이를 허용 하는 함수를 보여 줍니다. 포인터가 복사본이 아니라 원래 배열을 가리킵니다. 매개 변수가이 아닌 **`const`** 경우 함수는 배열 요소를 수정할 수 있습니다.

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

함수 블록 내에서 읽기 전용으로 만들려면 배열을 const로 선언 합니다.

```cpp
void process(const double p*, const size_t len);
```

동작을 변경 하지 않고 동일한 함수를 이러한 방식으로 선언할 수도 있습니다. 배열은 여전히 첫 번째 요소에 대 한 포인터로 전달 됩니다.

```cpp
// Unsized array
void process(const double p[], const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>다차원 배열

다른 배열에서 생성된 배열은 다차원 배열입니다. 이러한 다차원 배열은 여러 개의 대괄호로 묶인 상수 식을 순서대로 배치하여 지정됩니다. 예를 들어 다음 선언을 생각해 볼 수 있습니다.

```cpp
int i2[5][7];
```

**`int`** 다음 그림에 표시 된 것 처럼 5 개의 행과 7 개의 열로 이루어진 2 차원 행렬에 개념적으로 정렬 된 형식의 배열을 지정 합니다.

![다중&#45;차원 배열의 개념적 레이아웃](../cpp/media/vc38rc1.gif "다중&#45;차원 배열의 개념적 레이아웃") <br/>
다차원 배열의 개념적 레이아웃

[이니셜라이저에 설명](../cpp/initializers.md)된 대로 이니셜라이저 목록이 있는 다중 차원을 포함 하는 배열을 선언할 수 있습니다. 이러한 선언에서 첫 번째 차원의 경계를 지정 하는 상수 식은 생략할 수 있습니다. 예를 들면 다음과 같습니다.

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

앞의 선언은 세 개의 행과 네 개의 열로 구성된 배열을 정의합니다. 행은 공장을 나타내고 열은 공장에서 출하되는 시장을 나타냅니다. 값은 공장에서 시장까지의 운송 비용입니다. 배열의 첫 번째 차원은 생략되었지만 컴파일러가 이니셜라이저를 검사하여 해당 차원을 채웁니다.

N 차원 배열 형식에 대 한 간접 참조 연산자 (*)를 사용 하면 n-1 차원 배열이 생성 됩니다. n이 1인 경우 스칼라(또는 배열 요소)가 생성됩니다.

C++ 배열은 행 중심 순서로 저장됩니다. 행 중심 순서는 마지막 첨자가 가장 빠르게 변경됨을 의미합니다.

## <a name="example"></a>예제

다음과 같이 함수 선언에서 다차원 배열의 첫 번째 차원에 대 한 범위 지정을 생략할 수도 있습니다.

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

함수는 `FindMinToMkt` 새 팩터리를 추가 하는 경우 코드를 변경할 필요가 없으며 다시 컴파일해야 합니다.

## <a name="initializing-arrays"></a>배열 초기화

클래스 생성자가 있는 개체의 배열은 생성자에 의해 초기화 됩니다. 이니셜라이저 목록에 배열의 요소 보다 더 작은 항목이 있는 경우 나머지 요소에 대해 기본 생성자가 사용 됩니다. 클래스에 대해 정의 된 기본 생성자가 없는 경우 이니셜라이저 목록이 *완전*해야 합니다. 즉, 배열의 각 요소에 대해 이니셜라이저가 하나씩 있어야 합니다.

생성자 두 개를 정의하는 `Point` 클래스를 살펴보세요.

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

`aPoint`의 첫 번째 요소는 `Point( int, int )` 생성자를 사용하여 생성되고 나머지 두 요소는 기본 생성자를 사용하여 생성됩니다.

정적 멤버 배열 (에 관계 없이 **`const`** )은 해당 정의에서 초기화할 수 있습니다 (클래스 선언 외부). 예를 들면 다음과 같습니다.

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>배열 요소 액세스

배열 첨자 연산자(`[ ]`)를 사용하여 배열의 개별 요소에 액세스할 수 있습니다. 1 차원 배열의 이름을 첨자 없이 사용 하는 경우에는 배열의 첫 번째 요소에 대 한 포인터로 계산 됩니다.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

다차원 배열을 사용할 때 식에서 다양한 조합을 사용할 수 있습니다.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

위의 코드에서 `multi` 는 형식의 3 차원 배열입니다 **`double`** . `p2multi`포인터는 크기가 3 인 형식의 배열을 가리킵니다 **`double`** . 이 예제에서 배열은 한 개, 두 개 및 세 개의 아래 첨자와 함께 사용됩니다. 문에서와 같이 모든 첨자를 지정 하는 것이 일반적 이지만 `cout` 다음 문에서와 같이 배열 요소의 특정 하위 집합을 선택 하는 것이 유용할 수 있습니다 `cout` .

## <a name="overloading-subscript-operator"></a>첨자 연산자 오버 로드

다른 연산자와 마찬가지로 첨자 연산자 ( `[]` )는 사용자가 재정의할 수 있습니다. 첨자 연산자의 기본 동작은 다음 메서드를 사용하여 배열 이름과 첨자를 결합하는 것입니다.

`*((array_name) + (subscript))`

포인터 형식이 포함 된 모든 추가의 경우 처럼 크기 조정을 자동으로 수행 하 여 형식의 크기를 조정 합니다. 결과 값은의 원점에서 *n* 바이트가 `array_name` 아니라 배열의 *n*번째 요소입니다. 이 변환에 대 한 자세한 내용은 [덧셈 연산자](additive-operators-plus-and.md)를 참조 하세요.

다차원 배열에서도 다음 메서드를 사용하여 주소가 파생됩니다.

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>식의 배열

배열 형식의 식별자가 아닌 식에 **`sizeof`** , 참조의 주소 () 또는 초기화가 표시 되 면 `&` 첫 번째 배열 요소에 대 한 포인터로 변환 됩니다. 예를 들면 다음과 같습니다.

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

`psz` 포인터는 `szError1` 배열의 첫 번째 요소를 가리킵니다. 포인터와 달리 배열은 l-value를 수정할 필요가 없습니다. 그 이유는 다음 할당이 잘못 된 것입니다.

```cpp
szError1 = psz;
```

## <a name="see-also"></a>참고 항목

[std:: array](../standard-library/array-class-stl.md)
