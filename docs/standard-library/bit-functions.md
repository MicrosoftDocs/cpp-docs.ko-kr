---
title: '&lt;비트 &gt; 함수'
description: 개별 비트 및 비트 시퀀스에 액세스, 조작 및 처리 하는 함수
ms.date: 08/28/2020
f1_keywords:
- bit/std::bit_cast
- bit/std::has_single_bit
- bit/std::bit_ceil
- bit/std::bit_floor
- bit/std::bit_width
- bit/std::rotl
- bit/std::rotr
- bit/std::countl_zero
- bit/std::countl_one
- bit/std::countr_zero
- bit/std::countr_one
- bit/std::popcount
helpviewer_keywords:
- std::bit [C++], bit_cast
- std::bit [C++], has_single_bit
- std::bit [C++], bit_ceil
- std::bit [C++], bit_floor
- std::bit [C++], bit_width
- std::bit [C++], rotl
- std::bit [C++], rotr
- std::bit [C++], countl_zero
- std::bit [C++], countl_one
- std::bit [C++], countr_zero
- std::bit [C++], countr_one
- std::bit [C++], popcount
ms.openlocfilehash: f06e181a4fe6683adb0cc63c016cbd879f2fc574
ms.sourcegitcommit: e58918c45316d799c1952ca7797a85adbcd0c472
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89281811"
---
# <a name="ltbitgt-functions"></a>&lt;비트 &gt; 함수

헤더에는 \<bit> 다음과 같은 멤버 이외의 템플릿 함수가 포함 되어 있습니다.

