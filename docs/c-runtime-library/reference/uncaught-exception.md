---
description: '다음에 대 한 자세한 정보: __uncaught_exception'
title: __uncaught_exception
ms.date: 11/04/2016
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 22417e10e96e70faf2754ae2d8bb03b90bdbe020
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124815"
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
