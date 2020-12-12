---
description: '자세히 알아보기: 수동 Let 클래스'
title: HandleT 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: 608433193729e3d9be5b9490c469bf0b04d3531c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250012"
---
# <a name="handlet-class"></a>HandleT 클래스

개체에 대한 핸들을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>매개 변수

*HandleTraits*<br/>
핸들의 공통 특성을 정의 하는 [해당 구조체의 인스턴스를 만듭니다](handletraits-structure.md) .

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

Name     | 설명
-------- | -----------------------------
`Traits` | `HandleTraits`의 동의어입니다.

### <a name="public-constructors"></a>Public 생성자

이름                                | 설명
----------------------------------- | --------------------------------------------------
[수동 Let:: 수동 Let](#handlet)        | `HandleT` 클래스의 새 인스턴스를 초기화합니다.
[수동 Let:: ~ 핸드 Let](#tilde-handlet) | 클래스의 인스턴스를 초기화 하지 `HandleT` 않습니다.

### <a name="public-methods"></a>Public 메서드

이름                         | 설명
---------------------------- | ----------------------------------------------------------------------
[수동 Let:: Attach](#attach)   | 지정 된 핸들을 현재 개체와 연결 `HandleT` 합니다.
[수동 Let:: Close](#close)     | 현재 `HandleT` 개체를 닫습니다.
[수동 Let::D etach](#detach)   | 현재 개체를 `HandleT` 내부 핸들에서 분리 합니다.
[수동 Let:: Get](#get)         | 내부 핸들의 값을 가져옵니다.
[수동 Let:: IsValid](#isvalid) | 현재 `HandleT` 개체가 핸들을 나타내는지 여부를 나타냅니다.

### <a name="protected-methods"></a>Protected 메서드

Name                                     | 설명
---------------------------------------- | ------------------------------------
[수동 Let:: InternalClose](#internalclose) | 현재 `HandleT` 개체를 닫습니다.

### <a name="public-operators"></a>Public 연산자

Name                                   | 설명
-------------------------------------- | ----------------------------------------------------------------------------------
[핸드 Let:: operator =](#operator-assign) | 지정 된 개체의 값을 `HandleT` 현재 `HandleT` 개체로 이동 합니다.

### <a name="protected-data-members"></a>보호된 데이터 멤버

Name                        | 설명
--------------------------- | ----------------------------------------------------------------
[수동 Let:: handle_](#handle) | 개체가 나타내는 핸들을 포함 합니다 `HandleT` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`HandleT`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**네임 스페이스:** Microsoft:: WRL:: 래퍼

## <a name="handlethandlet"></a><a name="tilde-handlet"></a> 수동 Let:: ~ 핸드 Let

클래스의 인스턴스를 초기화 하지 `HandleT` 않습니다.

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a> 수동 Let:: Attach

지정 된 핸들을 현재 개체와 연결 `HandleT` 합니다.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
핸들입니다.

## <a name="handletclose"></a><a name="close"></a> 수동 Let:: Close

현재 `HandleT` 개체를 닫습니다.

```cpp
void Close();
```

### <a name="remarks"></a>설명

현재의 기반이 되는 핸들이 `HandleT` 닫혀 있고 `HandleT` 이 잘못 된 상태로 설정 된 경우

핸들이 제대로 닫히지 않은 경우 호출 스레드에서 예외가 발생합니다.

## <a name="handletdetach"></a><a name="detach"></a> 수동 Let::D etach

현재 개체를 `HandleT` 내부 핸들에서 분리 합니다.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>반환 값

내부 핸들입니다.

### <a name="remarks"></a>설명

이 작업이 완료 되 면 현재이 `HandleT` 잘못 된 상태로 설정 됩니다.

## <a name="handletget"></a><a name="get"></a> 수동 Let:: Get

내부 핸들의 값을 가져옵니다.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>반환 값

핸들입니다.

## <a name="handlethandle_"></a><a name="handle"></a> 수동 Let:: handle_

개체가 나타내는 핸들을 포함 합니다 `HandleT` .

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a> 수동 Let:: 수동 Let

`HandleT` 클래스의 새 인스턴스를 초기화합니다.

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
핸들입니다.

### <a name="remarks"></a>설명

첫 번째 생성자는 `HandleT` 개체에 대 한 유효한 핸들이 아닌 개체를 초기화 합니다. 두 번째 생성자는 `HandleT` 매개 변수 *h* 에서 새 개체를 만듭니다.

## <a name="handletinternalclose"></a><a name="internalclose"></a> 수동 Let:: InternalClose

현재 `HandleT` 개체를 닫습니다.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>반환 값

**`true`** 현재가 `HandleT` 성공적으로 닫혔으면이 고, 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

`InternalClose()` 는 **`protected`** 입니다.

## <a name="handletisvalid"></a><a name="isvalid"></a> 수동 Let:: IsValid

현재 `HandleT` 개체가 핸들을 나타내는지 여부를 나타냅니다.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>반환 값

**`true`**`HandleT`이 핸들을 나타내면이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="handletoperator"></a><a name="operator-assign"></a> 핸드 Let:: operator =

지정 된 개체의 값을 `HandleT` 현재 `HandleT` 개체로 이동 합니다.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>매개 변수

*h*<br/>
핸들에 대 한 rvalue 참조입니다.

### <a name="return-value"></a>반환 값

현재 개체에 대 한 참조 `HandleT` 입니다.

### <a name="remarks"></a>설명

이 작업은 `HandleT` 매개 변수 *h* 로 지정 된 개체를 무효화 합니다.
