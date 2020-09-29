---
title: Debug 클래스(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 47e1b949cb6e998508a3bd362b1c74961cf4cc23
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414154"
---
# <a name="debug-class-ccli"></a>Debug 클래스(C++/CLI)

Visual C++ 응용 프로그램에서를 사용 하는 경우 <xref:System.Diagnostics.Debug> 디버그와 릴리스 빌드 간에 동작이 변경 되지 않습니다.

## <a name="remarks"></a>설명

의 동작은 <xref:System.Diagnostics.Trace> Debug 클래스의 동작과 동일 하지만 정의 되는 기호 추적에 종속 됩니다. 즉, `#ifdef` 릴리스 빌드에서 디버그 동작을 방지 하기 위해 추적 관련 코드를 사용 해야 합니다.

## <a name="example-always-executes-output-statements"></a>예: 항상 output 문 실행

### <a name="description"></a>Description

다음 샘플에서는 **/DDEBUG** 또는 **/DTRACE**를 사용 하 여 컴파일 하는지 여부에 관계 없이 항상 output 문을 실행 합니다.

### <a name="code"></a>코드

```cpp
// mcpp_debug_class.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
   Trace::Unindent();

   Debug::WriteLine("test");
}
```

### <a name="output"></a>출력

```Output
    Entering Main
Hello World.
    Exiting Main
test
```

## <a name="example-use-ifdef-and-endif-directives"></a>예: #ifdef 및 #endif 지시문 사용

### <a name="description"></a>Description

예상 되는 동작을 가져오려면 (즉, 릴리스 빌드에 대해 "테스트" 출력이 인쇄 되지 않음) 및 지시문을 사용 해야 합니다 `#ifdef` `#endif` . 위의 코드 샘플은이 수정 사항을 보여 주기 위해 아래에서 수정 되었습니다.

### <a name="code"></a>코드

```cpp
// mcpp_debug_class2.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();

#ifdef TRACE   // checks for a debug build
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
#endif
   Trace::Unindent();

#ifdef DEBUG   // checks for a debug build
   Debug::WriteLine("test");
#endif   //ends the conditional block
}
```

## <a name="see-also"></a>참조

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
