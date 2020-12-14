---
description: '자세한 정보: 입력 스트림 멤버 함수'
title: 입력 스트림 멤버 함수
ms.date: 07/19/2019
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: 8b75470d39e5c376da497f721c725eaad8424b3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231604"
---
# <a name="input-stream-member-functions"></a>입력 스트림 멤버 함수

입력 스트림 멤버 함수는 디스크 입력에 사용됩니다.

## <a name="open"></a><a name="vclrftheopenfunctionforinputstreamsanchor11"></a> 열린

입력 파일 스트림 ()을 사용 하는 경우 `ifstream` 해당 스트림을 특정 디스크 파일에 연결 해야 합니다. 생성자에서이 작업을 수행 하거나 함수를 사용할 수 있습니다 `open` . 두 경우 모두 인수는 동일합니다.

일반적으로 입력 스트림과 연결 된 파일을 열 때 [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) 플래그를 지정 합니다. 기본 모드는입니다 `ios::in` . `openmode`플래그 목록은 [ios_base:: openmode](../standard-library/ios-base-class.md#openmode)를 참조 하세요. 플래그는 비트 OR( &#124; ) 연산자와 함께 사용할 수 있습니다.

파일을 읽으려면 먼저 멤버 함수를 사용 하 여 `fail` 존재 하는지 확인 합니다.

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="get"></a><a name="vclrfthegetfunctionanchor12"></a> 가져오기

형식이 지정 되지 않은 `get` 멤버 함수는 `>>` 두 개의 예외를 제외 하 고 연산자 처럼 작동 합니다. 첫째, 함수는 공백 `get` 문자를 포함 하는 반면, 추출기는 플래그가 설정 될 때 공백을 제외 합니다 `skipws` (기본값). 둘째, `get` 함수는 연결 된 출력 스트림 ( `cout` 예:)을 플러시할 가능성이 적습니다.

`get`함수의 변형은 버퍼 주소와 읽을 최대 문자 수를 지정 합니다. 이 함수는 다음 예제와 같이 특정 변수로 전송되는 문자 수를 제한하는 데 유용합니다.

```cpp
// ioo_get_function.cpp
// compile with: /EHsc
// Type up to 24 characters and a terminating character.
// Any remaining characters can be extracted later.
#include <iostream>
using namespace std;

int main()
{
   char line[25];
   cout << " Type a line terminated by carriage return\n>";
   cin.get( line, 25 );
   cout << line << endl;
}
```

### <a name="input"></a>입력

```Input
1234
```

### <a name="sample-output"></a>샘플 출력

```Output
1234
```

## <a name="getline"></a><a name="vclrfthegetlinefunctionanchor13"></a> getline

`getline`멤버 함수는 `get` 함수와 유사 합니다. 두 함수 모두 입력에 대해 종료 문자를 지정하는 세 번째 인수를 허용합니다. 기본값은 줄 바꿈 문자입니다. 두 함수 모두 필요한 종료 문자에 대해 문자 하나를 예약합니다. 그러나는 `get` 스트림에서 종료 문자를 그대로 두고 `getline` 종료 문자를 제거 합니다.

다음 예제에서는 입력 스트림에 대해 종료 문자를 지정합니다.

```cpp
// getline_func.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char line[100];
   cout << " Type a line terminated by 't'" << endl;
   cin.getline( line, 100, 't' );
   cout << line;
}
```

### <a name="input"></a>입력

```Input
test
```

## <a name="read"></a><a name="vclrfthereadfunctionanchor14"></a> 읽음

`read`멤버 함수는 파일에서 지정 된 메모리 영역까지 바이트를 읽습니다. 길이 인수가 읽은 바이트 수를 결정합니다. 해당 인수를 포함하지 않은 경우에는 실제 파일 끝에 도달하거나 텍스트 모드 파일의 경우 포함된 `EOF` 문자를 읽으면 읽기가 중지됩니다.

다음 예제에서는 급여 파일에서 구조로 이진 레코드를 읽어 옵니다.

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main()
{
   struct
   {
      double salary;
      char name[23];
   } employee;

   ifstream is( "payroll" );
   if( is ) {  // ios::operator void*()
      is.read( (char *) &employee, sizeof( employee ) );
      cout << employee.name << ' ' << employee.salary << endl;
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

프로그램에서는 종료 캐리지 리턴 또는 줄 바꿈 문자가 없는 구조에 지정 된 대로 데이터 레코드의 형식이 정확히 지정 된 것으로 가정 합니다.

## <a name="seekg-and-tellg"></a><a name="vclrftheseekgandtellgfunctionsanchor7"></a> seekg 및 tellg

입력 파일 스트림은 파일에서 다음에 읽을 데이터의 위치로 내부 포인터를 유지합니다. 다음과 같이 `seekg` 함수로 이 포인터를 설정합니다.

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main( )
{
   char ch;

   ifstream tfile( "payroll" );
   if( tfile ) {
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)
      while ( tfile.good() ) { // EOF or failure stops the reading
         tfile.get( ch );
         if( !ch ) break;      // quit on null
         cout << ch;
      }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

를 사용 하 여 `seekg` 레코드 지향 데이터 관리 시스템을 구현 하려면 고정 길이 레코드 크기와 레코드 번호를 곱하여 파일의 끝을 기준으로 바이트 위치를 구한 다음 개체를 사용 하 여 `get` 레코드를 읽습니다.

`tellg` 멤버 함수는 읽기를 위해 현재 파일 위치를 반환합니다. 이 값은에 정의 된 형식입니다 `streampos` **`typedef`** \<iostream> . 다음 예제에서는 파일을 읽고 공백의 위치를 보여 주는 메시지를 표시합니다.

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main( )
{
   char ch;
   ifstream tfile( "payroll" );
   if( tfile ) {
       while ( tfile.good( ) ) {
          streampos here = tfile.tellg();
          tfile.get( ch );
          if ( ch == ' ' )
             cout << "\nPosition " << here << " is a space";
       }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

## <a name="close"></a><a name="vclrftheclosefunctionforinputstreamsanchor15"></a> 닫습니다

`close`멤버 함수는 입력 파일 스트림과 연결 된 디스크 파일을 닫고 운영 체제 파일 핸들을 해제 합니다. [`ifstream`](../standard-library/basic-ifstream-class.md)소멸자는 파일을 닫지만 `close` 동일한 스트림 개체에 대해 다른 파일을 열어야 하는 경우에는 함수를 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[입력 스트림](../standard-library/input-streams.md)
