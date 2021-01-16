---
description: '자세한 정보: 예기치 않은 (CRT)'
title: unexpected(CRT)
ms.date: 1/14/2021
api_name:
- unexpected
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 098d686e7c33d17020990b1db168d95c327d5112
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242906"
---
# <a name="unexpected-crt"></a>`unexpected` CRT

**`terminate`** 또는를 사용 하 여 지정한 함수를 호출 **`set_unexpected`** 합니다.

## <a name="syntax"></a>구문

```C
void unexpected( void );
```

## <a name="remarks"></a>설명

**`unexpected`** 루틴은 c + + 예외 처리의 현재 구현과 함께 사용 되지 않습니다. **`unexpected`****`terminate`** 기본적으로를 호출 합니다. 사용자 지정 종료 함수를 작성 하 여이 기본 동작을 변경할 수 있습니다. **`set_unexpected`** 함수 이름을 인수로 사용 하 여를 호출 합니다. **`unexpected`** 에 전달 된 마지막 함수를 호출 **`set_unexpected`** 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**`unexpected`**|`<eh.h>`|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[예외 처리 루틴](../../c-runtime-library/exception-handling-routines.md)<br/>
[중단이](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[끝나야](terminate-crt.md)<br/>
