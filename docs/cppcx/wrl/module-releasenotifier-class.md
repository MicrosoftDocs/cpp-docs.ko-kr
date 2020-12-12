---
description: '자세한 정보: Module:: ReleaseNotifier 클래스'
title: Module::ReleaseNotifier 클래스
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
ms.openlocfilehash: ebb4d949cbb1e7230894fa24a523e4d6b6cd2657
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186261"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 클래스

모듈의 마지막 개체가 해제될 때 이벤트 처리기를 호출합니다.

## <a name="syntax"></a>구문

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                                                | 설명
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module:: ReleaseNotifier:: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | 클래스의 현재 인스턴스를 초기화 `Module::ReleaseNotifier` 합니다.
[Module:: ReleaseNotifier:: ReleaseNotifier](#releasenotifier-releasenotifier)        | `Module::ReleaseNotifier` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                                                         | 설명
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module:: ReleaseNotifier:: Invoke](#releasenotifier-invoke)   | 구현될 때 모듈의 마지막 개체가 해제되면 이벤트 처리기를 호출합니다.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | `Module::ReleaseNotifier`의 매개 변수를 사용 하 여 개체를 생성 한 경우 현재 개체를 삭제 **`true`** 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ReleaseNotifier`

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임스페이스:** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a> Module:: ReleaseNotifier:: ~ ReleaseNotifier

클래스의 현재 인스턴스를 초기화 `Module::ReleaseNotifier` 합니다.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a> Module:: ReleaseNotifier:: Invoke

구현될 때 모듈의 마지막 개체가 해제되면 이벤트 처리기를 호출합니다.

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a> Module:: ReleaseNotifier:: Release

`Module::ReleaseNotifier`의 매개 변수를 사용 하 여 개체를 생성 한 경우 현재 개체를 삭제 **`true`** 합니다.

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a> Module:: ReleaseNotifier:: ReleaseNotifier

`Module::ReleaseNotifier` 클래스의 새 인스턴스를 초기화합니다.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>매개 변수

*릴리스*<br/>
**`true`** 메서드가 호출 될 때이 인스턴스를 삭제 하려면이 `Release` 고, **`false`** 이 인스턴스를 삭제 하지 않으려면입니다.
