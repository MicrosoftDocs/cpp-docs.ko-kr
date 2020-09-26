---
title: C + + 프로그램 종료
description: exitC + + 언어 프로그램의 방법을 설명 합니다.
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: fd0c7699ae032b5551f4fbc37eb3b7fa999a168f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352923"
---
# <a name="c-program-termination"></a>C + + 프로그램 종료

C + +에서는 exit 다음과 같은 방법으로 프로그램을 수행할 수 있습니다.

- 함수를 호출 [exit](../c-runtime-library/reference/exit-exit-exit.md) 합니다.
- 함수를 호출 [abort](../c-runtime-library/reference/abort.md) 합니다.
- [return](return-statement-cpp.md)에서 문을 실행 `main` 합니다.

## <a name="no-locexit-function"></a>exit 함수

[exit](../c-runtime-library/reference/exit-exit-exit.md)에 선언 된 함수는 \<stdlib.h> c + + 프로그램을 종료 합니다. 에 대 한 인수로 제공 되는 값은 `exit` return 프로그램의 return 코드 또는 코드로 운영 체제에 적용 됩니다 exit . 규칙에 따라 return 코드 0은 프로그램이 성공적으로 완료 되었음을 의미 합니다. 에 정의 된 상수 EXIT_FAILURE 및 EXIT_SUCCESS를 사용 \<stdlib.h> 하 여 프로그램의 성공 또는 실패를 나타낼 수 있습니다.

**`return`** 함수에서 문을 실행 `main` 하는 것은 값을 인수로 사용 하 여 함수를 호출 하는 것과 같습니다 `exit` return .

## <a name="no-locabort-function"></a>abort 함수

[abort](../c-runtime-library/reference/abort.md)표준 포함 파일에도 선언 된 함수는 \<stdlib.h> c + + 프로그램을 종료 합니다. 와의 차이점 `exit` 은 `abort` `exit` c + + 런타임 종료 처리를 수행할 수 있도록 하는 것입니다 (전역 개체 소멸자가 호출 됨). 반면는 `abort` 프로그램을 즉시 종료 합니다. `abort`함수는 초기화 된 전역 정적 개체에 대 한 일반적인 소멸 프로세스를 무시 합니다. 또한 함수를 사용 하 여 지정 된 특별 한 처리를 무시 [atexit](../c-runtime-library/reference/atexit.md) 합니다.

## <a name="no-locatexit-function"></a>atexit 함수

[atexit](../c-runtime-library/reference/atexit.md)프로그램 종료 전에 실행 되는 작업을 지정 하려면 함수를 사용 합니다. 를 호출 하기 전에 초기화 된 전역 정적 개체 **atexit** 는 처리 함수를 실행 하기 전에 제거 되지 않습니다 exit .

## <a name="no-locreturn-statement-in-no-locmain"></a>return 문 main

[return](return-statement-cpp.md)에서 문을 실행 하는 것 `main` 은 함수를 호출 하는 것과 기능적으로 동일 `exit` 합니다. 다음 예제를 참조하세요.

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

`exit` **`return`** 위의 예제에서 및 문은 기능적으로 동일 합니다. 그러나 c + +에서는 값이 아닌 형식이 포함 된 함수가 필요 return **`void`** return 합니다. **`return`** 문은의 값을 사용할 수 있습니다 return `main` .

## <a name="destruction-of-static-objects"></a>정적 개체 소멸

`exit`에서 문을 호출 하거나 실행 하는 경우 **`return`** `main` 정적 개체는 초기화 (있는 경우)의 역순으로 소멸 됩니다 `atexit` . 다음 예제에서는 이러한 초기화 및 정리가 작동하는 방법을 보여 줍니다.

### <a name="example"></a>예제

다음 예제에서는 `sd1` `sd2` 로 진입 하기 전에 정적 개체 및가 만들어지고 초기화 됩니다 `main` . 이 프로그램은 문을 사용 하 여 종료 된 후 **`return`** 에 `sd2` 는 먼저 소멸 된 후에 제거 됩니다 `sd1` . `ShowData` 클래스에 대한 소멸자가 이 정적 개체와 연결된 파일을 닫습니다.

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

범위를 벗어나면 소멸되도록 블록 범위를 사용해 `ShowData` 개체를 선언하여 이 코드를 작성할 수도 있습니다.

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>참고 항목

[main 함수 및 명령줄 인수](main-function-command-line-args.md)
