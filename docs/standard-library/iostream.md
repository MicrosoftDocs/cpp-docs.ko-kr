---
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 18d6a8517d71cfa9c7e17a45c97f77977ec778f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385143"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

표준 스트림에서 읽기 및 쓰기를 제어하는 개체를 선언합니다. 대체로 C++ 프로그램에서 입력 및 출력을 수행하기 위해 포함해야 하는 유일한 헤더입니다.

## <a name="syntax"></a>구문

```cpp
#include <iostream>
```

## <a name="remarks"></a>설명

개체는 다음 두 그룹으로 나뉩니다.

- [cin](#cin), [cout](#cout), [cerr](#cerr) 및 [clog](#clog)는 바이트 지향적이며 일반적인 바이트 단위 전송을 수행합니다.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr) 및 [wclog](#wclog)는 와이드 지향적이며, 프로그램에서 내부적으로 조작하는 와이드 문자로/에서 변환을 수행합니다.

표준 입력과 같은 스트림에서 특정 작업을 수행한 후에는 동일한 스트림에서 다른 방향의 작업을 수행할 수 없습니다. 따라서 예를 들어 프로그램이 [cin](#cin) 및 [wcin](#wcin) 둘 다에서 구분 없이 작동할 수 없습니다.

이 헤더에서 선언된 모든 개체는 특이한 속성을 공유합니다. 이러한 개체는 \<iostream>을 포함하는 변환 단위에서 정의된 정적 개체 앞에 생성된다고 가정할 수 있습니다. 마찬가지로, 정의한 해당 정적 개체에 대한 소멸자 이전에 이러한 개체가 제거되지 않는다고 가정할 수 있습니다. 그러나 출력 스트림은 프로그램 종료 중에 플러시됩니다. 따라서 프로그램 시작 전과 프로그램 종료 후에 안전하게 표준 스트림에서 읽거나 쓸 수 있습니다.

그러나 이 보장은 범용이 아닙니다. 정적 생성자는 다른 변환 단위에서 함수를 호출할 수 있습니다. 호출된 함수는 변환 단위가 정적 구성에 참여하는 불확실한 순서를 감안할 때 이 헤더에 선언된 개체가 생성되었다고 가정할 수 없습니다. 이러한 컨텍스트에서 해당 개체를 사용하려면 먼저 [ios_base::Init](../standard-library/ios-base-class.md#init) 클래스의 개체를 생성해야 합니다.

### <a name="global-stream-objects"></a>전역 스트림 개체

|||
|-|-|
|[cerr](#cerr)|`cerr` 전역 스트림을 지정합니다.|
|[cin](#cin)|`cin` 전역 스트림을 지정합니다.|
|[clog](#clog)|`clog` 전역 스트림을 지정합니다.|
|[cout](#cout)|`cout` 전역 스트림을 지정합니다.|
|[wcerr](#wcerr)|`wcerr` 전역 스트림을 지정합니다.|
|[wcin](#wcin)|`wcin` 전역 스트림을 지정합니다.|
|[wclog](#wclog)|`wclog` 전역 스트림을 지정합니다.|
|[wcout](#wcout)|`wcout` 전역 스트림을 지정합니다.|

###  <a name="cerr"></a>  cerr

`cerr` 개체는 \<cstdio>에 선언된, `stderr` 개체와 연관된 스트림 버퍼로의 출력을 제어합니다.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>반환 값

[ostream](../standard-library/ostream-typedefs.md#ostream) 개체입니다.

#### <a name="remarks"></a>설명

이 개체는 표준 오류 출력에 대한 버퍼링되지 않은 삽입을 바이트 스트림으로 제어합니다. 개체가 생성되고 나면 `cerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) 식은 0이 아니고 `cerr.tie() == &cout`입니다.

#### <a name="example"></a>예제

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

###  <a name="cin"></a>  cin

`cin` 전역 스트림을 지정합니다.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>반환 값

[istream](../standard-library/istream-typedefs.md#istream) 개체입니다.

#### <a name="remarks"></a>설명

이 개체는 표준 입력에서의 추출을 바이트 스트림으로 제어합니다. 개체가 생성되고 나면 `cin.`[tie](../standard-library/basic-ios-class.md#tie) 호출에서 `&`[cout](#cout)를 반환합니다.

#### <a name="example"></a>예제

이 예제에서는 `cin`이 숫자가 아닌 문자를 발견할 경우 스트림에서 실패 비트를 설정합니다. 프로그램은 이 실패 비트를 지우고 스트림에서 잘못된 문자를 제거하여 계속 진행합니다.

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output

2
```

###  <a name="clog"></a>  clog

`clog` 전역 스트림을 지정합니다.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>반환 값

[ostream](../standard-library/ostream-typedefs.md#ostream) 개체입니다.

#### <a name="remarks"></a>설명

이 개체는 표준 오류 출력에 대한 버퍼링된 삽입을 바이트 스트림으로 제어합니다.

#### <a name="example"></a>예제

`clog` 사용 예제는 [cerr](#cerr)을 참조하세요.

###  <a name="cout"></a>  cout

`cout` 전역 스트림을 지정합니다.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>반환 값

[ostream](../standard-library/ostream-typedefs.md#ostream) 개체입니다.

#### <a name="remarks"></a>설명

이 개체는 표준 출력에 대한 삽입을 바이트 스트림으로 제어합니다.

#### <a name="example"></a>예제

`cout` 사용 예제는 [cerr](#cerr)을 참조하세요.

###  <a name="wcerr"></a>  wcerr

`wcerr` 전역 스트림을 지정합니다.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>반환 값

[wostream](../standard-library/ostream-typedefs.md#wostream) 개체입니다.

#### <a name="remarks"></a>설명

이 개체는 표준 오류 출력에 대한 버퍼링되지 않은 삽입을 와이드 스트림으로 제어합니다. 개체가 생성되고 나면 `wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) 식은 0이 아닙니다.

#### <a name="example"></a>예제

`wcerr` 사용 예제는 [cerr](#cerr)을 참조하세요.

###  <a name="wcin"></a>  wcin

`wcin` 전역 스트림을 지정합니다.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>반환 값

[wistream](../standard-library/istream-typedefs.md#wistream) 개체입니다.

#### <a name="remarks"></a>설명

이 개체는 표준 입력에서의 추출을 와이드 스트림으로 제어합니다. 개체가 생성되고 나면 `wcin.`[tie](../standard-library/basic-ios-class.md#tie) 호출에서 `&`[wcout](#wcout)를 반환합니다.

#### <a name="example"></a>예제

`wcin` 사용 예제는 [cerr](#cerr)을 참조하세요.

###  <a name="wclog"></a>  wclog

`wclog` 전역 스트림을 지정합니다.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>반환 값

[wostream](../standard-library/ostream-typedefs.md#wostream) 개체입니다.

#### <a name="remarks"></a>설명

이 개체는 표준 오류 출력에 대한 버퍼링된 삽입을 와이드 스트림으로 제어합니다.

#### <a name="example"></a>예제

`wclog` 사용 예제는 [cerr](#cerr)을 참조하세요.

###  <a name="wcout"></a>  wcout

`wcout` 전역 스트림을 지정합니다.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>반환 값

[wostream](../standard-library/ostream-typedefs.md#wostream) 개체입니다.

#### <a name="remarks"></a>설명

이 개체는 넓은 스트림으로 표준 출력에 삽입을 제어합니다.

#### <a name="example"></a>예제

`wcout` 사용 예제는 [cerr](#cerr)을 참조하세요.

다음 예제와 같이 `wcout` 문의 `CString` 인스턴스를 `const wchar_t*`로 캐스팅해야 합니다.

```

    CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;
```

자세한 내용은 [기본 CString 작업](../atl-mfc-shared/basic-cstring-operations.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 프로그래밍](../standard-library/iostream-programming.md)<br/>
[iostreams 규칙](../standard-library/iostreams-conventions.md)<br/>
