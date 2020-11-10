---
title: '`<ios>` 형식 정의'
description: '`<ios>`이전 라이브러리의 클래스를 지 원하는 STL (c + + 표준 템플릿 라이브러리) 형식 정의에 대해 설명 합니다 `ios` `iostream` .'
ms.date: 11/06/2020
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.openlocfilehash: b9dbed64c88a00f5ca065e23c4af2f3922634ece
ms.sourcegitcommit: b38485bb3a9d479e0c5d64ffc3d841fa2c2b366f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441270"
---
# <a name="ios-typedefs"></a>`<ios>` 형식 정의

## `ios`

`ios`이전 라이브러리의 클래스를 지원 `iostream` 합니다.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>설명

형식은 [`basic_ios`](../standard-library/basic-ios-class.md) **`char`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿의 동의어입니다.

## `streamoff`

내부 작업을 지원합니다.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>설명

형식이 부호 있는 정수입니다. 스트림 위치 지정 작업에서 바이트 오프셋을 저장할 수 있는 개체에 대해 설명 합니다. 해당 표현에는 32개 이상의 값 비트가 있습니다. 스트림 내에서 임의 바이트 위치를 나타낼 만큼 충분히 크지는 않습니다. 값은 `streamoff(-1)` 일반적으로 잘못 된 오프셋을 나타냅니다.

## `streampos`

버퍼 포인터 또는 파일 포인터의 현재 위치를 보유합니다.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>설명

형식은>의 동의어입니다 [`fpos`](../standard-library/fpos-class.md) <  `mbstate_t` .

### <a name="example"></a>예제

```cpp
// ios_streampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ofstream x( "iostream.txt" );
   x << "testing";
   streampos y = x.tellp( );
   cout << streamoff( y ) << '\n';
}
```

```Output
7
```

## `streamsize`

스트림의 크기를 지정합니다.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>설명

이 형식은 다양한 스트림 작업과 관련된 요소의 개수를 저장할 수 있는 개체를 설명하는 부호 있는 정수입니다. 해당 표현에는 16개 이상의 비트가 있습니다. 스트림 내에서 임의 바이트 위치를 나타낼 만큼 충분히 크지는 않습니다.

### <a name="example"></a>예제

다음 프로그램을 컴파일하고 실행 한 후 파일을 확인 하 여 `test.txt` 설정의 효과를 확인 `streamsize` 합니다.

```cpp
// ios_streamsize.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   char a[16] = "any such text";
   ofstream x( "test.txt" );
   streamsize y = 6;
   x.write( a, y );
}
```

## `wios`

`wios`이전 라이브러리의 클래스를 지원 `iostream` 합니다.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>설명

형식은 [`basic_ios`](../standard-library/basic-ios-class.md) **`wchar_t`** 기본 문자 특성을 포함 하는 형식의 요소에 대해 특수화 된 클래스 템플릿의 동의어입니다.

## `wstreampos`

버퍼 포인터 또는 파일 포인터의 현재 위치를 보유합니다.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>설명

형식은>의 동의어입니다 [`fpos`](../standard-library/fpos-class.md) <  `mbstate_t` .

### <a name="example"></a>예제

```cpp
// ios_wstreampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   wofstream xw( "wiostream.txt" );
   xw << L"testing";
   wstreampos y = xw.tellp( );
   cout << streamoff( y ) << '\n';
}
```

```Output
7
```
