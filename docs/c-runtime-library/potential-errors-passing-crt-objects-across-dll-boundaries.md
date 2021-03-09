---
title: DLL 경계를 넘어 CRT 개체를 전달할 때 발생할 수 있는 오류
description: DLL (동적 연결 라이브러리) 경계를 넘어 Microsoft C 런타임 개체를 전달할 때 발생할 수 있는 잠재적인 문제에 대 한 개요입니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 7af0fe8b5819bf428753c9ec71099113df0fa79e
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514553"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>DLL 경계를 넘어 CRT 개체를 전달할 때 발생할 수 있는 오류

파일 핸들, 로캘 및 환경 변수와 같은 CRT (C 런타임) 개체를 dll 경계를 넘어 함수 호출을 통해 DLL로 전달 하는 경우 dll 또는 DLL을 호출 하는 파일에서 다른 CRT 라이브러리 복사본을 사용 하는 경우 예기치 않은 동작이 발생할 수 있습니다.

메모리를 할당 (또는를 사용 하 여 명시적으로 또는, 등을 사용 하 여 `new` 암시적으로 `malloc` ) 한 `strdup` `strstreambuf::str` 다음 해제 된 DLL 경계를 넘어 포인터를 전달 하면 관련 문제가 발생할 수 있습니다. DLL 및 해당 소비자가 CRT 라이브러리의 다른 복사본을 사용 하는 경우이로 인해 메모리 액세스 위반 또는 힙 손상이 발생할 수 있습니다.

이 문제의 또 다른 증상은 다음과 같이 디버깅 중 출력 창에서 오류가 발생 하는 것입니다. `HEAP[]: Invalid Address specified to RtlValidateHeap(#,#)`

## <a name="causes"></a>원인

CRT 라이브러리 복사본마다 별도의 고유한 상태가 앱 또는 DLL에 의해 스레드 로컬 스토리지에 유지됩니다.

파일 핸들, 환경 변수 및 로캘과 같은 CRT 개체는 이러한 개체가 할당 또는 설정 된 응용 프로그램 또는 DLL의 CRT 복사본에만 유효 합니다. DLL 및 해당 클라이언트에서 다른 CRT 라이브러리 복사본을 사용 하는 경우 이러한 CRT 개체를 DLL 경계를 넘어 전달 하 고 다른 쪽에서는 올바르게 사용할 수 없습니다. Visual Studio 2015 이상에서 범용 CRT 이전의 CRT 버전에 적용 됩니다.

Visual Studio 2013 또는 이전 버전으로 빌드된 모든 버전의 Visual Studio에 대해 버전별 CRT 라이브러리가 있습니다. 데이터 구조 및 명명 규칙과 같은 CRT의 내부 구현 세부 정보는 각 버전에서 다릅니다. 한 버전의 CRT에 대해 컴파일된 코드를 CRT DLL의 다른 버전에 동적으로 연결 하는 것은 지원 되지 않습니다. 경우에 따라 디자인이 아니라 동작 하기 때문입니다.

Crt 라이브러리의 각 복사본에는 자체 힙 관리자가 있으므로 하나의 CRT 라이브러리에 메모리를 할당 하 고 DLL 경계를 넘어 포인터를 전달 하 여 다른 CRT 라이브러리 복사본에 의해 해제 되기 때문에 힙이 손상 될 수 있습니다. Dll 경계를 넘어 CRT 개체를 전달 하거나 메모리를 할당 하 고 DLL 외부에서 해제 될 것으로 예상 하도록 DLL을 디자인 하는 경우 DLL의 클라이언트는 DLL과 동일한 CRT 라이브러리 복사본을 사용 해야 합니다.

DLL 및 해당 클라이언트는 일반적으로 로드 타임에 둘 다 동일한 버전의 CRT DLL에 연결된 경우에만 동일한 CRT 라이브러리 복사본을 사용합니다. Visual Studio 2015 및 나중에 Windows 10에서 사용 되는 유니버설 CRT 라이브러리의 DLL 버전은 이제 중앙에서 배포 된 Windows 구성 요소 (ucrtbase.dll) 이므로 Visual Studio 2015 이상 버전을 사용 하 여 빌드된 앱에서 동일 합니다. 그러나 CRT 코드가 동일한 경우에도 하나의 힙에 할당 된 메모리를 다른 힙을 사용 하는 구성 요소에 제공할 수 없습니다.

## <a name="example-pass-file-handle-across-dll-boundary"></a>예: DLL 경계를 넘어 파일 핸들을 전달 합니다.

### <a name="description"></a>Description

이 예제에서는 DLL 경계를 넘어 파일 핸들을 전달합니다.

DLL 및 .exe 파일은를 사용 하 여 빌드되기 `/MD` 때문에 CRT의 단일 복사본을 공유할 수 있습니다.

를 사용 하 여를 다시 빌드하여 `/MT` CRT의 개별 복사본을 사용 하는 경우 결과 **test1Main.exe** 를 실행 하면 액세스 위반이 발생 합니다.

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
#include <stdio.h>
#include <process.h>
void writeFile(FILE *stream);

int main(void)
{
   FILE  * stream;
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );
   writeFile(stream);
   system( "type fprintf.out" );
}
```

```Output
this is a string
```

## <a name="example-pass-environment-variables-across-dll-boundary"></a>예: DLL 경계를 넘어 환경 변수 전달

### <a name="description"></a>Description

이 예제에서는 DLL 경계를 넘어 환경 변수를 전달합니다.

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
#include <stdio.h>
#include <stdlib.h>

__declspec(dllexport) void readEnv()
{
   char *libvar;
   size_t libvarsize;

   /* Get the value of the MYLIB environment variable. */
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );

   if( libvar != NULL )
      printf( "New MYLIB variable is: %s\n", libvar);
   else
      printf( "MYLIB has not been set.\n");
   free( libvar );
}
```

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

CRT 복사본이 하나만 사용 되도록 DLL과 .exe 파일을 모두 빌드하면 `/MD` 프로그램이 성공적으로 실행 되 고 다음과 같은 출력이 생성 됩니다.

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>추가 정보

[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
