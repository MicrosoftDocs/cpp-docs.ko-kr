---
description: '자세한 정보: appdomain'
title: appdomain
ms.date: 11/04/2016
f1_keywords:
- appdomain_cpp
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
ms.openlocfilehash: d817c71058c37b032e2ed6581de3a0fa8c169132
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239807"
---
# <a name="appdomain"></a>appdomain

관리되는 애플리케이션의 각 애플리케이션 도메인에 특정 전역 변수 또는 정적 멤버 변수의 자체 복사본이 포함되어야 하도록 지정합니다. 자세한 내용은 [응용 프로그램 도메인 및 Visual C++](../dotnet/application-domains-and-visual-cpp.md) 을 참조 하세요.

모든 애플리케이션 도메인에는 appdomain별 변수의 자체 복사본이 있습니다. 어셈블리를 애플리케이션 도메인으로 로드하면 appdomain 변수의 생성자가 실행되고 애플리케이션 도메인을 언로드하면 소멸자가 실행됩니다.

공용 언어 런타임에서 프로세스 내의 모든 애플리케이션 도메인이 전역 변수를 공유하도록 하려면 `__declspec(process)` 한정자를 사용합니다. `__declspec(process)` 는 기본적으로 [/clr](../build/reference/clr-common-language-runtime-compilation.md)에서 적용 됩니다. **/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

`__declspec(appdomain)` 는 **/clr** 컴파일러 옵션 중 하나를 사용 하는 경우에만 유효 합니다. 전역 변수, 정적 멤버 변수 또는 정적 로컬 변수만 `__declspec(appdomain)`로 표시할 수 있습니다. 관리되는 형식의 정적 멤버는 항상 이 동작을 수행하므로 `__declspec(appdomain)`를 적용하면 오류가 발생합니다.

를 사용 하 `__declspec(appdomain)` 는 것은 [TLS (스레드 로컬 저장소)](../parallel/thread-local-storage-tls.md)를 사용 하는 것과 비슷합니다. 스레드에는 애플리케이션 도메인과 마찬가지로 자체 스토리지가 있습니다. `__declspec(appdomain)`를 사용하면 전역 변수가 이 애플리케이션용으로 작성된 각 애플리케이션 도메인에 자체 스토리지를 포함할 수 있습니다.

프로세스 및 appdomain 별 변수의 사용을 혼합 하는 데는 제한이 있습니다. 자세한 내용은 [프로세스](../cpp/process.md) 를 참조 하세요.

예를 들어 프로그램 시작 시에는 모든 프로세스별 변수가 초기화된 후에 모든 appdomain 변수가 초기화됩니다. 따라서 프로세스별 변수는 초기화 중에 애플리케이션 도메인별 변수의 값을 사용할 수 없습니다. 따라서 appdomain별 변수와 프로세스별 변수를 조합하여 사용(할당)하는 것은 적절하지 않습니다.

특정 응용 프로그램 도메인에서 함수를 호출 하는 방법에 대 한 자세한 내용은 [Call_in_appdomain 함수](../dotnet/call-in-appdomain-function.md)를 참조 하세요.

## <a name="example"></a>예제

```cpp
// declspec_appdomain.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

class CGlobal {
public:
   CGlobal(bool bProcess) {
      Counter = 10;
      m_bProcess = bProcess;
      Console::WriteLine("__declspec({0}) CGlobal::CGlobal constructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   ~CGlobal() {
      Console::WriteLine("__declspec({0}) CGlobal::~CGlobal destructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   int Counter;

private:
   bool m_bProcess;
};

__declspec(process) CGlobal process_global = CGlobal(true);
__declspec(appdomain) CGlobal appdomain_global = CGlobal(false);

value class Functions {
public:
   static void change() {
      ++appdomain_global.Counter;
   }

   static void display() {
      Console::WriteLine("process_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         process_global.Counter);

      Console::WriteLine("appdomain_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         appdomain_global.Counter);
   }
};

int main() {
   AppDomain^ defaultDomain = AppDomain::CurrentDomain;
   AppDomain^ domain = AppDomain::CreateDomain("Domain 1");
   AppDomain^ domain2 = AppDomain::CreateDomain("Domain 2");
   CrossAppDomainDelegate^ changeDelegate = gcnew CrossAppDomainDelegate(&Functions::change);
   CrossAppDomainDelegate^ displayDelegate = gcnew CrossAppDomainDelegate(&Functions::display);

   // Print the initial values of appdomain_global in all appdomains.
   Console::WriteLine("Initial value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   // Changing the value of appdomain_global in the domain and domain2
   // appdomain_global value in "default" appdomain remain unchanged
   process_global.Counter = 20;
   domain->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);

   // Print values again
   Console::WriteLine("Changed value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   AppDomain::Unload(domain);
   AppDomain::Unload(domain2);
}
```

```Output
__declspec(process) CGlobal::CGlobal constructor
__declspec(appdomain) CGlobal::CGlobal constructor
Initial value
process_global value in appdomain 'declspec_appdomain.exe': 10
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 1': 10
appdomain_global value in appdomain 'Domain 1': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 2': 10
appdomain_global value in appdomain 'Domain 2': 10
Changed value
process_global value in appdomain 'declspec_appdomain.exe': 20
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
process_global value in appdomain 'Domain 1': 20
appdomain_global value in appdomain 'Domain 1': 11
process_global value in appdomain 'Domain 2': 20
appdomain_global value in appdomain 'Domain 2': 12
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(process) CGlobal::~CGlobal destructor
```

## <a name="see-also"></a>참고 항목

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)
