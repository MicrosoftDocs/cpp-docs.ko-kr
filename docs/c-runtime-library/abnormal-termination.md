---
description: '다음에 대 한 자세한 정보: _abnormal_termination'
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: 2fa4b82deeebda7624d8ac96be675efc100ae926
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224285"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

**`__finally`** 시스템에서 종료 처리기의 내부 목록을 실행 하는 동안 [try-catch 문의](../cpp/try-finally-statement.md) 블록을 입력 했는지 여부를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Return Value

**`true`** 시스템이 스택을 해제 하면 *이 고* , 그렇지 않으면입니다. 그렇지 않으면 **`false`** 입니다.

## <a name="remarks"></a>설명

해제 예외를 관리하기 위해 사용되는 내부 함수이며 사용자 코드에서 호출할 수 없습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>참조

[try-finally 문](../cpp/try-finally-statement.md)
