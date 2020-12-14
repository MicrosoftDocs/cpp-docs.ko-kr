---
description: '다음에 대 한 자세한 정보: _rmtmp'
title: _rmtmp
ms.date: 4/2/2020
api_name:
- _rmtmp
- _o__rmtmp
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _rmtmp
helpviewer_keywords:
- removing temporary files
- _rmtmp function
- files [C++], temporary
- rmtmp function
- files [C++], removing
- temporary files [C++], removing
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
ms.openlocfilehash: fd87dd407b2e392d197e7eb407bc307b48ea2263
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250194"
---
# <a name="_rmtmp"></a>_rmtmp

임시 파일을 제거합니다.

## <a name="syntax"></a>구문

```C

int _rmtmp( void );
```

## <a name="return-value"></a>Return Value

**_rmtmp** 는 닫히고 삭제 된 임시 파일의 수를 반환 합니다.

## <a name="remarks"></a>설명

**_Rmtmp** 함수는 현재 디렉터리에 있는 모든 임시 파일을 정리 합니다. 함수는 **tmpfile** 에 의해 생성 된 파일만 제거 합니다. 임시 파일을 만든 디렉터리와 동일한 디렉터리 에서만 사용 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_rmtmp**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="example"></a>예제

[tmpfile](tmpfile.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_flushall](flushall.md)<br/>
[tmpfile](tmpfile.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
