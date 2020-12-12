---
description: '자세히 알아보기: 구조 수동'
title: HANDLETraits 구조체
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
ms.openlocfilehash: c3eef03c724b1ba868ba67ed251acdb310d8b66f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250025"
---
# <a name="handletraits-structure"></a>HANDLETraits 구조체

핸들의 공통 특성을 정의 합니다.

## <a name="syntax"></a>구문

```cpp
struct HANDLETraits;
```

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name   | 설명
------ | ---------------------
`Type` | 핸들의 동의어입니다.

### <a name="public-methods"></a>Public 메서드

이름                                              | 설명
------------------------------------------------- | -----------------------------
[:: Close 수동](#close)                     | 지정 된 핸들을 닫습니다.
[해당:: GetInvalidValue 수동 작업](#getinvalidvalue) | 는 잘못 된 핸들을 나타냅니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`HANDLETraits`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼:: 핸드

## <a name="handletraitsclose"></a><a name="close"></a> :: Close 수동

지정 된 핸들을 닫습니다.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
닫을 핸들입니다.

### <a name="return-value"></a>반환 값

**`true`***핸들을* 성공적으로 닫았습니다. 그렇지 않으면 **`false`** 입니다.

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a> 해당:: GetInvalidValue 수동 작업

는 잘못 된 핸들을 나타냅니다.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>반환 값

INVALID_HANDLE_VALUE 항상를 반환 합니다. (INVALID_HANDLE_VALUE는 Windows에서 정의 됩니다.)
