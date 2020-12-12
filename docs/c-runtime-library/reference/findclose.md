---
description: '다음에 대 한 자세한 정보: _findclose'
title: _findclose
ms.date: 4/2/2020
api_name:
- _findclose
- _o__findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: 389a8aaf55605a1d9e3193c86ce500bf313fd631
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329203"
---
# <a name="_findclose"></a>_findclose

지정된 검색 핸들을 닫고 연결된 리소스를 해제합니다.

## <a name="syntax"></a>구문

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>매개 변수

*처리*<br/>
**_Findfirst** 에 대 한 이전 호출에서 반환 된 검색 핸들입니다.

## <a name="return-value"></a>반환 값

성공 하면 **_findclose** 가 0을 반환 합니다. 그렇지 않으면-1을 반환 하 고 **errno** 를 **enoent (** 로 설정 하 여 더 이상 일치 하는 파일을 찾을 수 없음을 나타냅니다.

## <a name="remarks"></a>설명

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_findclose**|\<io.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[시스템 호출](../../c-runtime-library/system-calls.md)<br/>
[파일 이름 검색 함수](../../c-runtime-library/filename-search-functions.md)<br/>
