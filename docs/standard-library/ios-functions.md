---
title: '&lt;ios&gt; 함수 | Microsoft 문서'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- xiosbase/std::defaultfloat
- xiosbase/std::boolalpha
- xiosbase/std::dec
- ios/std::fixed
- ios/std::hex
- ios/std::internal
- ios/std::left
- ios/std::noboolalpha
- ios/std::noshowbase
- ios/std::noshowpoint
- ios/std::noshowpos
- ios/std::noskipws
- ios/std::nounitbuf
- ios/std::nouppercase
- ios/std::oct
- ios/std::right
- ios/std::scientific
- ios/std::showbase
- ios/std::showpoint
- ios/std::showpos
- ios/std::skipws
- ios/std::unitbuf
- ios/std::uppercase
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::internal [C++]
- std::left [C++]
- std::noboolalpha [C++]
- std::noshowbase [C++]
- std::noshowpoint [C++]
- std::noshowpos [C++]
- std::noskipws [C++]
- std::nounitbuf [C++]
- std::nouppercase [C++]
- std::oct [C++]
- std::right [C++]
- std::scientific [C++]
- std::showbase [C++]
- std::showpoint [C++]
- std::showpos [C++]
- std::skipws [C++]
- std::unitbuf [C++]
- std::uppercase [C++]
ms.openlocfilehash: a19d023400179e1e7e16541b7e3d7ef38ad963ba
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101095"
---
# <a name="ltiosgt-functions"></a>&lt;ios&gt; 함수