| **멤버가 아닌 함수** | **설명** |
|--------|---------|
|[bit_cast](#bit_cast) | 개체 표현을 한 형식에서 다른 형식으로 다시 해석 합니다. |
|[bit_ceil](#bit_ceil) | 값 보다 크거나 같은 2의 가장 작은 거듭제곱을 찾습니다. |
|[bit_floor](#bit_floor) | 값 보다 크지 않은 2의 최대 거듭제곱을 찾습니다. |
|[bit_width](#bit_width) | 값을 나타내는 데 필요한 최소 비트 수를 찾습니다. |
|[countl_zero](#countl_zero) | 가장 중요 한 비트에서 시작 하 여 0으로 설정 된 연속 비트 수를 계산 합니다. |
|[countl_one](#countl_one) | 가장 중요 한 비트에서 시작 하 여 1로 설정 된 연속 비트 수를 계산 합니다. |
|[countr_zero](#countr_zero) | 최하위 비트에서 시작 하 여 0으로 설정 된 연속 비트 수를 계산 합니다. |
|[countr_one](#countl_one) | 최하위 비트에서 시작 하 여 1로 설정 된 연속 비트 수를 계산 합니다. |
|[has_single_bit](#has_single_bit) | 값에 1 비트만 설정 되어 있는지 확인 합니다. 이는 값이 2의 거듭제곱 인지 여부를 테스트 하는 것과 같습니다. |
|[popcount](#popcount) | 1로 설정 된 비트 수를 계산 합니다. |
|[rotl](#rotl) | 비트 왼쪽 회전의 결과를 계산 합니다. |
|[rotr](#rotr) | 비트 오른쪽 회전의 결과를 계산 합니다. |

## <a name="bit_cast"></a>`bit_cast`

형식의 개체에서 형식의 새 개체로 비트 패턴을 복사 `From` `To` 합니다.

```cpp
template <class To, class From>
[[nodiscard]] constexpr To bit_cast(const From& from) noexcept;
```

### <a name="parameters"></a>매개 변수

*받는 사람*\
출력의 형식입니다.

*보낸 사람*\
변환할 값의 형식입니다.

*보낸 사람*\
변환할 값입니다.

### <a name="return-value"></a>반환 값

`To` 형식의 개체입니다.

의 패딩 비트가 없는 경우 결과의 각 비트는의 해당 비트와 일치 `from` `To` 합니다 .이 경우 결과의 비트는 지정 되지 않습니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <iostream>

int main()
{
    float f = std::numeric_limits<float>::infinity();
    int i = std::bit_cast<int>(f);
    std::cout << "float f = " << std::hex << f
              << "\nstd::bit_cat<int>(f) = " << std::hex << i << '\n';
    return 0;
}
```

```Output
float f = inf
std::bit_cat<int>(f) = 7f800000
```

### <a name="remarks"></a>설명

하위 수준 코드는 한 형식의 개체를 다른 형식으로 해석 해야 하는 경우가 많습니다. 다시 해석 개체는 원래와 동일한 비트 표현을 갖지만 다른 형식입니다.

대신 `reinterpret_cast` , 또는를 사용 하는 `memcpy()` 것이 `bit_cast()` 이러한 변환을 수행 하는 더 좋은 방법입니다. 다음 이유 때문에 더 좋습니다.
- `bit_cast()`가 `constexpr`인 경우
- `bit_cast()` 형식은 일반적으로 복사할 수 및 동일한 크기 여야 합니다. 이렇게 하면를 사용 하 여 발생할 수 있는 잠재적인 문제를 방지 하 `reinterpret_cast` `memcpy` 고, 실수로 일반적으로 복사할 수 없는 형식을 변환 하는 데 사용할 수 있기 때문입니다. 또한 `memcpy()` 는 크기가 다른 형식 간에 실수로 복사 하는 데 사용할 수 있습니다. 예를 들어 부호 없는 int (4 바이트) 또는 그 밖의 다른 방법으로 double (8 바이트)을 사용할 수 있습니다.

이 오버 로드는 다음과 같은 경우에만 오버 로드 확인에 참여 합니다.
-  `sizeof(To) == sizeof(From)`
- `To` 및 `From` 가 [is_trivially_copyable](https://docs.microsoft.com/cpp/standard-library/is-trivially-copyable-class?view=vs-2019`)됩니다.

이 함수 템플릿은 `constexpr` , 및 인 경우에만입니다 `To` `From` .
- 공용 구조체 또는 포인터 형식이 아닙니다.
- 멤버 형식에 대 한 포인터가 아닙니다.
- volatile 한정 안 함
- 참조 형식인 비정적 데이터 멤버가 없습니다.

## <a name="bit_ceil"></a>`bit_ceil`

값 보다 크거나 같은 2의 가장 작은 거듭제곱을 찾습니다. 예를 들어, 지정 된 `3` 는를 반환 `4` 합니다.

```cpp
template<class T>
[[nodiscard]] constexpr T bit_ceil(T value);
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

 보다 크거나 같은 2의 최소 거듭제곱입니다 `value` .

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_ceil() takes an unsigned integer type
    {
        auto nextClosestPowerOf2 = std::bit_ceil(i);
        std::cout << "\nbit_ceil(0b" << std::bitset<4>(i) << ") = "
                  << "0b" << std::bitset<4>(nextClosestPowerOf2);
    }
    return 0;
}
```

```Output
bit_ceil(0b0000) = 0b0001
bit_ceil(0b0001) = 0b0001
bit_ceil(0b0010) = 0b0010
bit_ceil(0b0011) = 0b0100
bit_ceil(0b0100) = 0b0100
bit_ceil(0b0101) = 0b1000
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="bit_floor"></a>`bit_floor`

값 보다 크지 않은 2의 최대 거듭제곱을 찾습니다. 예를 들어, 지정 된 `5` 는를 반환 `4` 합니다.

```cpp
template< class T >
[[nodiscard]] constexpr T bit_floor(T value) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

보다 크지 않은 2의 가장 큰 거듭제곱 `value`
`value`가 0 이면는 0을 반환 합니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_floor() takes an unsigned integer type
    {
        auto previousPowerOf2 = std::bit_floor(i);
        std::cout << "\nbit_floor(0b" << std::bitset<4>(i) << ") = 0b"
                  << std::bitset<4>(previousPowerOf2);
    }
    return 0;
}
```

```Output
bit_floor(0b0000) = 0b0000
bit_floor(0b0001) = 0b0001
bit_floor(0b0010) = 0b0010
bit_floor(0b0011) = 0b0010
bit_floor(0b0100) = 0b0100
bit_floor(0b0101) = 0b0100
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="bit_width"></a>`bit_width`

값을 나타내는 데 필요한 최소 비트 수를 찾습니다.

예를 들어 지정 된 5 (0b101)는 3 개의 이진 비트를 사용 하 여 값 5를 표현 하기 때문에 3을 반환 합니다.

```cpp
template<class T>
[[nodiscard]] constexpr T bit_width(T value) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

나타내는 데 필요한 비트 수 `value` 입니다.
`value`가 0 이면는 0을 반환 합니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <iostream>

int main()
{
    for (unsigned i=0u; i <= 8u; ++i)
    {
        std::cout << "\nbit_width(" << i << ") = "
                  << std::bit_width(i);
    }
    return 0;
}
```

```Output
bit_width(0) = 0
bit_width(1) = 1
bit_width(2) = 2
bit_width(3) = 2
bit_width(4) = 3
bit_width(5) = 3
bit_width(6) = 3
bit_width(7) = 3
bit_width(8) = 4
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="countl_zero"></a>`countl_zero`

가장 중요 한 비트에서 시작 하 여 0으로 설정 된 연속 비트 수를 계산 합니다.

```cpp
template<class T>
[[nodiscard]] constexpr int countl_zero(T value) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

가장 중요 한 비트부터 시작 하 여 연속 제로 비트 수입니다.
`value`가 0 이면 형식의 비트 수입니다 `value` .

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountl_zero(0b" << std::bitset<8>(result) << ") = " << std::countl_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countl_zero(0b00000000) = 8
countl_zero(0b00000001) = 7
countl_zero(0b00000010) = 6
countl_zero(0b00000100) = 5
countl_zero(0b00001000) = 4
countl_zero(0b00010000) = 3
countl_zero(0b00100000) = 2
countl_zero(0b01000000) = 1
countl_zero(0b10000000) = 0
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="countl_one"></a>`countl_one`

가장 중요 한 비트에서 시작 하 여 1로 설정 된 연속 비트 수를 계산 합니다.

```cpp
template<class T>
[[nodiscard]] constexpr int countl_one(T value) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

가장 중요 한 비트에서 시작 하 여 1로 설정 된 연속 비트 수입니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (unsigned char bit = 128; bit > 0; bit /= 2)
    {
        value |= bit;
        std::cout << "\ncountl_one(0b" << std::bitset<8>(value) << ") = "
                  << std::countl_one(value);
    }
    return 0;
}
```

```Output
countl_one(0b10000000) = 1
countl_one(0b11000000) = 2
countl_one(0b11100000) = 3
countl_one(0b11110000) = 4
countl_one(0b11111000) = 5
countl_one(0b11111100) = 6
countl_one(0b11111110) = 7
countl_one(0b11111111) = 8
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="countr_zero"></a>`countr_zero`

최하위 비트에서 시작 하 여 0으로 설정 된 연속 비트 수를 계산 합니다.

```cpp
template<class T>
[[nodiscard]] constexpr int countr_zero(T value) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

최하위 비트부터 시작 하 여 연속 제로 비트 수입니다.
`value`가 0 이면 형식의 비트 수입니다 `value` .

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountr_zero(0b" << std::bitset<8>(result) << ") = "
                  << std::countr_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countr_zero(0b00000000) = 8
countr_zero(0b00000001) = 0
countr_zero(0b00000010) = 1
countr_zero(0b00000100) = 2
countr_zero(0b00001000) = 3
countr_zero(0b00010000) = 4
countr_zero(0b00100000) = 5
countr_zero(0b01000000) = 6
countr_zero(0b10000000) = 7
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="countr_one"></a>`countr_one`

최하위 비트에서 시작 하 여 1로 설정 된 연속 비트 수를 계산 합니다.

```cpp
template<class T>
[[nodiscard]] constexpr int countr_one(T value) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

최하위 비트에서 시작 하 여 1로 설정 된 연속 비트 수입니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (int bit = 1; bit <= 128; bit *= 2)
    {
        value |= bit;
        std::cout << "\ncountr_one(0b" << std::bitset<8>(value) << ") = "
                  << std::countr_one(value);
    }
    return 0;
}
```

```Output
countr_one(0b00000001) = 1
countr_one(0b00000011) = 2
countr_one(0b00000111) = 3
countr_one(0b00001111) = 4
countr_one(0b00011111) = 5
countr_one(0b00111111) = 6
countr_one(0b01111111) = 7
countr_one(0b11111111) = 8
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="has_single_bit"></a>`has_single_bit`

값에 한 비트만 설정 되었는지 확인 합니다. 이는 값이 2의 거듭제곱 인지 여부를 테스트 하는 것과 같습니다.
 
```cpp
template <class T>
[[nodiscard]] constexpr bool has_single_bit(T value) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

`true``value`에 하나의 비트 집합만 있는 경우 `value` 가 2의 거듭제곱을 의미 합니다. 그렇지 않으면 `false`입니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>
#include <iomanip>

int main()
{
    for (auto i = 0u; i < 10u; ++i)
    {
        std::cout << "has_single_bit(0b" << std::bitset<4>(i) << ") = "
                  << std::boolalpha << std::has_single_bit(i) << '\n';
    }
    return 0;
}
```

```Output
has_single_bit(0b0000) = false
has_single_bit(0b0001) = true
has_single_bit(0b0010) = true
has_single_bit(0b0011) = false
has_single_bit(0b0100) = true
has_single_bit(0b0101) = false
has_single_bit(0b0110) = false
has_single_bit(0b0111) = false
has_single_bit(0b1000) = true
has_single_bit(0b1001) = false
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="popcount"></a>`popcount`

부호 없는 정수 값에서 1로 설정 된 비트 수를 계산 합니다.
 
```cpp
template<class T>
[[nodiscard]] constexpr int popcount(T value) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
테스트할 부호 없는 정수 값입니다.

### <a name="return-value"></a>반환 값

에서 1로 설정 된 숫자 비트 `value` 입니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
   for (unsigned char value = 0; value < 16; value++)
    {
        std::cout << "\npopcount(0b" << std::bitset<4>(value) << ") = "
                  << std::popcount(value);
    }
    return 0;
}
```

```Output
popcount(0b0000) = 0
popcount(0b0001) = 1
popcount(0b0010) = 1
popcount(0b0011) = 2
popcount(0b0100) = 1
popcount(0b0101) = 2
popcount(0b0110) = 2
popcount(0b0111) = 3
popcount(0b1000) = 1
popcount(0b1001) = 2
popcount(0b1010) = 2
popcount(0b1011) = 3
popcount(0b1100) = 2
popcount(0b1101) = 3
popcount(0b1110) = 3
popcount(0b1111) = 4
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="rotl"></a>`rotl`

부호 없는 정수 값의 비트를 지정 된 횟수 만큼 왼쪽으로 회전 합니다. 가장 왼쪽 비트의 "축소" 비트가 가장 오른쪽 비트로 회전 합니다.
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotl(T value, int s) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
회전할 부호 없는 정수 값입니다.

*삭제*\
수행할 왼쪽 회전의 수입니다.

### <a name="return-value"></a>반환 값

왼쪽으로 회전 한 결과 `value` `s` 입니다.
`s`가 0 이면를 반환 `value` 합니다.
`s`가 음수 이면는를 수행 `rotr(value, -s)` 합니다. 가장 오른쪽 비트의 ' out ' 비트가 가장 왼쪽 비트로 회전 됩니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 1;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotl(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotl(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotl(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotl(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotl(0b00000001, 1) = 0b00000010
rotl(0b00000010, 1) = 0b00000100
rotl(0b00000100, 1) = 0b00001000
rotl(0b00001000, 1) = 0b00010000
rotl(0b00010000, 1) = 0b00100000
rotl(0b00100000, 1) = 0b01000000
rotl(0b01000000, 1) = 0b10000000
rotl(0b10000000, 1) = 0b00000001
rotl(0b00000001,-1) = 0b10000000
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="rotr"></a>`rotr`

오른쪽의 비트를 `value` 지정 된 횟수 만큼 회전 합니다. 가장 오른쪽 비트의 ' out ' 비트가 맨 왼쪽으로 다시 회전 됩니다.
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotr(T value, int s) noexcept;
```

### <a name="parameters"></a>매개 변수

*기본값*\
회전할 부호 없는 정수 값입니다.

*삭제*\
수행할 오른쪽 회전의 수입니다.

### <a name="return-value"></a>반환 값

오른쪽으로 회전 한 결과 `value` `s` 입니다. \
`s`가 0 이면를 반환 `value` 합니다.
`s`가 음수 이면는를 수행 `rotl(value, -s)` 합니다. 맨 왼쪽 비트의 ' 제어 ' 비트가 가장 오른쪽 비트로 회전 합니다.

### <a name="example"></a>예

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 128;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotr(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotr(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotr(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotr(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotr(0b10000000, 1) = 0b01000000
rotr(0b01000000, 1) = 0b00100000
rotr(0b00100000, 1) = 0b00010000
rotr(0b00010000, 1) = 0b00001000
rotr(0b00001000, 1) = 0b00000100
rotr(0b00000100, 1) = 0b00000010
rotr(0b00000010, 1) = 0b00000001
rotr(0b00000001, 1) = 0b10000000
rotr(0b10000000,-1) = 0b00000001
```

### <a name="remarks"></a>설명

이 템플릿 함수 `T` 는가 부호 없는 정수 형식인 경우에만 오버 로드 확인에 참여 합니다. 예를 들면 `unsigned int` ,,, `unsigned long` `unsigned short` `unsigned char` 등입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<bit>

**네임스페이스:** std

`/std:c++latest` 필수

## <a name="see-also"></a>참고 항목

[\<bit>](bit.md)