---
description: '다음에 대 한 자세한 정보: _set_app_type'
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: cd04f1c17f7876c08f8eafb4ef77960073fb3f33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277104"
---
# <a name="_set_app_type"></a>_set_app_type

시작 시에 앱이 콘솔 앱인지 아니면 GUI 앱인지를 CRT에 알려 주는 데 사용되는 내부 함수입니다.

## <a name="syntax"></a>구문

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>매개 변수

*appType*<br/>
애플리케이션 형식을 나타내는 값입니다. 가능한 값은 다음과 같습니다.

|값|설명|
|----------------|-----------------|
|_crt_unknown_app|알 수 없는 애플리케이션 형식입니다.|
|_crt_console_app|콘솔(명령줄) 애플리케이션입니다.|
|_crt_gui_app|GUI(Windows) 애플리케이션입니다.|

## <a name="remarks"></a>설명

일반적으로는 이 함수를 호출할 필요가 없습니다. 이 함수는 앱에서 `main`이 호출되기 전에 실행되는 C 런타임 시작 코드의 일부분입니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|_set_app_type|process.h|
