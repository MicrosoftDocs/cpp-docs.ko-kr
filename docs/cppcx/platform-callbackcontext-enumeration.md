---
description: '자세한 정보: Platform:: CallbackContext 열거형'
title: Platform::CallbackContext 열거형
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 36c30b674065f42f7d50a403d1506344ffcfecac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170973"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext 열거형

콜백 함수(이벤트 처리기)가 실행되는 스레드 컨텍스트를 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>멤버

|형식 코드|설명|
|---------------|-----------------|
|모두|콜백 함수가 모든 스레드 컨텍스트에서 실행될 수 있습니다.|
|동일|콜백 함수가 비동기 작업을 시작한 스레드 컨텍스트에서만 실행될 수 있습니다.|

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타 데이터:** platform.object
