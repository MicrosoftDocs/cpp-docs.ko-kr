---
description: '자세한 정보: 매크로 _countof'
title: _countof 매크로
ms.date: 03/22/2018
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
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 190f47aa7bb6bcf6bbd9478cce9df90aca81b437
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146460"
---
# <a name="_countof-macro"></a>_countof 매크로

정적으로 할당 된 배열의 요소 수를 계산 합니다.

## <a name="syntax"></a>구문

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>매개 변수

*array*<br/>
배열 이름입니다.

## <a name="return-value"></a>반환 값

**Size_t** 로 표현 된 배열의 요소 수입니다.

## <a name="remarks"></a>설명

**_countof** 는 함수 형태의 전처리기 매크로로 구현 됩니다. C + + 버전에는 정적으로 선언 된 배열 대신 포인터가 전달 되는 경우 컴파일 타임에 검색할 추가 템플릿 기계가 있습니다.

*배열이* 실제로 포인터가 아니라 배열 인지 확인 합니다. C에서는 *배열이* 포인터인 경우 **_countof** 에서 잘못 된 결과를 생성 합니다. C + +에서는 *배열이* 포인터인 경우 **_countof** 컴파일되지 않습니다.  Decays 함수에 매개 변수로 전달 되는 배열은 *포인터로* 전달 됩니다. 즉, 함수 내에서 **_countof** 를 사용 하 여 배열의 범위를 확인할 수 없습니다.

## <a name="requirements"></a>요구 사항

|매크로|필수 헤더|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

## <a name="example"></a>예제

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>참고 항목

[sizeof 연산자](../../cpp/sizeof-operator.md)<br/>
