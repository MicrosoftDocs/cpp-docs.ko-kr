---
title: '&lt;ios&gt; 형식 정의'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 20bffbeb7720274302633c5dda9e6364c06d5b54
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424688"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; 형식 정의

## <a name="ios"></a>io

이전 iostream 라이브러리의 ios 클래스를 지원합니다.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>설명

이 형식은 기본 문자 특성을 포함 하는 **char** 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_ios](../standard-library/basic-ios-class.md)의 동의어입니다.

## <a name="streamoff"></a>streamoff

내부 작업을 지원합니다.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>설명

이 형식은 다양한 스트림 위치 지정 작업과 관련된 바이트 오프셋을 저장할 수 있는 개체를 설명하는 부호 있는 정수입니다. 해당 표현에는 32개 이상의 값 비트가 있습니다. 스트림 내에서 임의의 바이트 위치를 나타낼 만큼 충분히 크지 않아도 됩니다. 값 `streamoff(-1)` 일반적으로 잘못 된 오프셋을 나타냅니다.

## <a name="streampos"></a>streampos

버퍼 포인터 또는 파일 포인터의 현재 위치를 보유합니다.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>설명

이 형식은 [fpos](../standard-library/fpos-class.md)< `mbstate_t`>의 동의어입니다.

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
   cout << y << endl;
}
```

```Output
7
```

## <a name="streamsize"></a>  streamsize

스트림의 크기를 지정합니다.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>설명

이 형식은 다양한 스트림 작업과 관련된 요소의 개수를 저장할 수 있는 개체를 설명하는 부호 있는 정수입니다. 해당 표현에는 16개 이상의 비트가 있습니다. 스트림 내에서 임의의 바이트 위치를 나타낼 만큼 충분히 크지 않아도 됩니다.

### <a name="example"></a>예제

다음 프로그램을 컴파일하고 실행한 후 test.txt 파일에서 `streamsize` 설정의 결과를 확인합니다.

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

## <a name="wios"></a>  wios

이전 iostream 라이브러리의 wios 클래스를 지원합니다.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>설명

이 형식은 기본 문자 특성을 사용 하 여 **wchar_t** 형식의 요소에 대해 특수화 된 클래스 템플릿 [basic_ios](../standard-library/basic-ios-class.md)의 동의어입니다.

## <a name="wstreampos"></a>wstreampos

버퍼 포인터 또는 파일 포인터의 현재 위치를 보유합니다.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>설명

이 형식은 [fpos](../standard-library/fpos-class.md)< `mbstate_t`>의 동의어입니다.

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
   cout << y << endl;
}
```

```Output
7
```
