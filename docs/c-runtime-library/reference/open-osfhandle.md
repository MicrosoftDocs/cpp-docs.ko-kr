---
title: _open_osfhandle | Microsoft Docs
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af3783420389dc008e39c818c39406f0b2af8af5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569838"
---
# <a name="openosfhandle"></a>_open_osfhandle

C 런타임 파일 설명자를 기존 운영 체제 파일 핸들에 연결합니다.

## <a name="syntax"></a>구문

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>매개 변수

*osfhandle*<br/>
운영 체제 파일 핸들입니다.

*flags*<br/>
허용되는 연산의 유형입니다.

## <a name="return-value"></a>반환 값

성공 하면 **_open_osfhandle** C 런타임 파일 설명자를 반환 합니다. 그렇지 않으면-1을 반환 합니다.

## <a name="remarks"></a>설명

**_open_osfhandle** 함수 C 런타임 파일 설명자를 할당 하 고 지정 된 운영 체제 파일 핸들에 연결 *osfhandle*합니다. 컴파일러 경고를 방지 하려면 캐스팅는 *osfhandle* 인수 **처리** 를 **intptr_t**합니다. *플래그* 인수는 하나에서 구성 하는 정수 식 또는에 정의 된 매니페스트 상수 중 \<fcntl.h > 합니다. 매니페스트 상수를 두 개 이상의 형식으로 사용 하는 경우는 *플래그* 인수를 해당 상수는 비트 OR 연산자로 결합 됩니다 ( **&#124;** ).

이러한 매니페스트 상수에 정의 된 \<fcntl.h >:

|||
|-|-|
**\_O\_추가**|모든 쓰기 작업 전에 파일 포인터를 파일 끝에 배치합니다.
**\_O\_RDONLY**|읽기 전용으로 파일을 엽니다.
**\_O\_TEXT**|파일을 텍스트(변환됨) 모드에서 엽니다.
**\_O\_WTEXT**|파일을 유니코드(변환된 UTF-16) 모드에서 엽니다.

**_open_osfhandle** 호출 파일 설명자에 Win32 파일 핸들의 소유권을 전송 합니다. 사용 하 여 열린 파일을 닫으려면 **_open_osfhandle**, 호출 [ \_닫습니다](close.md)합니다. 호출 하 여 기본 OS 파일 핸들도 닫혀 **_close**이므로 Win32 함수를 호출할 필요는 없습니다 **CloseHandle** 원래 핸들입니다. 파일 설명자가 소유 하는 경우는 **파일 &#42;**  다음 호출 하는 스트림 [fclose](fclose-fcloseall.md) 그에 **파일 &#42;**  스트림 파일 설명자를 또한 종료 및 기본 핸들입니다. 이 경우 호출 하지 않으면 **_close** 파일 설명자에 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고자료

[파일 처리](../../c-runtime-library/file-handling.md)<br/>
