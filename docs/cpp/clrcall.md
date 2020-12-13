---
description: '다음에 대 한 자세한 정보: __clrcall'
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 3c3932333a198063d2878be7ff8618524ff2eb5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335562"
---
# <a name="__clrcall"></a>__clrcall

관리 코드에서만 함수를 호출할 수 있도록 지정합니다.  관리 코드 에서만 호출 되는 모든 가상 함수에 **__clrcall** 를 사용 합니다. 그러나 네이티브 코드에서 호출되는 함수에는 이 호출 규칙을 사용할 수 없습니다. **__Clrcall** 한정자는 Microsoft 전용입니다.

**__Clrcall** 를 사용 하 여 관리 되는 함수에서 가상 관리 되는 함수 또는 관리 되는 함수에서 포인터를 통해 관리 되는 함수로 호출할 때 성능을 향상 시킬 수 있습니다.

진입점은 컴파일러에서 생성된 별도의 함수입니다. 함수에 네이티브 진입점과 관리되는 진입점이 둘 다 있을 경우 둘 중 하나는 함수 구현이 포함된 실제 함수입니다. 다른 함수는 실제 함수를 호출하고 공용 언어 런타임에서 PInvoke를 수행하게 하는 별도의 함수(썽크)입니다. 함수를 **__clrcall** 표시 하는 경우 함수 구현이 MSIL 이어야 하 고 네이티브 진입점 함수가 생성 되지 않음을 표시 합니다.

**__Clrcall** 지정 되지 않은 경우 네이티브 함수의 주소를 사용 하는 경우 컴파일러는 네이티브 진입점을 사용 합니다. **__clrcall** 함수를 관리 하 고 관리에서 네이티브로 전환할 필요가 없음을 나타냅니다. 이 경우 컴파일러가 관리되는 진입점을 사용합니다.

`/clr`(Not `/clr:pure` 또는)를 `/clr:safe` 사용 하 고 **__clrcall** 를 사용 하지 않는 경우 함수의 주소를 가져오는 것은 항상 네이티브 진입점 함수의 주소를 반환 합니다. **__Clrcall** 를 사용 하는 경우 기본 진입점 함수가 생성 되지 않으므로 진입점 썽크 함수가 아닌 관리 되는 함수의 주소를 가져옵니다. 자세한 내용은 [이중 썽킹](../dotnet/double-thunking-cpp.md)을 참조 하세요. **/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

[/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md) 은 모든 함수 및 함수 포인터가 **__clrcall** 되었으며 컴파일러가 compiland 내의 함수를 **__clrcall** 이외의 값으로 표시할 수 없음을 의미 합니다. **/Clr: pure** 를 사용 하는 경우 함수 포인터 및 외부 선언에만 **__clrcall** 을 지정할 수 있습니다.

**/Clr** 을 사용 하 여 컴파일된 기존 c + + 코드에서 함수에 MSIL 구현이 있는 한 **__clrcall** 함수를 직접 호출할 수 있습니다. **__clrcall** 함수는 인라인 asm이 있는 함수에서 직접 호출할 수 없으며 예를 들어를 사용 하 여 컴파일된 경우에도 CPU 관련 내장을 호출할 수 없습니다 `/clr` .

**__clrcall** 함수 포인터는 생성 된 응용 프로그램 도메인 에서만 사용 됩니다.  응용 프로그램 도메인에서 **__clrcall** 함수 포인터를 전달 하는 대신를 사용 <xref:System.CrossAppDomainDelegate> 합니다. 자세한 내용은 [응용 프로그램 도메인 및 Visual C++](../dotnet/application-domains-and-visual-cpp.md)을 참조 하세요.

## <a name="examples"></a>예제

함수가 **__clrcall** 로 선언 되 면 필요할 때 코드가 생성 됩니다. 예를 들어 함수를 호출 하는 경우입니다.

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

다음 샘플에서는 함수 포인터를 정의하고 관리 코드에서만 함수 포인터를 호출할 수 있도록 선언합니다. 여기서는 컴파일러가 관리되는 함수를 직접 호출하고 네이티브 진입점(이중 썽크 문제)을 방지할 수 있습니다.

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>참고 항목

[인수 전달 및 명명 규칙](../cpp/argument-passing-and-naming-conventions.md)<br/>
[키워드](../cpp/keywords-cpp.md)
