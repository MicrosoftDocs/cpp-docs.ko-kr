---
description: '자세한 정보: CreatorMap 구조체'
title: CreatorMap 구조체
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 0ef3b441390a22a6c4b35f274857ccb58de030d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273048"
---
# <a name="creatormap-structure"></a>CreatorMap 구조체

는 Windows 런타임 c + + 템플릿 라이브러리 인프라를 지원 하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>설명

개체를 초기화, 등록 및 등록 취소 하는 방법에 대 한 정보를 포함 합니다.

`CreatorMap`에는 다음 정보가 포함되어 있습니다.

- 개체를 초기화, 등록 및 등록 취소 하는 방법입니다.

- 클래식 COM 또는 Windows 런타임 팩터리에 따라 활성화 데이터를 비교 하는 방법입니다.

- 인터페이스에 대 한 팩터리 캐시 및 서버 이름에 대 한 정보입니다.

## <a name="members"></a>멤버

### <a name="public-data-members"></a>공용 데이터 멤버

Name                                          | 설명
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap:: activationId](#activationid)     | 클래식 COM 클래스 ID 또는 Windows 런타임 이름으로 식별 되는 개체 ID를 나타냅니다.
[CreatorMap:: factoryCache](#factorycache)     | 에 대 한 팩터리 캐시에 포인터를 저장 `CreatorMap` 합니다.
[CreatorMap:: factoryCreator](#factorycreator) | 지정 된에 대 한 팩터리를 만듭니다 `CreatorMap` .
[CreatorMap:: serverName](#servername)         | 의 서버 이름을 저장 `CreatorMap` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CreatorMap`

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="creatormapactivationid"></a><a name="activationid"></a> CreatorMap:: activationId

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>매개 변수

*가*<br/>
인터페이스 ID입니다.

*Getrunti의 Ame*<br/>
개체의 Windows 런타임 이름을 검색 하는 함수입니다.

### <a name="remarks"></a>설명

클래식 COM 클래스 ID 또는 Windows 런타임 이름으로 식별 되는 개체 ID를 나타냅니다.

## <a name="creatormapfactorycache"></a><a name="factorycache"></a> CreatorMap:: factoryCache

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>설명

에 대 한 팩터리 캐시에 포인터를 저장 `CreatorMap` 합니다.

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a> CreatorMap:: factoryCreator

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>매개 변수

*currentflags*<br/>
[RuntimeClassType](runtimeclasstype-enumeration.md) 열거자 중 하나입니다.

*엔트리의*<br/>
CreatorMap입니다.

*iidClassFactory*<br/>
클래스 팩터리의 인터페이스 ID입니다.

*공장*<br/>
작업이 완료 되 면 클래스 팩터리의 주소입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

지정 된 CreatorMap에 대 한 팩터리를 만듭니다.

## <a name="creatormapservername"></a><a name="servername"></a> CreatorMap:: serverName

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>설명

CreatorMap의 서버 이름을 저장 합니다.
