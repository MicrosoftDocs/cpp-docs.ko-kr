---
title: bitor
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
- bitor
- std.bitor
- std::bitor
helpviewer_keywords:
- bitor function
ms.assetid: 3c0a3711-9c74-41f2-b400-2f7797da30d1
ms.openlocfilehash: e8bb78e73b8beca4cbffd975f41c3432cf9fdefe
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521910"
---
# <a name="bitor"></a>bitor

&#124; 연산자에 대한 대안입니다.

## <a name="syntax"></a>구문

```C

#define bitor |
```

## <a name="remarks"></a>설명

매크로가 &#124; 연산자를 생성합니다.

## <a name="example"></a>예제

```cpp
// iso646_bitor.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 1, b = 2, result;

   result = a | b;
   cout << result << endl;

   result= a bitor b;
   cout << result << endl;
}
```

```Output
3
3
```

## <a name="requirements"></a>요구 사항

**헤더:** \<iso646.h>