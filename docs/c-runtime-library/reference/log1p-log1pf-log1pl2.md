---
title: log1p, log1pf, log1pl2
ms.date: 04/05/2018
api_name:
- log1p
- log1pf
- log1pl
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
ms.openlocfilehash: aad6675a832e1715c505026fe11ffe77f1f6d275
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953212"
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

1을 더한 지정된 값의 자연 로그를 계산합니다.

## <a name="syntax"></a>구문

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);
```

### <a name="parameters"></a>매개 변수

*x*<br/>
부동 소수점 인수입니다.

## <a name="return-value"></a>반환 값

성공 하면 (*x* + 1)의 자연 (밑수-*e*) 로그를 반환 합니다.

그렇지 않으면 다음 값 중 하나를 반환할 수 있습니다.

|입력|결과|SEH 예외|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Denormals|입력과 동일함|UNDERFLOW||
|±0|입력과 동일함|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|±SNaN|입력과 동일함|INVALID||
|± QNaN, 무한|입력과 동일함|||

*X* =-1 인 경우 **ERRNO** 값은 ERANGE로 설정 됩니다. *X* <-1 인 경우 **Errno** 값은 **edom** 으로 설정 됩니다.

## <a name="remarks"></a>설명

*X* 가 0에 가까워지면 **log1p** 함수는를 `log(x + 1)` 사용 하는 것 보다 더 정확 하 게 사용할 수 있습니다.

는 C++ 오버 로드를 허용 하기 때문에 **float** 및 **long** **double** 형식을 사용 하 고 반환 하는 **log1p** 의 오버 로드를 호출할 수 있습니다. C 프로그램에서 **log1p** 은 항상 **double**을 사용 하 고 반환 합니다.

*X* 가 자연 수 인 경우이 함수는 (*x* -1)의 계승값에 대 한 로그를 반환 합니다.

## <a name="requirements"></a>요구 사항

|기능|C 헤더|C++ 헤더|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
