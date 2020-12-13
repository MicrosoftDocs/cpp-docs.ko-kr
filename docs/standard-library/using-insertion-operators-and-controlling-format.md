---
description: '자세한 정보: 삽입 연산자 사용 및 형식 제어'
title: 삽입 연산자 사용 및 형식 제어
ms.date: 11/04/2016
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
ms.openlocfilehash: 0ed0e850cb578b66ea9131d135891cbbd26da4b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153566"
---
# <a name="using-insertion-operators-and-controlling-format"></a>삽입 연산자 사용 및 형식 제어

이 항목에서는 형식을 제어하는 방법 및 고유 클래스에 대한 삽입 연산자를 만드는 방법을 보여 줍니다. **<<** 모든 표준 c + + 데이터 형식에 대 한 미리 프로그래밍 삽입 () 연산자는 출력 스트림 개체에 바이트를 보냅니다. 삽입 연산자는 정수 인수의 기본 형식을 변경하는 요소인 미리 정의된 "조작자"와 함께 작동합니다.

다음 옵션을 사용하여 형식을 제어할 수 있습니다.

- [출력 너비](#vclrfoutputwidthanchor3)

- [맞춤](#vclrfalignmentanchor4)

- [정밀도](#vclrfprecisionanchor5)

- [기 수](#vclrfradixanchor6)

## <a name="output-width"></a><a name="vclrfoutputwidthanchor3"></a> 출력 너비

출력을 정렬 하려면 `setw` 스트림에 조작자를 배치 하거나 멤버 함수를 호출 하 여 각 항목에 대 한 출력 너비를 지정 합니다 `width` . 이 예제에서는 너비가 10자 이상인 열의 값을 오른쪽에 맞춥니다.

```cpp
// output_width.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   for( int i = 0; i < 4; i++ )
   {
      cout.width(10);
      cout << values[i] << '\n';
   }
}
```

```Output
      1.23
     35.36
     653.7
   4358.24
```

너비가 10자 미만인 값은 앞에 공백이 추가됩니다.

필드를 채우려면 지정 된 너비의 `fill` 필드에 대 한 패딩 문자의 값을 설정 하는 멤버 함수를 사용 합니다. 기본값은 공백입니다. 별표를 사용 하 여 숫자 열을 채우려면 이전 루프를 다음과 같이 수정 합니다 **`for`** .

```cpp
for (int i = 0; i <4; i++)
{
    cout.width(10);
    cout.fill('*');
    cout << values[i] << endl;
}
```

`endl` 조작자는 줄 바꿈 문자(`'\n'`)를 대체합니다. 출력은 다음과 같습니다.

```Output
******1.23
*****35.36
*****653.7
**_4358.24
```

동일한 줄의 데이터 요소에 대한 너비를 지정하려면 `setw` 조작자를 사용합니다.

```cpp
// setw.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   char _names[] = { "Zoot", "Jimmy", "Al", "Stan" };
   for( int i = 0; i < 4; i++ )
      cout << setw( 7 )  << names[i]
           << setw( 10 ) << values[i] << endl;
}
```

`width`멤버 함수는에서 선언 됩니다 \<iostream> . 또는 인수를 사용 하는 다른 조작자를 사용 하는 경우에 `setw` 는를 포함 해야 \<iomanip> 합니다. 출력에서 문자열은 너비가 6인 필드에 출력되고 정수는 너비가 10인 필드에 출력됩니다.

```Output
   Zoot      1.23
  Jimmy     35.36
     Al     653.7
   Stan   4358.24
```

`setw`및은 `width` 값을 잘리지 않습니다. 형식이 지정된 출력이 너비를 초과할 경우 전체 값이 출력되고 스트림의 전체 자릿수 설정이 적용됩니다. `setw`및 `width` 는 모두 다음 필드에만 영향을 줍니다. 한 필드가 출력된 후 필드 너비가 기본 동작(필요한 너비)으로 돌아갑니다. 그러나 다른 스트림 형식 옵션은 변경될 때까지 적용된 상태로 유지됩니다.

## <a name="alignment"></a><a name="vclrfalignmentanchor4"></a> 할당

출력 스트림은 기본적으로 오른쪽 맞춤 텍스트로 설정됩니다. 앞의 예제에서 이름을 왼쪽에 맞추고 숫자를 오른쪽에 맞추려면 루프를 다음과 같이 바꿉니다 **`for`** .

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6) << names[i]
         << resetiosflags(ios::left)
         << setw(10) << values[i] << endl;
```

출력은 다음과 같습니다.

```Output
Zoot        1.23
Jimmy      35.36
Al         653.7
Stan     4358.24
```

왼쪽 맞춤 플래그는 `left` 열거자와 함께 [setiosflags](../standard-library/iomanip-functions.md#setiosflags) 조작자를 사용하여 설정됩니다. 이 열거자는 [ios](../standard-library/basic-ios-class.md) 클래스에서 정의되므로 해당 참조에 **ios::** 접두사가 포함되어야 합니다. [resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) 조작자는 왼쪽 맞춤 플래그를 해제합니다. 및와 달리 `width` `setw` 및의 효과 `setiosflags` 는 `resetiosflags` 영구적입니다.

## <a name="precision"></a><a name="vclrfprecisionanchor5"></a> 소수

부동 소수점 전체 자릿수의 기본값은 6입니다. 예를 들어 숫자 3466.9768은 3466.98로 출력됩니다. 이 값이 출력되는 방법을 변경하려면 [setprecision](../standard-library/iomanip-functions.md#setprecision) 조작자를 사용합니다. 조작자에는 [fixed](../standard-library/ios-functions.md#fixed) 및 [scientific](../standard-library/ios-functions.md#scientific)의 두 플래그가 있습니다. [fixed](../standard-library/ios-functions.md#fixed)를 설정하면 숫자가 3466.976800으로 출력됩니다. `scientific`가 설정 된 경우 설정 하면 3.4669773 + 003으로 출력 됩니다.

[맞춤](#vclrfalignmentanchor4) 에 표시 된 부동 소수점 숫자를 유효 자릿수 1 자리로 표시 하려면 다음과 **`for`** 같이 루프를 바꿉니다.

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6)
         << names[i]
         << resetiosflags(ios::left)
         << setw(10)
         << setprecision(1)
         << values[i]
         << endl;
```

이 목록이 다음과 같이 출력됩니다.

```Output
Zoot          1
Jimmy     4e+01
Al        7e+02
Stan      4e+03
```

과학적 표기법을 제거 하려면 루프 앞에이 문을 삽입 합니다 **`for`** .

```cpp
cout << setiosflags(ios::fixed);
```

고정 표기법을 사용할 경우 소수점 이하 1자리로 출력됩니다.

```Output
Zoot         1.2
Jimmy       35.4
Al         653.7
Stan      4358.2
```

플래그를로 변경 하면 `ios::fixed` `ios::scientific` 프로그램에서 다음을 출력 합니다.

```cpp
Zoot    1.2e+00
Jimmy   3.5e+01
Al      6.5e+02
Stan    4.4e+03
```

다시 소수점 이하 1자리로 출력됩니다. 또는 중 `ios::fixed` 하나 `ios::scientific` 를 설정 하면 전체 자릿수 값에 따라 소수점이 하 자릿수가 결정 됩니다. 두 플래그를 모두 설정하지 않으면 전체 자릿수 값에 따라 전체 유효 자릿수가 결정됩니다. `resetiosflags` 조작자는 이러한 플래그를 지웁니다.

## <a name="radix"></a><a name="vclrfradixanchor6"></a> 기 수

`dec`, `oct` 및 조작자는 `hex` 입력 및 출력에 대 한 기본 기 기를 설정 합니다. 예를 들어 조작자를 출력 스트림에 삽입 하는 경우 `hex` 개체가 정수의 내부 데이터 표현을 16 진수 출력 형식으로 올바르게 변환 합니다. [uppercase](../standard-library/ios-functions.md#uppercase) 플래그를 지우면(기본값) 숫자가 소문자 a에서 f까지의 숫자로 표시되고, 그렇지 않으면 대문자로 표시됩니다. 기본 기 수는 `dec` (10 진수)입니다.

## <a name="quoted-strings-c14"></a>따옴표 붙은 문자열(C++14)

스트림에 문자열을 삽입하는 경우 stringstream::str() 멤버 함수를 호출하여 동일한 문자열을 쉽게 다시 검색할 수 있습니다. 그러나 나중에 추출 연산자를 사용하여 새 문자열에 스트림을 삽입하려는 경우 >> 연산자는 기본적으로 첫 번째 공백 문자를 발견할 때 중지되기 때문에 예기치 않은 결과가 발생할 수 있습니다.

```cpp
std::stringstream ss;
std::string inserted = "This is a sentence.";
std::string extracted;

ss << inserted;
ss >> extracted;

std::cout << inserted;     //  This is a sentence.
std::cout << extracted;    //  This
```

이 동작은 수동으로 재정의할 수 있지만, 문자열 왕복을 더 편리하게 만들기 위해 C++14에서는 `std::quoted` 스트림 조작자를 \<iomanip>에 추가합니다. 삽입 시 `quoted()`는 문자열을 구분 기호(기본적으로 큰따옴표 ' " ')로 둘러싸고, 추출 시 스트림을 조작하여 최종 구분 기호가 발견될 때까지 모든 문자를 추출합니다. 포함된 따옴표는 이스케이프 문자(기본적으로 '\\\\')로 이스케이프됩니다.

구분 기호는 stream 개체에만 표시 됩니다. 추출 된 문자열에는 없지만 [basic_stringstream:: str](../standard-library/basic-stringstream-class.md#str)에서 반환 된 문자열에 표시 됩니다.

삽입 및 추출 작업의 공백 동작은 문자열이 코드에서 표현되는 방식에 독립적이므로 따옴표 붙은 연산자는 입력 문자열이 원시 문자열 리터럴인지 또는 일반 문자열인지에 관계없이 유용합니다. 형식에 관계없이 입력 문자열에 포함된 따옴표, 줄 바꿈, 탭 등이 있을 수 있으며, 이러한 모든 항목은 quoted() 조작자에 의해 보존됩니다.

자세한 내용 및 전체 코드 예제는 [따옴표 붙은](../standard-library/iomanip-functions.md#quoted)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[출력 스트림](../standard-library/output-streams.md)
