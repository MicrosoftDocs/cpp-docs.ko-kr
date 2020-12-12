---
description: '자세한 정보: 관리 되는 예외 사용의 기본 개념'
title: 관리되는 예외 사용의 기본 개념
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: 1c6e405de2a82e32375092007dcc1f0fd8f654c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282603"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>관리되는 예외 사용의 기본 개념

이 항목에서는 관리 되는 응용 프로그램의 예외 처리에 대해 설명 합니다. 즉, **/clr** 컴파일러 옵션을 사용 하 여 컴파일된 응용 프로그램입니다.

## <a name="in-this-topic"></a>항목 내용

- [/Clr에서 예외 throw](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [CLR 확장에 대 한 Try/Catch 블록](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>설명

**/Clr** 옵션을 사용 하 여 컴파일하면 clr 예외를 처리할 수 있을 뿐만 아니라 clr 예외를 <xref:System.Exception> 처리 하는 데 유용한 여러 메서드를 제공할 수 있으며 사용자 정의 예외 클래스에 대 한 기본 클래스로 사용 하는 것이 좋습니다.

**/Clr** 에서 인터페이스에서 파생 된 예외 형식을 catch 하는 것은 지원 되지 않습니다. 또한 공용 언어 런타임에서는 스택 오버플로 예외를 catch 하는 것을 허용 하지 않습니다. 스택 오버플로 예외는 프로세스를 종료 합니다.

관리 되는 응용 프로그램 및 관리 되지 않는 응용 프로그램에서 예외 처리의 차이점에 대 한 자세한 내용은 [Managed Extensions for C++에서 예외 처리 동작의 차이점](../dotnet/differences-in-exception-handling-behavior-under-clr.md)을 참조 하세요.

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> /Clr에서 예외 throw

C + + throw 식이 CLR 형식에 대 한 핸들을 throw 하도록 확장 되었습니다. 다음 예제에서는 사용자 지정 예외 형식을 만든 다음 해당 형식의 인스턴스를 throw 합니다.

```cpp
// clr_exception_handling.cpp
// compile with: /clr /c
ref struct MyStruct: public System::Exception {
public:
   int i;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   throw pMyStruct;
}
```

값 형식은 throw 되기 전에 boxing 해야 합니다.

```cpp
// clr_exception_handling_2.cpp
// compile with: /clr /c
value struct MyValueStruct {
   int i;
};

void GlobalFunction() {
   MyValueStruct v = {11};
   throw (MyValueStruct ^)v;
}
```

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> CLR 확장에 대 한 Try/Catch 블록

동일한 **`try`** / **`catch`** 블록 구조를 사용 하 여 CLR 및 네이티브 예외를 모두 catch 할 수 있습니다.

```cpp
// clr_exception_handling_3.cpp
// compile with: /clr
using namespace System;
ref struct MyStruct : public Exception {
public:
   int i;
};

struct CMyClass {
public:
   double d;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   pMyStruct->i = 11;
   throw pMyStruct;
}

void GlobalFunction2() {
   CMyClass c = {2.0};
   throw c;
}

int main() {
   for ( int i = 1; i >= 0; --i ) {
      try {
         if ( i == 1 )
            GlobalFunction2();
         if ( i == 0 )
            GlobalFunction();
      }
      catch ( CMyClass& catchC ) {
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );
         Console::WriteLine( catchC.d );
      }
      catch ( MyStruct^ catchException ) {
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );
         Console::WriteLine( catchException->i );
      }
   }
}
```

### <a name="output"></a>출력

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>C + + 개체 해제 순서

Throw 함수와 처리 함수 간의 런타임 스택에 있을 수 있는 소멸자가 있는 모든 c + + 개체에 대해 해제가 발생 합니다. CLR 형식은 힙에 할당 되기 때문에 해제는 적용 되지 않습니다.

Throw 된 예외에 대 한 이벤트 순서는 다음과 같습니다.

1. 런타임은 예외를 catch 하기 위해 적절 한 catch 절을 찾는 스택 또는 SEH의 경우를 제외한 SEH 필터를 단계별로 안내 합니다. Catch 절은 먼저 어휘 순서로 검색 된 다음 동적으로 호출 스택을 검색 합니다.

1. 올바른 처리기를 찾으면 해당 지점으로 스택이 해제 됩니다. 스택의 각 함수 호출에 대 한 로컬 개체는 소멸이 고, 대부분의 중첩 된에서 실행 되는 __finally 블록은 실행 됩니다.

1. 스택이 해제 되 면 catch 절이 실행 됩니다.

### <a name="catching-unmanaged-types"></a>관리 되지 않는 형식 catch

관리 되지 않는 개체 형식이 throw 되 면 형식의 예외와 함께 래핑됩니다 <xref:System.Runtime.InteropServices.SEHException> . 적절 한 **`catch`** 절을 검색 하는 경우 두 가지 가능성이 있습니다.

- 네이티브 c + + 형식이 발견 되 면 예외가 래핑 해제 되 고 발견 된 형식과 비교 됩니다. 이러한 비교는 일반적인 방식으로 네이티브 c + + 형식을 catch 할 수 있도록 합니다.

- 그러나 **`catch`** **Sehexception** 형식의 절 이나 해당 기본 클래스를 먼저 검사 하면 절에서 예외를 가로채 게 됩니다. 따라서 네이티브 c + + 형식을 catch 하는 모든 catch 절을 CLR 형식의 catch 절 앞에 먼저 넣어야 합니다.

다음 사항에 유의하세요.

```
catch(Object^)
```

및

```
catch(...)
```

는 SEH 예외를 포함 하 여 모든 throw 된 형식을 catch 합니다.

Catch (Object ^)에서 관리 되지 않는 형식을 catch 하는 경우에는 throw 된 개체를 삭제 하지 않습니다.

관리 되지 않는 예외를 throw 하거나 catch 할 때 **/EHs** 또는 **/eha** 대신 [/ehsc](../build/reference/eh-exception-handling-model.md) 컴파일러 옵션을 사용 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

[예외 처리](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[예외 처리](../cpp/exception-handling-in-visual-cpp.md)
