---
title: _byteswap_uint64, _byteswap_ulong, _byteswap_ushort | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _byteswap_uint64
- _byteswap_ulong
- _byteswap_ushort
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- byteswap_ulong
- _byteswap_ulong
- byteswap_uint64
- _byteswap_ushort
- _byteswap_uint64
- byteswap_ushort
dev_langs:
- C++
helpviewer_keywords:
- _byteswap_uint64 function
- byteswap_uint64 function
- swapping bytes
- byte swapping
- byteswap_ushort function
- _byteswap_ushort function
- bytes, swapping
- byteswap_ulong function
- _byteswap_ulong function
ms.assetid: 83bda211-f02f-4cf0-8a78-d6de1f175970
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c845d2c14ee721fd2fd28fbdb0857cedecfab561
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="byteswapuint64-byteswapulong-byteswapushort"></a>_byteswap_uint64, _byteswap_ulong, _byteswap_ushort

정수에서 바이트의 순서를 반대로 바꿉니다.

## <a name="syntax"></a>구문

```C
unsigned short _byteswap_ushort ( unsigned short val );
unsigned long _byteswap_ulong ( unsigned long val );
unsigned __int64 _byteswap_uint64 ( unsigned __int64 val );
```

### <a name="parameters"></a>매개 변수

*val*<br/>
바이트 순서를 반대로 바꿀 정수입니다.

## <a name="requirements"></a>요구 사항

|루틴|필수 헤더|
|-------------|---------------------|
|**_byteswap_ushort**|\<stdlib.h>|
|**_byteswap_ulong**|\<stdlib.h>|
|**_byteswap_uint64**|\<stdlib.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```C
// crt_byteswap.c
#include <stdlib.h>

int main()
{
   unsigned __int64 u64 = 0x0102030405060708;
   unsigned long ul = 0x01020304;

   printf("byteswap of %I64x = %I64x\n", u64, _byteswap_uint64(u64));
   printf("byteswap of %Ix = %Ix", ul, _byteswap_ulong(ul));
}
```

```Output
byteswap of 102030405060708 = 807060504030201
byteswap of 1020304 = 4030201
```

## <a name="see-also"></a>참고자료

[범주별으로 유니버설 C 런타임 루틴](../../c-runtime-library/run-time-routines-by-category.md)<br/>
