---
description: '자세한 정보: fsetpos'
title: fsetpos
ms.date: 4/2/2020
api_name:
- fsetpos
- _o_fsetpos
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
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: e8259bcf4dba951bf6603fb5d4984db6ece0e266
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114223"
---
# <a name="fsetpos"></a>fsetpos

스트림 위치 표시기를 설정합니다.

## <a name="syntax"></a>구문

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>매개 변수

*스트림*<br/>
**FILE** 구조체에 대한 포인터입니다.

*pos*<br/>
위치 표시기 스토리지입니다.

## <a name="return-value"></a>반환 값

성공 하면 **fsetpos** 가 0을 반환 합니다. 오류가 발생 하면 함수는 0이 아닌 값을 반환 하 고 **errno** 를 errno에 정의 된 다음 매니페스트 상수 중 하나로 설정 합니다. H): **Ebadf**(파일에 액세스할 수 없거나 *스트림이* 가리키는 개체가 유효한 파일 구조가 아님을 의미 함) 또는 **EINVAL** 입니다 .이는 *stream* 또는 *pos* 에 대해 잘못 된 값이 전달 되었음을 의미 합니다. 잘못된 매개 변수가 전달되면 이러한 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)의 설명대로 잘못된 매개 변수 처리기를 호출합니다.

이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [_doserrno, errno, _sys_errlist 및 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)를 참조하세요.

## <a name="remarks"></a>설명

**Fsetpos** 함수는 스트림에 대 한 **fgetpos** 에 *대 한 이전* 호출에서 가져온 *pos* 의 값으로 *스트림에* 대 한 파일 위치 표시기를 설정 합니다. 함수는 파일 끝 표시기를 지우고 *스트림에서* [ungetc](ungetc-ungetwc.md) 의 효과를 실행 취소 합니다. **Fsetpos** 를 호출한 후 *스트림에* 대 한 다음 작업은 입력 또는 출력 중 하나일 수 있습니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[fgetpos](fgetpos.md)의 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
