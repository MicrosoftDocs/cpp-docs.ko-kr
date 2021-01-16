---
description: '다음에 대 한 자세한 정보: __uncaught_exception'
title: __uncaught_exception
ms.date: 1/14/2021
api_name:
- __uncaught_exception
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
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: dd3fb85a0264005b0c26f1030046661c5b291972
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243049"
---
# <a name="__uncaught_exception"></a>__uncaught_exception

하나 이상의 예외가 throw 되었지만 try-catch 문의 해당 블록에서 아직 처리 되지 않은 경우를 나타냅니다 **`catch`** . [](../../cpp/try-throw-and-catch-statements-cpp.md)

## <a name="syntax"></a>구문

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Return Value

**`true`****`try`** 일치 하는 블록이 초기화 될 때까지 블록에서 예외가 throw 되 면 **`catch`** 이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="remarks"></a>설명

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>참고 항목

[try, throw 및 catch 문(C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
