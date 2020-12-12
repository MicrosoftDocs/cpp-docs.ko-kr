---
description: '자세한 정보: Module:: MethodReleaseNotifier 클래스'
title: Module::MethodReleaseNotifier 클래스
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: 6c0b2569abe8dbebde893bb7c8aee84abc3d8047
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186365"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 클래스

현재 모듈의 마지막 개체가 해제될 때 이벤트 처리기를 호출합니다. 이벤트 처리기는 개체 및 해당 포인터에 대 한 포인터 멤버에 의해 지정 됩니다.

## <a name="syntax"></a>구문

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
멤버 함수가 이벤트 처리기 인 개체의 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                                                                 | 설명
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module:: MethodReleaseNotifier:: MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | `Module::MethodReleaseNotifier` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                                                                   | 설명
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module:: MethodReleaseNotifier:: Invoke](#methodreleasenotifier-invoke) | 현재 개체와 연결 된 이벤트 처리기를 호출 합니다 `Module::MethodReleaseNotifier` .

### <a name="protected-data-members"></a>보호된 데이터 멤버

Name                                                                    | 설명
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module:: MethodReleaseNotifier:: method_](#methodreleasenotifier-method) | 현재 개체에 대 한 이벤트 처리기에 대 한 포인터를 보유 `Module::MethodReleaseNotifier` 합니다.
[Module:: MethodReleaseNotifier:: object_](#methodreleasenotifier-object) | 멤버 함수가 현재 개체에 대 한 이벤트 처리기 인 개체에 대 한 포인터를 보유 `Module::MethodReleaseNotifier` 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임스페이스:** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a> Module:: MethodReleaseNotifier:: Invoke

현재 개체와 연결 된 이벤트 처리기를 호출 합니다 `Module::MethodReleaseNotifier` .

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a> Module:: MethodReleaseNotifier:: method_

현재 개체에 대 한 이벤트 처리기에 대 한 포인터를 보유 `Module::MethodReleaseNotifier` 합니다.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a> Module:: MethodReleaseNotifier:: MethodReleaseNotifier

`Module::MethodReleaseNotifier` 클래스의 새 인스턴스를 초기화합니다.

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>매개 변수

*object*<br/>
멤버 함수가 이벤트 처리기 인 개체입니다.

*방법이*<br/>
이벤트 처리기 인 parameter *개체* 의 멤버 함수입니다.

*릴리스*<br/>
**`true`** 기본 [Module:: ReleaseNotifier:: Release ()](module-releasenotifier-class.md#releasenotifier-release) 메서드를 호출할 수 있도록 지정 하려면를 지정 하 고 그렇지 않으면를 지정 **`false`** 합니다.

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a> Module:: MethodReleaseNotifier:: object_

멤버 함수가 현재 개체에 대 한 이벤트 처리기 인 개체에 대 한 포인터를 보유 `Module::MethodReleaseNotifier` 합니다.

```cpp
T* object_;
```
