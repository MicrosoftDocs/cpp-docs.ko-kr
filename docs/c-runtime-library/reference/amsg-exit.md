---
description: '다음에 대 한 자세한 정보: _amsg_exit'
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
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
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: d00283f3222a217db8337129f66b377f7c0d494e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211403"
---
# <a name="_amsg_exit"></a>_amsg_exit

지정된 런타임 오류 메시지를 내보낸 다음 오류 코드 255와 함께 애플리케이션을 종료합니다.

## <a name="syntax"></a>구문

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>매개 변수

*rterrnum*<br/>
시스템 정의 런타임 오류 메시지의 ID 번호입니다.

## <a name="remarks"></a>설명

이 함수는 콘솔 애플리케이션에 대한 런타임 오류 메시지를 **stderr** 로 내보내거나 Windows 애플리케이션에 대한 메시지를 메시지 상자에 표시합니다. 디버그 모드에서 종료하기 전에 디버거를 호출하도록 선택할 수 있습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|_amsg_exit|internal.h|
