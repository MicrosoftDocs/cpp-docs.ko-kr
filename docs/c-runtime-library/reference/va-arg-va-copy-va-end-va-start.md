---
description: '자세한 정보: va_arg, va_copy, va_end, va_start'
title: va_arg, va_copy, va_end, va_start
ms.date: 11/04/2016
api_name:
- va_arg
- va_end
- va_copy
- va_start
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
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
helpviewer_keywords:
- variable argument lists, accessing
- va_start macro
- va_arg macro
- va_end macro
- arguments [C++], argument lists
- va_list macro
- va_dcl macro
- va_alist macro
- va_copy macro
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
ms.openlocfilehash: 368a08e3ceb78d09d11a9f661772c6b0abef471f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299282"
---
# <a name="va_arg-va_copy-va_end-va_start"></a>va_arg, va_copy, va_end, va_start

가변 인수 목록에 액세스합니다.

## <a name="syntax"></a>구문

```C
type va_arg(
   va_list arg_ptr,
   type
);
void va_copy(
   va_list dest,
   va_list src
); // (ISO C99 and later)
void va_end(
   va_list arg_ptr
);
void va_start(
   va_list arg_ptr,
   prev_param
); // (ANSI C89 and later)
void va_start(
   arg_ptr
);  // (deprecated Pre-ANSI C89 standardization version)
```

### <a name="parameters"></a>매개 변수

*type*<br/>
검색할 인수의 형식입니다.

*arg_ptr*<br/>
인수 목록에 대한 포인터입니다.

*dest*<br/>
*Src* 에서 초기화할 인수 목록에 대 한 포인터입니다.

*src*<br/>
*대상* 에 복사할 초기화 된 인수 목록에 대 한 포인터입니다.

*prev_param*<br/>
첫 번째 선택적 인수 앞에 오는 매개 변수입니다.

## <a name="return-value"></a>반환 값

**va_arg** 현재 인수를 반환 합니다. **va_copy**, **va_start** 및 **va_end** 값을 반환 하지 않습니다.

## <a name="remarks"></a>설명

**Va_arg**, **va_copy**, **va_end** 및 **va_start** 매크로는 함수에서 가변 개수의 인수를 사용 하는 경우 함수에 대 한 인수에 액세스할 수 있는 이식 가능한 방법을 제공 합니다. 매크로에는 두 가지 버전이 있습니다. STDARG.H에서 정의되는 매크로는 ISO C99 표준을 준수합니다. VARARGS.H에서 정의되는 매크로는 더 이상 사용되지 않지만 ANSI C89 표준이 적용되기 전에 작성된 이전 버전 코드와의 호환성을 위해 유지됩니다.

이러한 매크로는 함수가 고정된 수의 필수 인수에 가변 수의 선택적 인수가 붙은 형식을 사용한다고 가정합니다. 필수 인수는 함수에 대한 일반 매개 변수로 선언되며 매개 변수 이름을 통해 액세스할 수 있습니다. 선택적 인수의 경우 STDARG.H(ANSI C89 표준이 적용되기 전에 작성된 코드의 경우 VARARGS.H) 매크로를 통해 액세스합니다. 이 경우 인수 목록의 첫 번째 선택적 인수에 대한 포인터를 설정하고, 목록에서 인수를 검색한 다음 인수 처리가 완료되면 포인터를 다시 설정합니다.

STDARG.H로 정의되는 C 표준 매크로는 다음과 같이 사용됩니다.

- **va_start** 는 함수에 전달 되는 인수 목록의 첫 번째 선택적 인수로 *arg_ptr* 를 설정 합니다. *Arg_ptr* 인수는 **va_list** 형식 이어야 합니다. 인수 *prev_param* 은 인수 목록의 첫 번째 선택적 인수 바로 앞에 오는 필수 매개 변수의 이름입니다. *Prev_param* register 저장소 클래스를 사용 하 여 선언 된 경우 매크로의 동작이 정의 되지 않습니다. **va_start** 를 사용 하려면 먼저 **va_arg** 를 사용 해야 합니다.

- **va_arg** 은 *arg_ptr* 에서 제공 하는 위치에서 *형식의* 값을 검색 하 고, *형식의* 크기를 사용 하 여 다음 인수를 시작할 위치를 결정 하 여 목록의 다음 인수를 가리키도록 *arg_ptr* 를 늘립니다. 함수에서 여러 번 **va_arg** 사용 하 여 목록에서 인수를 검색할 수 있습니다.

