---
description: Call_in_appdomain 함수에 대해 자세히 알아보세요.
title: call_in_appdomain 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- call_in_appdomain
helpviewer_keywords:
- call_in_appdomain function
ms.assetid: 9a1a5026-b76b-4cae-a3d4-29badeb9db9c
ms.openlocfilehash: ece4929e2b99b09f3c9148b50c609ec1b5596b3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282577"
---
# <a name="call_in_appdomain-function"></a>call_in_appdomain 함수

지정 된 응용 프로그램 도메인에서 함수를 실행 합니다.

## <a name="syntax"></a>구문

```
template <typename ArgType1, ...typename ArgTypeN>
void call_in_appdomain(
   DWORD appdomainId,
   void (*voidFunc)(ArgType1, ...ArgTypeN) [ ,
   ArgType1 arg1,
   ...
   ArgTypeN argN ]
);
template <typename RetType, typename ArgType1, ...typename ArgTypeN>
RetType call_in_appdomain(
   DWORD appdomainId,
   RetType (*nonvoidFunc)(ArgType1, ...ArgTypeN) [ ,
   ArgType1 arg1,
   ...
   ArgTypeN argN ]
);
```

#### <a name="parameters"></a>매개 변수

*appdomainId*<br/>
함수를 호출할 appdomain입니다.

*voidFunc*<br/>
**`void`** N 개의 매개 변수를 사용 하는 함수에 대 한 포인터입니다 (0 <= n <= 15).

*nonvoidFunc*<br/>
**`void`** N 개의 매개 변수를 사용 하는 비 함수에 대 한 포인터입니다 (0 <= n <= 15).

*arg1 ... argN*<br/>
다른 appdomain에 전달 되는 매개 변수는 0 ~ 15 `voidFunc` `nonvoidFunc` 입니다.

## <a name="return-value"></a>반환 값

`voidFunc` `nonvoidFunc` 지정 된 응용 프로그램 도메인에서 또는를 실행 한 결과입니다.

## <a name="remarks"></a>설명

에 전달 된 함수의 인수는 `call_in_appdomain` CLR 형식이 아니어야 합니다.

## <a name="example"></a>예제

```cpp
// msl_call_in_appdomain.cpp
// compile with: /clr

// Defines two functions: one takes a parameter and returns nothing,
// the other takes no parameters and returns an int.  Calls both
// functions in the default appdomain and in a newly-created
// application domain using call_in_appdomain.

#include <msclr\appdomain.h>

using namespace System;
using namespace msclr;

void PrintCurrentDomainName( char* format )
{
   String^ s = gcnew String(format);
   Console::WriteLine( s, AppDomain::CurrentDomain->FriendlyName );
}

int GetDomainId()
{
   return AppDomain::CurrentDomain->Id;
}

int main()
{
   AppDomain^ appDomain1 = AppDomain::CreateDomain( "First Domain" );

   call_in_appdomain( AppDomain::CurrentDomain->Id,
                   &PrintCurrentDomainName,
                   (char*)"default appdomain: {0}" );
   call_in_appdomain( appDomain1->Id,
                   &PrintCurrentDomainName,
                   (char*)"in appDomain1: {0}" );

   int id;
   id = call_in_appdomain( AppDomain::CurrentDomain->Id, &GetDomainId );
   Console::WriteLine( "default appdomain id = {0}", id );
   id = call_in_appdomain( appDomain1->Id, &GetDomainId );
   Console::WriteLine( "appDomain1 id = {0}", id );
}
```

## <a name="output"></a>출력

```
default appdomain: msl_call_in_appdomain.exe
in appDomain1: First Domain
default appdomain id = 1
appDomain1 id = 2
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\appdomain.h>

Msclr **네임 스페이스**
