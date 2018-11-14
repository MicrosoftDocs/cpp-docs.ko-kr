---
title: not_eq
ms.date: 11/04/2016
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- not_eq
- std::not_eq
- std.not_eq
helpviewer_keywords:
- not_eq function
ms.assetid: d87ad299-8b50-4393-a57f-06f70e1f23fb
ms.openlocfilehash: 881aae0ba511d8339b6911720b6fc481ff2f59c0
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520285"
---
# <a name="noteq"></a>not_eq

!= 연산자에 대한 대안입니다.

## <a name="syntax"></a>구문

```C

#define not_eq !=
```

## <a name="remarks"></a>설명

매크로가 != 연산자를 생성합니다.

## <a name="example"></a>예제

```cpp
// iso646_not_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 0, b = 1;

   if (a != b)
      cout << "a is not equal to b" << endl;

   if (a not_eq b)
      cout << "a is not equal to b" << endl;
}
```

```Output
a is not equal to b
a is not equal to b
```

## <a name="requirements"></a>요구 사항

**헤더:** \<iso646.h>