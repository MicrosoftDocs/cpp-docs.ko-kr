---
description: 다음에 대해 자세히 알아보세요. Verify인터페이스 도우미 구조
title: VerifyInterfaceHelper 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: a9b51eac55666d15b8362fc070d0feb731e9674d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135033"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper 구조체

는 Windows 런타임 c + + 템플릿 라이브러리 인프라를 지원 하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>매개 변수

*I*<br/>
확인할 인터페이스입니다.

*isWinRTInterface*

## <a name="remarks"></a>설명

템플릿 매개 변수로 지정 된 인터페이스가 특정 요구 사항을 충족 하는지 확인 합니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

이름                                            | 설명
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify 메서드](#verify) | 현재 템플릿 매개 변수에 지정 된 인터페이스가 특정 요구 사항을 충족 하는지 확인 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`VerifyInterfaceHelper`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a> Verify인터페이스 도우미:: Verify

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
static void Verify();
```

### <a name="remarks"></a>설명

현재 템플릿 매개 변수에 지정 된 인터페이스가 특정 요구 사항을 충족 하는지 확인 합니다.
