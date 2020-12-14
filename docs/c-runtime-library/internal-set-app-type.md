---
description: '다음에 대 한 자세한 정보: __set_app_type'
title: __set_app_type
ms.date: 11/04/2016
api_name:
- __set_app_type
- _set_app_type
api_location:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __set_app_type
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
ms.openlocfilehash: 19aafebc4f7fd848804e21193332fb693af56010
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246768"
---
# <a name="__set_app_type"></a>__set_app_type

현재 애플리케이션 형식을 설정합니다.

## <a name="syntax"></a>구문

```cpp
void __set_app_type (
   int at
   )
```

#### <a name="parameters"></a>매개 변수

*at*<br/>
애플리케이션 형식을 나타내는 값입니다. 가능한 값은 다음과 같습니다.

|값|설명|
|-----------|-----------------|
|_UNKNOWN_APP|알 수 없는 애플리케이션 형식입니다.|
|_CONSOLE_APP|콘솔(명령줄) 애플리케이션입니다.|
|_GUI_APP|GUI(Windows) 애플리케이션입니다.|

## <a name="remarks"></a>설명

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__set_app_type|internal.h|
