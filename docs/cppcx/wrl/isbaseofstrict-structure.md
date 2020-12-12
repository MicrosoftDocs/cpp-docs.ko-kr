---
description: '자세한 정보: IsBaseOfStrict 구조체'
title: IsBaseOfStrict 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: bcdab9c4b6b5a2ab108b59d3127c08b53589e16a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298957"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 구조체

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>매개 변수

*하단*<br/>
기본 형식입니다.

*파생*<br/>
파생 된 형식입니다.

## <a name="remarks"></a>설명

형식 하나가 다른 형식의 기본 형식인지 테스트합니다.

첫 번째 템플릿은 형식이 기본 형식에서 파생 되는지 여부를 테스트 합니다 .이는 또는을 생성할 수 있습니다 **`true`** **`false`** . 두 번째 템플릿은 형식이 자체에서 파생 되는지 여부를 테스트 하 여 항상을 생성 **`false`** 합니다.

## <a name="members"></a>멤버

### <a name="public-constants"></a>공용 상수

Name                            | 설명
------------------------------- | --------------------------------------------------
[IsBaseOfStrict:: value](#value) | 한 형식이 다른 형식에 대 한 기본 형식 인지 여부를 나타냅니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IsBaseOfStrict`

## <a name="requirements"></a>요구 사항

**헤더:** internal. h

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="isbaseofstrictvalue"></a><a name="value"></a> IsBaseOfStrict:: value

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>설명

한 형식이 다른 형식에 대 한 기본 형식 인지 여부를 나타냅니다.

`value` 형식이 형식의 **`true`** 기본 클래스 이면이 고 `Base` `Derived` , 그렇지 않으면입니다 **`false`** .
