---
description: '자세한 정보: Module:: GenericReleaseNotifier 클래스'
title: Module::GenericReleaseNotifier 클래스
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
ms.openlocfilehash: dd82da7c1b6b9a77c68b6d451bfa6dac31f51180
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186378"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier 클래스

현재 모듈의 마지막 개체가 해제될 때 이벤트 처리기를 호출합니다. 이벤트 처리기는 람다, 함수 또는 함수 포인터에 의해 지정됩니다.

## <a name="syntax"></a>구문

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>매개 변수

*T*<br/>
이벤트 처리기의 위치를 포함하는 데이터 멤버 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

이름                                                                                                     | 설명
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module:: GenericReleaseNotifier:: GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | `Module::GenericReleaseNotifier` 클래스의 새 인스턴스를 초기화합니다.

### <a name="public-methods"></a>Public 메서드

이름                                                                     | 설명
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module:: GenericReleaseNotifier:: Invoke](#genericreleasenotifier-invoke) | 현재 개체와 연결 된 이벤트 처리기를 호출 합니다 `Module::GenericReleaseNotifier` .

### <a name="protected-data-members"></a>보호된 데이터 멤버

Name                                                                          | 설명
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module:: GenericReleaseNotifier:: callback_](#genericreleasenotifier-callback) | 현재 개체와 연결 된 람다, 함수 또는 함수 포인터 이벤트 처리기를 포함 합니다 `Module::GenericReleaseNotifier` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>요구 사항

**헤더:** module .h

**네임스페이스:** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a> Module:: GenericReleaseNotifier:: callback_

현재 개체와 연결 된 람다, 함수 또는 함수 포인터 이벤트 처리기를 포함 합니다 `Module::GenericReleaseNotifier` .

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a> Module:: GenericReleaseNotifier:: GenericReleaseNotifier

`Module::GenericReleaseNotifier` 클래스의 새 인스턴스를 초기화합니다.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>매개 변수

*콜백(callback)*<br/>
괄호 함수 연산자 ()를 사용 하 여 호출할 수 있는 람다, 함수 또는 함수 포인터 이벤트 처리기 `()` 입니다.

*릴리스*<br/>
**`true`** 기본 [Module:: ReleaseNotifier:: Release ()](module-releasenotifier-class.md#releasenotifier-release) 메서드를 호출할 수 있도록 지정 하려면를 지정 하 고 그렇지 않으면를 지정 **`false`** 합니다.

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a> Module:: GenericReleaseNotifier:: Invoke

현재 개체와 연결 된 이벤트 처리기를 호출 합니다 `Module::GenericReleaseNotifier` .

```cpp
void Invoke();
```
