---
description: '다음에 대 한 자세한 정보: xor_eq'
title: xor_eq
ms.date: 11/04/2016
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- std.xor_eq
- xor_eq
- std::xor_eq
helpviewer_keywords:
- xor_eq function
ms.assetid: eca4b6b4-b77a-4d44-a09a-5a7e69fdb56c
ms.openlocfilehash: d16c1a85ff2943156b03bb772ffb8231180a16c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117148"
---
# <a name="xor_eq"></a>xor_eq

^= 연산자에 대한 대안입니다.

## <a name="syntax"></a>구문

```C

#define xor_eq ^=
```

## <a name="remarks"></a>설명

매크로가 ^= 연산자를 생성합니다.

## <a name="example"></a>예제

```cpp
// iso646_xor_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 3, b = 2, result;

   result= a ^= b;
   cout << result << endl;

   a = 3;
   b = 2;

   result= a xor_eq b;
   cout << result << endl;
}
```

```Output
1
1
```

## <a name="requirements"></a>요구 사항

**헤더:**\<iso646.h>