||||
|-|-|-|
|[defaultfloat](#ios_defaultfloat)|[boolalpha](#boolalpha)|[dec](#dec)|
|[fixed](#fixed)|[hex](#hex)|[internal](#internal)|
|[left](#left)|[noboolalpha](#noboolalpha)|[noshowbase](#noshowbase)|
|[noshowpoint](#noshowpoint)|[noshowpos](#noshowpos)|[noskipws](#noskipws)|
|[nounitbuf](#nounitbuf)|[nouppercase](#nouppercase)|[oct](#oct)|
|[right](#right)|[scientific](#scientific)|[showbase](#showbase)|
|[showpoint](#showpoint)|[showpos](#showpos)|[skipws](#skipws)|
|[unitbuf](#unitbuf)|[uppercase](#uppercase)|

## <a name="boolalpha"></a>  boolalpha

[bool](../cpp/bool-cpp.md) 형식의 변수가 스트림에서 **true** 또는 **false**로 표시되도록 지정합니다.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

기본적으로 형식의 변수가 **bool** 1 또는 0으로 표시 됩니다.

`boolalpha` 효과적으로 호출한 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha`)를 반환 합니다 *str*합니다.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha)는 `boolalpha`의 결과를 되돌립니다.

### <a name="example"></a>예제

```cpp
// ios_boolalpha.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   bool b = true;
   cout << b << endl;
   boolalpha( cout );
   cout << b << endl;
   noboolalpha( cout );
   cout << b << endl;
   cout << boolalpha << b << endl;
}
```

```Output
1
true
1
true
```

## <a name="dec"></a>  dec

정수 변수가 밑수 10 표기법으로 표시되도록 지정합니다.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

기본적으로 정수 변수는 10진으로 표시됩니다.

`dec` 효과적으로 호출한 `str.` [setf](../standard-library/ios-base-class.md#setf)( `ios_base::dec`합니다 `ios_base::basefield`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_dec.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 100;

   cout << i << endl;   // Default is base 10
   cout << hex << i << endl;
   dec( cout );
   cout << i << endl;
   oct( cout );
   cout << i << endl;
   cout << dec << i << endl;
}
```

```Output
100
64
100
144
100
```

## <a name="ios_defaultfloat"></a>  &lt;ios&gt; defaultfloat

부동 소수점 값에 기본 표시 형식을 사용하도록 `ios_base` 개체의 플래그를 구성합니다.

```cpp
ios_base& defaultfloat(ios_base& _Iosbase);
```

### <a name="parameters"></a>매개 변수

*_Iosbase*<br/>
`ios_base` 개체입니다.

### <a name="remarks"></a>설명

조작자는 _I `osbase.`[ios_base::unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`를 효과적으로 호출한 다음 _I `osbase`를 반환합니다.

## <a name="fixed"></a>  fixed

부동 소수점 숫자가 고정 Decimal 표기법으로 표시되도록 지정합니다.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

`fixed` 부동 소수점 숫자에 대 한 기본 표시 표기법입니다. [scientific](../standard-library/ios-functions.md#scientific)은 과학적 표기법을 사용하여 부동 소수점 숫자를 표시하도록 합니다.

조작자 * str.*[setf](../standard-library/ios-base-class.md#setf)( `ios_base::fixed`합니다 `ios_base::floatfield`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_fixed.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 1.1F;

   cout << i << endl;   // fixed is the default
   cout << scientific << i << endl;
   cout.precision( 1 );
   cout << fixed << i << endl;
}
```

```Output
1.1
1.100000e+000
1.1
```

## <a name="hex"></a>  hex

정수 변수가 16진 표기법으로 표시되도록 지정합니다.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

기본적으로 정수 변수는 10진 표기법으로 표시됩니다. [dec](../standard-library/ios-functions.md#dec) 및 [oct](../standard-library/ios-functions.md#oct)도 정수 변수가 표시되는 방식을 변경합니다.

조작자 `str` **.** [setf](../standard-library/ios-base-class.md#setf)( `ios_base::hex`합니다 `ios_base::basefield`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

참조 [dec](../standard-library/ios-functions.md#dec) 사용 하는 방법의 예 `hex`합니다.

## <a name="internal"></a>  internal

숫자의 부호를 왼쪽에 맞추고 숫자를 오른쪽에 맞춥니다.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

개체에 대 한 참조를 *str* 파생 됩니다.

### <a name="remarks"></a>설명

[showpos](../standard-library/ios-functions.md#showpos)는 양수에 대해 부호가 표시되도록 합니다.

조작자는 `str`. [setf](../standard-library/ios-base-class.md#setf)( [ios_base](../standard-library/ios-base-class.md#fmtflags)합니다 [ios_base:: adjustfield](../standard-library/ios-base-class.md#fmtflags))를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_internal.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( void )
{
   using namespace std;
   float i = -123.456F;
   cout.fill( '.' );
   cout << setw( 10 ) << i << endl;
   cout << setw( 10 ) << internal << i << endl;
}
```

```Output
..-123.456
-..123.456
```

## <a name="left"></a>  left

너비가 출력 너비보다 작은 텍스트를 왼쪽에 여백을 두고 스트림 플러시에 표시합니다.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::left`를 `ios_base::adjustfield`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_left.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout.width( 20 );
   cout << f1 << endl;
   cout << left << f1 << endl;
}
```

```Output
                   5
5
```

## <a name="noboolalpha"></a>  noboolalpha

[bool](../cpp/bool-cpp.md) 형식의 변수가 스트림에서 1 또는 0으로 표시되도록 지정합니다.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

기본적으로 `noboolalpha`가 설정되어 있습니다.

`noboolalpha` 효과적으로 호출한 `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::boolalpha`)를 반환 합니다 *str*합니다.

[boolalpha](../standard-library/ios-functions.md#boolalpha)는 `noboolalpha`의 결과를 되돌립니다.

### <a name="example"></a>예제

`noboolalpha` 사용 예제는 [boolalpha](../standard-library/ios-functions.md#boolalpha)를 참조하세요.

## <a name="noshowbase"></a>  noshowbase

숫자가 표시되는 표기법 밑수 표시를 해제합니다.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

`noshowbase`는 기본적으로 설정되어 있습니다. [showbase](../standard-library/ios-functions.md#showbase)를 사용하여 숫자의 표기 기준을 나타냅니다.

조작자 `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showbase`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

`noshowbase`를 사용하는 방법에 대한 예제는 [showbase](../standard-library/ios-functions.md#showbase)를 참조하세요.

## <a name="noshowpoint"></a>  noshowpoint

소수 부분이 0인 부동 소수점 숫자의 정수 부분만 표시합니다.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

`noshowpoint`는 기본적으로 설정되어 있습니다. [showpoint](../standard-library/ios-functions.md#showpoint) 및 [precision](../standard-library/ios-base-class.md#precision)을 사용하여 소수점 뒤에 0을 표시합니다.

조작자 `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showpoint`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_noshowpoint.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.000;
   cout << f1 << endl;   // noshowpoint is default
   cout.precision( 4 );
   cout << showpoint << f1 << endl;
   cout << noshowpoint << f1 << endl;
}
```

```Output
5
5.000
5
```

## <a name="noshowpos"></a>  noshowpos

양수에 명시적으로 부호가 지정되지 않습니다.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

`noshowpos`는 기본적으로 설정되어 있습니다.

조작자 `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showps`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

`noshowpos` 사용 예제는 [showpos](../standard-library/ios-functions.md#showpos)를 참조하세요.

## <a name="noskipws"></a>  noskipws

입력 스트림이 공백을 읽습니다.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

기본적으로 [skipws](../standard-library/ios-functions.md#skipws)가 적용됩니다. 입력 스트림에서 공백을 읽으면 버퍼의 끝을 신호로 보냅니다.

조작자 `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::skipws`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_noskipws.cpp
// compile with: /EHsc
#include <iostream>
#include <string>

int main() {
   using namespace std;
   string s1, s2, s3;
   cout << "Enter three strings: ";
   cin >> noskipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

## <a name="nounitbuf"></a>  nounitbuf

출력이 버퍼링되고 버퍼가 가득 차면 처리되도록 합니다.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

[unitbuf](../standard-library/ios-functions.md#unitbuf)는 버퍼가 비어 있지 않으면 처리되도록 합니다.

조작자 `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::unitbuf`)를 반환 합니다 *str*합니다.

## <a name="nouppercase"></a>  nouppercase

16진수 숫자와 과학적 표기법의 지수가 소문자로 표시되도록 지정합니다.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

조작자 `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::uppercase`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

`nouppercase` 사용 예제는 [uppercase](../standard-library/ios-functions.md#uppercase)를 참조하세요.

## <a name="oct"></a>  oct

정수 변수가 밑수 8 표기법으로 표시되도록 지정합니다.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

개체에 대 한 참조를 *str* 파생 됩니다.

### <a name="remarks"></a>설명

기본적으로 정수 변수는 10진 표기법으로 표시됩니다. [dec](../standard-library/ios-functions.md#dec) 및 [hex](../standard-library/ios-functions.md#hex)도 정수 변수가 표시되는 방식을 변경합니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::oct`를 `ios_base::basefield`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

참조 [dec](../standard-library/ios-functions.md#dec) 사용 하는 방법의 예 `oct`합니다.

## <a name="right"></a>  right

너비가 출력 너비보다 작은 텍스트를 오른쪽에 여백을 두고 스트림 플러시에 표시합니다.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

개체에 대 한 참조를 *str* 파생 됩니다.

### <a name="remarks"></a>설명

[left](../standard-library/ios-functions.md#left)도 텍스트의 양쪽 맞춤을 수정합니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::right`를 `ios_base::adjustfield`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_right.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << left << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << right << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
}
```

```Output
5
                   5
5
5
                   5
                   5
```

## <a name="scientific"></a>  scientific

과학적 표기법을 사용하여 부동 소수점 숫자가 표시되도록 합니다.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

기본적으로 [fixed](../standard-library/ios-functions.md#fixed) 표기법이 부동 소수점 숫자에 적용됩니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::scientific`를 `ios_base::floatfield`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_scientific.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 100.23F;

   cout << i << endl;
   cout << scientific << i << endl;
}
```

```Output
100.23
1.002300e+002
```

## <a name="showbase"></a>  showbase

숫자가 표시되는 표기법 밑수를 표시합니다.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

숫자의 표기 기준은 [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct) 또는 [hex](../standard-library/ios-functions.md#hex)를 사용하여 변경할 수 있습니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::showbase`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_showbase.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int j = 100;

   cout << showbase << j << endl;   // dec is default
   cout << hex << j << showbase << endl;
   cout << oct << j << showbase << endl;

   cout << dec << j << noshowbase << endl;
   cout << hex << j << noshowbase << endl;
   cout << oct << j << noshowbase << endl;
}
```

```Output
100
0x64
0144
100
64
144
```

## <a name="showpoint"></a>  showpoint

소수 부분이 0인 경우에도 부동 소수점 숫자의 정수 부분과 소수점 이하 자릿수를 표시합니다.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

기본적으로 [noshowpoint](../standard-library/ios-functions.md#noshowpoint)가 적용됩니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::showpoint`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

`showpoint` 사용 예제는 [noshowpoint](../standard-library/ios-functions.md#noshowpoint)를 참조하세요.

## <a name="showpos"></a>  showpos

양수에 명시적으로 부호가 지정됩니다.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

[noshowpos](../standard-library/ios-functions.md#noshowpos)가 기본값입니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::showpos`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_showpos.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 1;

   cout << noshowpos << i << endl;   // noshowpos is default
   cout << showpos << i << endl;
}
```

```Output
1
+1
```

## <a name="skipws"></a>  skipws

입력 스트림이 공백을 읽지 않습니다.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

_ *Str*이 파생되는 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

기본적으로 `skipws`가 설정되어 있습니다. [noskipws](../standard-library/ios-functions.md#noskipws)는 입력 스트림에서 공백을 읽도록 합니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( `ios_base::skipws`)를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   char s1, s2, s3;
   cout << "Enter three characters: ";
   cin >> skipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

```Output

1 2 3

```

```Output

      1 2 3.1.
.2.
.3.
```

## <a name="unitbuf"></a>  unitbuf

버퍼가 비어 있지 않으면 출력이 처리됩니다.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

개체에 대 한 참조를 *str* 파생 됩니다.

### <a name="remarks"></a>설명

`endl`도 버퍼를 플러시합니다.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf)가 기본적으로 적용됩니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( [ios_base:: unitbuf](../standard-library/ios-base-class.md#fmtflags))를 반환 합니다 *str*합니다.

## <a name="uppercase"></a>  uppercase

16진수 숫자와 과학적 표기법의 지수가 대문자로 표시되도록 지정합니다.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
[ios_base](../standard-library/ios-base-class.md) 형식의 개체에 대한 참조 또는 `ios_base`에서 상속되는 형식입니다.

### <a name="return-value"></a>반환 값

개체에 대 한 참조를 *str* 파생 됩니다.

### <a name="remarks"></a>설명

기본적으로 [nouppercase](../standard-library/ios-functions.md#nouppercase)가 적용됩니다.

조작자 `str`.[ setf](../standard-library/ios-base-class.md#setf)( [ios_base:: uppercase](../standard-library/ios-base-class.md#fmtflags))를 반환 합니다 *str*합니다.

### <a name="example"></a>예제

```cpp
// ios_uppercase.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
   using namespace std;

   double i = 1.23e100;
   cout << i << endl;
   cout << uppercase << i << endl;

   int j = 10;
   cout << hex << nouppercase << j << endl;
   cout << hex << uppercase << j << endl;
}
```

```Output
1.23e+100
1.23E+100
a
A
```

## <a name="see-also"></a>참고자료

[\<ios>](../standard-library/ios.md)<br/>
