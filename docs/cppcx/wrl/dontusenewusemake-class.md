---
description: '자세히 알아보기: DontUseNewUseMake 클래스'
title: DontUseNewUseMake 클래스
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: f6b6740e472123e59565e3bad16e4a535a4e17fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272905"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>설명

에서 연산자를 사용할 수 없습니다 `new` `RuntimeClass` . 따라서 대신이 [함수](make-function.md) 를 사용 해야 합니다.

## <a name="members"></a>멤버

### <a name="public-operators"></a>Public 연산자

Name                                             | 설명
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake:: operator new](#operator-new) | 오버 로드 연산자 `new` 를 사용 하 여에서 연산자를 사용할 수 없습니다 `RuntimeClass` .

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`DontUseNewUseMake`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a> DontUseNewUseMake:: operator new

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>매개 변수

*__unnamed0*<br/>
할당할 메모리의 바이트 수를 지정 하는 명명 되지 않은 매개 변수입니다.

*배치가*<br/>
할당할 형식입니다.

### <a name="return-value"></a>반환 값

연산자를 오버 로드 하는 경우 추가 인수를 전달 하는 방법을 제공 합니다 `new` .

### <a name="remarks"></a>설명

오버 로드 연산자 `new` 를 사용 하 여에서 연산자를 사용할 수 없습니다 `RuntimeClass` .