- **va_copy** 은 현재 상태의 인수 목록에 대 한 복사본을 만듭니다. *Src* 매개 변수는 이미 **va_start** 를 사용 하 여 초기화 해야 합니다. **va_arg** 호출로 업데이트 되었지만 **va_end** 를 사용 하 여 다시 설정 하지 않아야 합니다. *Dest* 에서 **va_arg** 에 의해 검색 되는 다음 인수는 *src* 에서 검색 된 다음 인수와 동일 합니다.

- 모든 인수가 검색 된 후 **va_end** 는 포인터를 **NULL** 로 다시 설정 합니다. 함수가 반환 되기 전에 **va_start** 또는 **va_copy** 를 사용 하 여 초기화 된 각 인수 목록에서 **va_end** 를 호출 해야 합니다.

> [!NOTE]
> VARARGS.H 형식의 매크로는 더 이상 사용되지 않으며 ANSI C89 표준이 적용되기 전에 작성된 이전 버전 코드와의 호환성을 위해서만 유지됩니다. 다른 모든 경우에는 STDARGS.H 형식의 매크로를 사용합니다.

[/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)을 사용하여 컴파일하는 경우 기본 형식 시스템과 CLR(공용 언어 시스템) 형식 시스템 간의 차이로 인해 이러한 매크로를 사용하는 프로그램이 예기치 않은 결과를 생성할 수 있습니다. 다음 프로그램을 살펴보세요.

```C
#include <stdio.h>
#include <stdarg.h>

void testit (int i, ...)
{
    va_list argptr;
    va_start(argptr, i);

    if (i == 0)
    {
        int n = va_arg(argptr, int);
        printf("%d\n", n);
    }
    else
    {
        char *s = va_arg(argptr, char*);
        printf("%s\n", s);
    }

    va_end(argptr);
}

int main()
{
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int
    testit(1, NULL);       // 2nd problem: NULL is not a char*
}
```

**Testit** 는 두 번째 매개 변수가 또는 일 것으로 예상 **`int`** **`char*`** 합니다. 전달 되는 인수는 0xffffffff ( **`unsigned int`** a, not **`int`** ) 및 **NULL** (실제로는 **`int`** 이 아님 **`char*`** )입니다. 네이티브 코드용으로 프로그램을 컴파일하면 다음 출력이 생성됩니다.

```Output
-1

(null)
```

## <a name="requirements"></a>요구 사항

**헤더:** \<stdio.h> 하거나 \<stdarg.h>

**사용 되지 않는 헤더:**\<varargs.h>

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

```C
// crt_va.c
// Compile with: cl /W3 /Tc crt_va.c
// The program below illustrates passing a variable
// number of arguments using the following macros:
//      va_start            va_arg              va_copy
//      va_end              va_list

#include <stdio.h>
#include <stdarg.h>
#include <math.h>

double deviation(int first, ...);

int main( void )
{
    /* Call with 3 integers (-1 is used as terminator). */
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));

    /* Call with 4 integers. */
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));

    /* Call with just -1 terminator. */
    printf("Deviation is: %f\n", deviation(-1));
}

/* Returns the standard deviation of a variable list of integers. */
double deviation(int first, ...)
{
    int count = 0, i = first;
    double mean = 0.0, sum = 0.0;
    va_list marker;
    va_list copy;

    va_start(marker, first);     /* Initialize variable arguments. */
    va_copy(copy, marker);       /* Copy list for the second pass */
    while (i != -1)
    {
        sum += i;
        count++;
        i = va_arg(marker, int);
    }
    va_end(marker);              /* Reset variable argument list. */
    mean = sum ? (sum / count) : 0.0;

    i = first;                  /* reset to calculate deviation */
    sum = 0.0;
    while (i != -1)
    {
        sum += (i - mean)*(i - mean);
        i = va_arg(copy, int);
    }
    va_end(copy);               /* Reset copy of argument list. */
    return count ? sqrt(sum / count) : 0.0;
}
```

```Output
Deviation is: 0.816497
Deviation is: 2.236068
Deviation is: 0.000000
```

## <a name="see-also"></a>참고 항목

[인수 액세스](../../c-runtime-library/argument-access.md)<br/>
[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
