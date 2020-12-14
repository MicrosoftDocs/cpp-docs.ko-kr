---
description: '다음에 대 한 자세한 정보: fpos 클래스'
title: fpos 클래스
ms.date: 03/27/2019
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
ms.openlocfilehash: 22b9a5e69b179ef4206a0664b51b92cc55d4320d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232332"
---
# <a name="fpos-class"></a>fpos 클래스

클래스 템플릿은 임의의 스트림 내에서 임의 파일 위치 표시기를 복원 하는 데 필요한 모든 정보를 저장할 수 있는 개체를 설명 합니다. Fpos 클래스의 개체는 \< **St**> 두 개 이상의 멤버 개체를 효과적으로 저장 합니다.

- [streamoff](../standard-library/ios-typedefs.md#streamoff) 형식의 바이트 오프셋

- 형식의 basic_filebuf 클래스 개체에서 사용 하는 변환 상태 (일반적으로)입니다 `St` `mbstate_t` .

[basic_filebuf](../standard-library/basic-filebuf-class.md) 클래스의 개체에서 사용하기 위한 `fpos_t` 형식의 임의 파일 위치를 저장할 수도 있습니다. 그러나 파일 크기가 제한된 환경에서는 `streamoff`와 `fpos_t`를 바꿔서 사용할 수 있는 경우도 있습니다. 상태 종속적 인코딩을 포함하는 스트림이 없는 환경에서는 `mbstate_t`가 실제로 사용되지 않을 수 있습니다. 따라서 저장되는 멤버 개체 수는 경우에 따라 다를 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>매개 변수

*Statetype*\
상태 정보입니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[fpos](#fpos)|스트림 내의 위치(오프셋)에 대한 정보를 포함하는 개체를 만듭니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[seekpos](#seekpos)|C++ 표준 라이브러리에서만 내부적으로 사용됩니다. 사용자 코드에서 이 메서드를 호출하지 마세요.|
|[state](#state)|변환 상태를 설정하거나 반환합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자! =](#op_neq)|파일 위치 표시기가 같지 않은지 테스트합니다.|
|[연산자 +](#op_add)|파일 위치 표시기를 증가시킵니다.|
|[operator + =](#op_add_eq)|파일 위치 표시기를 증가시킵니다.|
|[연산자](#operator-)|파일 위치 표시기를 감소시킵니다.|
|[연산자-=](#operator-_eq)|파일 위치 표시기를 감소시킵니다.|
|[연산자 = =](#op_eq_eq)|파일 위치 표시기가 같은지 테스트합니다.|
|[operator streamoff](#op_streamoff)|`fpos` 형식의 개체를 `streamoff` 형식의 개체로 캐스팅합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<ios>

**네임스페이스:** std

## <a name="fposfpos"></a><a name="fpos"></a> fpos:: fpos

스트림 내의 위치(오프셋)에 대한 정보를 포함하는 개체를 만듭니다.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>매개 변수

*_Off*\
스트림에 대한 오프셋입니다.

*_State*\
`fpos` 개체의 시작 상태입니다.

*_Filepos*\
스트림에 대한 오프셋입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 파일의 시작과 초기 변환 상태 (해당 하는 경우)를 기준으로 하는 오프셋 *_Off* 저장 합니다. *_Off* -1 인 경우 결과 개체는 잘못 된 스트림 위치를 나타냅니다.

두 번째 생성자는 0 오프셋과 *_State* 개체를 저장 합니다.

## <a name="fposoperator"></a><a name="op_neq"></a> fpos:: operator! =

파일 위치 표시기가 같지 않은지 테스트합니다.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 파일 위치 표시기입니다.

### <a name="return-value"></a>반환 값

**`true`** 파일 위치 표시기가 같지 않으면이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

멤버 함수는 `!(*this == right)`를 반환합니다.

### <a name="example"></a>예제

```cpp
// fpos_op_neq.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;

   fpos<int> pos1, pos2;
   ifstream file;
   char c;

   // Compare two fpos object
   if ( pos1 != pos2 )
      cout << "File position pos1 and pos2 are not equal" << endl;
   else
      cout << "File position pos1 and pos2 are equal" << endl;

   file.open( "fpos_op_neq.txt" );
   file.seekg( 0 );   // Goes to a zero-based position in the file
   pos1 = file.tellg( );
   file.get( c);
   cout << c << endl;

   // Increment pos1
   pos1 += 1;
   file.get( c );
   cout << c << endl;

   pos1 = file.tellg( ) - fpos<int>( 2);
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   // Increment pos1
   pos1 = pos1 + fpos<int>( 1 );
   file.get(c);
   cout << c << endl;

   pos1 -= fpos<int>( 2 );
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   file.close( );
}
```

## <a name="fposoperator"></a><a name="op_add"></a> fpos:: operator +

파일 위치 표시기를 증가시킵니다.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>매개 변수

*_Off*\
파일 위치 표시기를 증분시킬 기준 오프셋입니다.

### <a name="return-value"></a>반환 값

파일 내 위치입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 **fpos(\*this) +=** `_Off`를 반환합니다.

### <a name="example"></a>예제

`operator+` 사용에 대한 샘플은 [operator!=](#op_neq)을 참조하세요.

## <a name="fposoperator"></a><a name="op_add_eq"></a> fpos:: operator + =

파일 위치 표시기를 증가시킵니다.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>매개 변수

*_Off*\
파일 위치 표시기를 증분시킬 기준 오프셋입니다.

### <a name="return-value"></a>반환 값

파일 내 위치입니다.

### <a name="remarks"></a>설명

멤버 함수는 저장 된 오프셋 멤버 개체에 *_Off* 을 추가한 다음 **\* 이** 를 반환 합니다. 파일 내 위치를 지정할 경우 결과는 일반적으로 상태 종속적 인코딩이 없는 이진 스트림의 경우에만 유효합니다.

### <a name="example"></a>예제

`operator+=` 사용에 대한 샘플은 [operator!=](#op_neq)을 참조하세요.

## <a name="fposoperator-"></a><a name="operator-"></a> fpos:: operator-

파일 위치 표시기를 감소시킵니다.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
파일 위치입니다.

*_Off*\
스트림 오프셋입니다.

### <a name="return-value"></a>반환 값

첫 번째 멤버 함수는 `(streamoff)*this - (streamoff) right`을 반환합니다. 두 번째 멤버 함수는 `fpos(*this) -= _Off`를 반환합니다.

### <a name="example"></a>예제

`operator-` 사용에 대한 샘플은 [operator!=](#op_neq)을 참조하세요.

## <a name="fposoperator-"></a><a name="operator-_eq"></a> fpos:: operator-=

파일 위치 표시기를 감소시킵니다.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>매개 변수

*_Off*\
스트림 오프셋입니다.

### <a name="return-value"></a>반환 값

멤버 함수는 `fpos(*this) -= _Off`를 반환합니다.

### <a name="remarks"></a>설명

파일 내 위치를 지정할 경우 결과는 일반적으로 상태 종속적 인코딩이 없는 이진 스트림의 경우에만 유효합니다.

### <a name="example"></a>예제

`operator-=` 사용에 대한 샘플은 [operator!=](#op_neq)을 참조하세요.

## <a name="fposoperator"></a><a name="op_eq_eq"></a> fpos:: operator = =

파일 위치 표시기가 같은지 테스트합니다.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
비교할 파일 위치 표시기입니다.

### <a name="return-value"></a>반환 값

**`true`** 파일 위치 표시기가 같으면이 고, 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

멤버 함수는 `(streamoff)*this == (streamoff)right`를 반환합니다.

### <a name="example"></a>예제

`operator+=` 사용에 대한 샘플은 [operator!=](#op_neq)을 참조하세요.

## <a name="fposoperator-streamoff"></a><a name="op_streamoff"></a> fpos:: operator streamoff

`fpos` 형식 개체를 `streamoff` 형식 개체로 캐스트합니다.

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>설명

이 멤버 함수는 저장된 오프셋 멤버 개체와 `fpos_t` 멤버 개체의 일부로 저장된 모든 추가 오프셋을 반환합니다.

### <a name="example"></a>예제

```cpp
// fpos_op_streampos.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   streamoff s;
   ofstream file( "rdbuf.txt");

   fpos<mbstate_t> f = file.tellp( );
   // Is equivalent to ..
   // streampos f = file.tellp( );
   s = f;
   cout << s << endl;
}
```

```Output
0
```

## <a name="fposseekpos"></a><a name="seekpos"></a> fpos:: seekpos

이 메서드는 C++ 표준 라이브러리에서만 내부적으로 사용됩니다. 사용자 코드에서 이 메서드를 호출하지 마세요.

```cpp
fpos_t seekpos() const;
```

## <a name="fposstate"></a><a name="state"></a> fpos:: 상태

변환 상태를 설정하거나 반환합니다.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>매개 변수

*_State*\
새로운 변환 상태입니다.

### <a name="return-value"></a>반환 값

변환 상태입니다.

### <a name="remarks"></a>설명

첫 번째 멤버 함수는 멤버 개체에 저장 된 값을 반환 합니다 `St` . 두 번째 멤버 함수는 멤버 개체에 *_State* 을 저장 합니다 `St` .

### <a name="example"></a>예제

```cpp
// fpos_state.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main() {
   using namespace std;
   streamoff s;
   ifstream file( "fpos_state.txt" );

   fpos<mbstate_t> f = file.tellg( );
   char ch;
   while ( !file.eof( ) )
      file.get( ch );
   s = f;
   cout << f.state( ) << endl;
   f.state( 9 );
   cout << f.state( ) << endl;
}
```

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
