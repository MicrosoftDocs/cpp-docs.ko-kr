---
description: '자세히 알아보기: FactoryCache Structure'
title: FactoryCache 구조체
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 3e9ee084a063eb8094c309dee412a8793801921b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198555"
---
# <a name="factorycache-structure"></a>FactoryCache 구조체

는 Windows 런타임 c + + 템플릿 라이브러리 인프라를 지원 하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>설명

클래스 팩터리의 위치 및 등록 된 wrt 또는 COM 클래스 개체를 식별 하는 값을 포함 합니다.

## <a name="members"></a>멤버

### <a name="public-data-members"></a>공용 데이터 멤버

Name                              | 설명
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache:: cookie](#cookie)   | 등록 된 Windows 런타임 또는 COM 클래스 개체를 식별 하는 값을 포함 하며 나중에 개체의 등록을 취소 하는 데 사용 됩니다.
[FactoryCache:: factory](#factory) | Windows 런타임 또는 COM 클래스 팩터리를 가리킵니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`FactoryCache`

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="factorycachecookie"></a><a name="cookie"></a> FactoryCache:: cookie

는 Windows 런타임 c + + 템플릿 라이브러리 인프라를 지원 하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>설명

등록 된 Windows 런타임 또는 COM 클래스 개체를 식별 하는 값을 포함 하며 나중에 개체의 등록을 취소 하는 데 사용 됩니다.

## <a name="factorycachefactory"></a><a name="factory"></a> FactoryCache:: factory

는 Windows 런타임 c + + 템플릿 라이브러리 인프라를 지원 하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>설명

Windows 런타임 또는 COM 클래스 팩터리를 가리킵니다.
