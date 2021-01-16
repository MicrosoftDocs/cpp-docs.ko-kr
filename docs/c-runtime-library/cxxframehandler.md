---
description: '다음에 대 한 자세한 정보: __CxxFrameHandler'
title: __CxxFrameHandler
ms.date: 1/14/2021
api_name:
- __CxxFrameHandler
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __CxxFrameHandler
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
ms.openlocfilehash: 0bf82b3a247505d052f1d64edc63bb9cd76a1dcb
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243192"
---
# <a name="__cxxframehandler"></a>__CxxFrameHandler

내부 CRT 함수입니다. CRT에서 구조화된 예외 프레임을 처리하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
EXCEPTION_DISPOSITION __CxxFrameHandler(
      EHExceptionRecord  *pExcept,
      EHRegistrationNode *pRN,
      void               *pContext,
      DispatcherContext  *pDC
   )
```

#### <a name="parameters"></a>매개 변수

*pExcept*<br/>
가능한 문에 전달 되는 예외 레코드입니다 **`catch`** .

*.Prn*<br/>
예외를 처리하는 데 사용되는 스택 프레임에 대한 동적 정보입니다. 자세한 내용은 ehdata.h를 참조하세요.

*pContext*<br/>
컨텍스트입니다. Intel 프로세서에는 사용되지 않습니다.

*컨트롤러가*<br/>
함수 시작 및 스택 프레임에 대한 추가 정보입니다.

## <a name="return-value"></a>반환 값

[try-except Statement](../cpp/try-except-statement.md)에서 사용하는 *필터 식* 값 중 하나입니다.

## <a name="remarks"></a>설명

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h, ehdata.h|
